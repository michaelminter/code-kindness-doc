# Ruby
Ruby is a dynamic, interpreted, reflective, object-oriented, general-purpose programming language.

## Style Guides

[Shopify](https://shopify.github.io/ruby-style-guide/)
: This Style Guide is the result of over a decade of Ruby development at Shopify.

[Github](https://github.com/github/rubocop-github/blob/master/STYLEGUIDE.md)
: This is GitHub's Ruby Style Guide, inspired by RuboCop's guide.

## Class
the blueprint from which individual objects are created.

```ruby
class NewClassName; end
```

## Module
Modules are a way of grouping together methods, classes, and constants. Modules give you two major benefits.

- Modules provide a namespace and prevent name clashes.
- Modules implement the mixin facility.

```ruby
module NewModuleName; end
```

## Mixins
Include mixes in specified module methods as instance methods in the target class. Extend mixes in specified module methods as class methods in the target class.

A mixin can basically be thought of as a set of code that can be added to one or more classes to add additional capabilities without using inheritance.

```ruby
module MixinModule; end

class NewClass
  include MixinModule
end
```

Or namespacing.

```ruby
class Mixin::NewClass; end
```

## Object
Objects are instances of the class.

## Symbol
A Symbol is the most basic Ruby object you can create. It's just a name and an internal ID. Symbols are useful because a given symbol name refers to the same object throughout a Ruby program. ... Two strings with the same contents are two different objects, but for any given name there is only one Symbol object.

## Metaprogramming
Metaprogramming is a technique by which you can write code that writes code by itself dynamically at runtime.

## Constructor
Method gets automatically invoked whenever an instance of the class is created.
```ruby
def initialize(*properties)
  # ...
end
```

## Closures
Blocks, procs, lambdas, and methods available in Ruby are collectively called closures. A block is basically Ruby’s version of a closure—a block of code that can be wrapped up into a proc (a type of function) that can then be stored in a variable or passed to a method and run when desired. Blocks can syntactically be written as blocks of code between `{ }` or the `do` and `end` keywords.
### Block
The simplest kind of closure is a block. A chunk of code that can be passed to an object/method and is executed under the context of that object.

```ruby
def explicit_block(&block)
  block.call # same as yield
end
explicit_block { puts "Explicit block called" }
# => "Explicit block called"
```

Check if `block` was given

```ruby
def do_something_with_block
  return "No block given" unless block_given?
  yield
end
```

### Proc
A Proc object is an encapsulation of a block of code, which can be stored in a local variable, passed to a method or another Proc, and can be called. Proc is an essential concept in Ruby and a core of its functional programming features.

```ruby
square = Proc.new { |x| x ** 2 }
# => #<Proc:0x00007fc3381acba8@(irb):32>

square.call(3)  # => 9
square.(3)      # => 9
square[3]       # => 9
```

`proc` does not report an error if the number of parameters passed does not match the number of parameters it accepts whereas a `lambda` does.

```ruby
p = Proc.new{ |x| "Vampire #{x}" }
  
p.call                      # => "Vampire "
p.call('shoes')             # => "Vampire shoes"
p.call('shoes', 'house')    # => "Vampire shoes"
```

A `proc` will try to return from the current context.

```ruby
def call_proc
  puts "Before proc"
  
  my_lambda = -> { return 1 }
  puts my_lambda.call

  my_proc = Proc.new { return 2 } # Will return from method here 
  puts my_proc.call
  
  puts "After proc"
end
p call_proc
# =>
# Before proc
# 1
# 2

```

### Lambda

There is no dedicated `Lambda` class. A `lambda` is just a special `Proc` object. If you take a look at the instance methods for `Proc`, you will notice there is a `lambda?` method.

```ruby
say_something = -> { puts "This is a lambda" }
# => #<Proc:0x00007fc3381594f8@(irb):24 (lambda)>
say_something.call
# => "This is a lambda"
```

Other ways to call a `lambda`

```ruby
my_lambda = ->(var) { puts "Something #{var}" }

my_lambda.call('near')  # => "Something near"
my_lambda.('far')       # => "Something far"
my_lambda['wide']       # => "Something wide"
my_lambda.==='wet'      # => "Something wet"
my_lambda.call          # => ArgumentError (wrong number of arguments (given 0, expected 1))
```

A `lambda` will return normally, like a regular method.

## Yield
A Ruby method that receives a code block.

## Method Access Control
There are three levels of method access control for classes. Methods may either be public, protected, or private.

- Public methods can be called by anyone.
- Protected methods are only accessible within their defining class and its subclasses.
- Private methods can only be accessed and viewed within their defining class.

## Methods
A method in Ruby is a set of expressions that returns a value.
### Getter Method
Getter methods help you retrieve the value of an instance variable. If you don't have a getter method, trying to retrieve a variable is going to result in an error.
### Setter Method
Setter methods help us assign new values to our instance variables.
### Attribute Accessor
- `attr_reader` - generates a getter method
- `attr_writer` - generates a setter method
- `attr_accessor` - generates both getter and setter methods

### Destructive Method
Permanently modify their callers. Sometimes end with a bang character (!).

```ruby
def set_broadcaster!; end
```

_In Rails, a method with an exclamation at the end usually means that an exception will be raised for an unexpected event._

### Predicate Method
Returns `true` or `false`. Sometimes end with a question mark (?).

```ruby
def has_water?; end
```

## Self
Gives you access to the current object – the object that is receiving the current message.

## Super
A call to `super` invokes the parent method with the same arguments that were passed to the child method.

- It can only be used inside a method.
- It returns the result from calling the parent method.
- It can be called multiple times.

An error will occur if the arguments passed to the child method don’t match what the parent is expecting.

Options:
- `super()` invokes the parent method without any arguments.
- `super(arg1, arg2, ...)` to choose what arguments you want to pass.

```ruby
class Animal
  def name
    puts "Animal"
  end
end

class Cat < Animal
  def name
    super
  end
end

cat = Cat.new
cat.name #=> "Animal"
```

If you call it inside the `initialize` method it can be used to initialize instance variables on the parent class.

## Singleton Classes
Can only have one object instantiated from them. Prevent instantiation of more than one object of that class. Use, include Singleton

is a creational design pattern, which ensures that only one object of its kind exists and provides a single point of access to it for any other code.

- Explain what singleton methods are.
- What is Eigenclass in Ruby?

## Cloning
`Object#dup` creates a shallow copy of an object. For example, it will not copy any mixed-in module methods, whereas `Object#clone` will.

`#dup` does not have a direct association with the original; and thus, modifying the attributes of a duped object will not result in a change to the original one.


`#clone` copies the singleton class, while `#dup` does not.

`#clone` preserves the frozen state, while `#dup` does not.


`clone` is used to duplicate an object, including its internal state, `dup` typically uses the class of the descendant object to create the new instance.

When using `dup`, any modules that the object has been extended with will not be copied.


One difference is with frozen objects. The clone of a frozen object is also frozen (whereas a dup of a frozen object isn't).


They both create a shallow copy of an object (meaning that they don't copy the objects that might be referenced within the copied object). However, #clone does two things that #dup doesn't:

- copy the singleton class of the copied object
- maintain the frozen status of the copied object

```ruby
new_campaign = Campaign.find(1).dup
new_campaign.title = "Campaign 2019"
new_campaign.save!
```

## Variables
Variables are the memory locations, which hold any data to be used by any program.
### Constant
Constants begin with an uppercase letter. Constants defined within a class or module can be accessed from within that class or module, and those defined outside a class or module can be accessed globally.

Constants may not be defined within methods. Referencing an uninitialized constant produces an error. Making an assignment to a constant that is already initialized produces a warning.
### Local Variable
These are variables that are assigned within a method. They can only be used within the method in which they have been declared.
### Global Variable
These are variables that can be used by two or more methods. These variables are declared outside of methods and can be manipulated within methods. Start with $.
### Instance Variable
Global variables that are ONLY used in Instance Methods within a class. Start with @.
### Class Variable
Used in both Instance Methods and Class Methods within a class. They can be used anywhere within the class or its children. Start with @@.
### Psuedo Variables
are special variables that have the appearance of local variables but behave like constants. You cannot assign any value to these variables.

Examples:

* `self` − The receiver object of the current method.
* `true` − Value representing true.
* `false` − Value representing false.
* `nil` − Value representing undefined.
* `__FILE__` − The name of the current source file.
* `__LINE__` − The current line number in the source file.

## Operators
[https://www.tutorialspoint.com/ruby/ruby_operators.htm]()
### Unary operator
is an operation with a single input

Examples:

- `-` used as notation for a negative number
- `&`
- `*` splat

### Arithmetic operator
Examples:

- `+` Adds values on either side of the operator.
- `-` Subtracts right hand operand from left hand operand.
- `*` Multiplies values on either side of the operator.
- `/` Division, divides left hand operand by right hand operand.
- `%` Modulus, divides left hand operand by right hand operand and returns remainder.
- `**` Exponent, performs exponential (power) calculation on operators.

### Comparison
Examples:

- `==`
- `!=`
- `>`
- `<=>` Combined comparison operator. Returns `0` if first operand equals second, `1` if first operand is greater than the second and `-1` if first operand is less than the second.
- `===`

### Assignment
Examples:

- `=`
- `+=` Add
- `-=` Subtract
- `*=` Multiply
- `/=` Divide
- `%=` Modulus
- `**=` Exponent (power)

### Bitwise operator
works on bits and performs bit by bit operation.
### Logical operator
Examples:

- `&&` (AND) The main purpose of the `and` operator is actually to control the flow of logic. You can use the and operator for chaining operations that depend on each other.
- `||` (OR)
- `!` (NOT)

### Ternary operator
It first evaluates an expression for a true or false value and then executes one of the two given statements depending upon the result of the evaluation.

```ruby
is_true() ? condition_1 : condition_2
```

### Range
Sequence ranges in Ruby are used to create a range of successive values - consisting of a start value, an end value, and a range of values in between.

In Ruby, these sequences are created using the `..` and `...` range operators. The two-dot form creates an inclusive range, while the three-dot form creates a range that excludes the specified high value.

```ruby
(1..5)        #==> 1, 2, 3, 4, 5
(1...5)       #==> 1, 2, 3, 4

('a'..'d')    #==> 'a', 'b', 'c', 'd'
('a'...'d')   #==> 'a', 'b', 'c'
```
### Splat
Method Definitions:

```
def say(what, *people)
  people.each{ |person| puts "#{what} #{person}!" }
end
 
say "Hello!", "Alice", "Bob", "Carl"
#=> 
Hello Alice!
Hello Bob!
Hello Carl!
```

Calling Methods:

```
def add(a,b)
  a + b
end

add(*[3,7]) #=> 10
```

Array Destructuring:

```
first, *list = [1,2,3,4]          #=> first=1, list=[2,3,4]
*list, last = [1,2,3,4]           #=> list=[1,2,3], last=4
first, *middle, last = [1,2,3,4]  #=> first=1, middle=[2,3], last=4
```

## Literals

### Fixnum
Underscore characters are ignored in the digit string.

```
123                  # Fixnum decimal
1_234                # Fixnum decimal with underline
-500                 # Negative Fixnum
0377                 # octal
0xff                 # hexadecimal
0b1011               # binary
?a                   # character code for 'a'
?\n                  # code for a newline (0x0a)
12345678901234567890 # Bignum
```
Integers outside their designated range are stored in objects of class `Bignum`.

### Float
Numbers with decimals.

```
123.4                # floating point value
1.0e6                # scientific notation
4E20                 # dot not required
4e+20                # sign before exponential
```

### String
Double-quoted strings allow substitution and backslash notation but single-quoted strings don't allow substitution and allow backslash notation only for `\\` and `\'`.

```
"Regular string"
"Backslash Notation example\n\n"
'Regular string'
'Escape using "\\"';
'That\'s right';
```
You can substitute the value of any Ruby expression into a string using the sequence #{ expr }. Here, expr could be any ruby expression.

```
"Multiplication Value : #{24*60*60}"
#=> Multiplication Value : 86400
```

### Array
Literals of Ruby Array are created by placing a comma-separated series of object references between the square brackets. A trailing comma is ignored.

```
[  "fred", 10, 3.14, "This is a string", "last element", ]
```

### Hash
A literal Ruby Hash is created by placing a list of key/value pairs between braces, with either a comma or the sequence => between the key and the value. A trailing comma is ignored.

```ruby
{ "red" => 0xf00, :green => 0x0f0, blue: 0x00f }
#=> { "red" => 0xf00, :green => 0x0f0, :blue => 0x00f }
```

Return a new hash with all keys converted to symbols. With a select block, limits conversion to only a certain selection of keys.

```ruby
foo = { :name => 'Gavin', 'wife' => :Lisa }
foo.symbolize_keys    #=>  { :name => "Gavin", :wife => :Lisa }
foo                   #=>  { :name => "Gavin", "wife" => :Lisa }
```

Destructively convert all keys to symbols. This is the same as Hash#symbolize_keys, but modifies the receiver in place and returns it. With a select block, limits conversion to only selected keys.

```ruby
foo = { 'name' => 'Gavin', 'wife' => :Lisa }
foo.symbolize_keys!    #=>  { :name => "Gavin", :wife => :Lisa }
foo                    #=>  { :name => "Gavin", :wife => :Lisa }
```

### Range
A Range represents an interval which is a set of values with a start and an end. Ranges may be constructed using the `s..e` and `s...e` literals, or with Range.new.

Ranges constructed using `..` run from the start to the end inclusively. Those created using `...` exclude the end value. When used as an iterator, ranges return each value in the sequence.

A range `(1..5)` means it includes 1, 2, 3, 4, 5 values and a range `(1...5)` means it includes 1, 2, 3, 4 values.

### Backslash Notation
```
\n   Newline (0x0a)
\r   Carriage return (0x0d)
\f   Formfeed (0x0c)
\b   Backspace (0x08)
\a   Bell (0x07)
\e   Escape (0x1b)
\s   Space (0x20)
...
```

### OpenStruct
An OpenStruct is a data structure, similar to a Hash, that allows the definition of arbitrary attributes with their accompanying values. This is accomplished by using Ruby’s metaprogramming to define methods on the class itself.

An OpenStruct employs a Hash internally to store the attributes and values.

```ruby
require "ostruct"

person = OpenStruct.new(:name => "John", "age" => 70)
# => #<OpenStruct name="John", age=70>
person.gender = 'M'
# => "M"

person           # => #<OpenStruct name="John", age=70, gender="M">
person.name      # => "John"
person.address   # => nil
```

Removing the presence of an attribute requires the execution of the `#delete_field` method as setting the property value to `nil` will not remove the attribute.

```ruby
first_pet  = OpenStruct.new(:name => "Rowdy", :owner => "John Smith")
second_pet = OpenStruct.new(:name => "Rowdy")

first_pet.owner = nil
first_pet                 # => #<OpenStruct name="Rowdy", owner=nil>
first_pet == second_pet   # => false

first_pet.delete_field(:owner)
first_pet                 # => #<OpenStruct name="Rowdy">
first_pet == second_pet   # => true
```

## TODO
- Explain how (almost) everything is an object in Ruby.
- What is not an object?
- Describe Ruby method lookup path.
- Interpolation
- Duck Typing
- What is Rack?
- Explain the Rack application interface.
- Write a simple Rack application.
- How does Rack middleware work?