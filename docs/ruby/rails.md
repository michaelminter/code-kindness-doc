# Rails

## ActionCable
Action Cable seamlessly integrates WebSockets with the rest of your Rails application. It allows for real-time features to be written in Ruby in the same style and form as the rest of your Rails application, while still being performant and scalable. It's a full-stack offering that provides both a client-side JavaScript framework and a server-side Ruby framework. You have access to your full domain model written with Active Record or your ORM of choice.

https://guides.rubyonrails.org/action_cable_overview.html

## ActionController
Action Controller is the C in MVC. After the router has determined which controller to use for a request, the controller is responsible for making sense of the request, and producing the appropriate output. Luckily, Action Controller does most of the groundwork for you and uses smart conventions to make this as straightforward as possible.

https://guides.rubyonrails.org/action_controller_overview.html

## ActionView

https://guides.rubyonrails.org/layouts_and_rendering.html

## ActiveRecord
Active Record is the M in MVC - the model - which is the layer of the system responsible for representing business data and logic. Active Record facilitates the creation and use of business objects whose data requires persistent storage to a database. It is an implementation of the Active Record pattern which itself is a description of an Object Relational Mapping system.

https://guides.rubyonrails.org/active_record_basics.html

### Callbacks
are methods that get called at certain moments of an object's life cycle. With callbacks it is possible to write code that will run whenever an Active Record object is created, saved, updated, deleted, validated, or loaded from the database.

## ActiveJob
Active Job is a framework for declaring jobs and making them run on a variety of queuing backends. These jobs can be everything from regularly scheduled clean-ups, to billing charges, to mailings. Anything that can be chopped up into small units of work and run in parallel, really.

https://guides.rubyonrails.org/active_job_basics.html

## ActiveMailer
Action Mailer allows you to send emails from your application using mailer classes and views.

https://guides.rubyonrails.org/action_mailer_basics.html

## ActiveStorage
Active Storage facilitates uploading files to a cloud storage service like Amazon S3, Google Cloud Storage, or Microsoft Azure Storage and attaching those files to Active Record objects. It comes with a local disk-based service for development and testing and supports mirroring files to subordinate services for backups and migrations.

https://guides.rubyonrails.org/active_storage_overview.html

## ActiveSupport
Active Support is the Ruby on Rails component responsible for providing Ruby language extensions, utilities, and other transversal stuff.

#### ActiveSupport::HashWithIndifferentAccess
To implement a hash where keys :foo and "foo" are considered to be the same:

```ruby
list = { "red" => 0xf00, :green => 0x0f0, blue: 0x00f }.with_indifferent_access
#=> { red: 0xf00, green: 0x0f0, blue: 0x00f }
list['red']    # => 0xf00
list[:blue]    # => 0x00f
```

https://api.rubyonrails.org/classes/ActiveSupport/HashWithIndifferentAccess.html

#### ActiveSupport::Concern
This is a great way of testing a cohesive piece of functionality and making it clear to other developers that these methods belong together. Unit tests can also operate on a test double or a stub, which will keep functionality as decoupled from the remaining model implementation as possible.

A typical module looks like this:

```ruby
module M
  def self.included(base)
    base.extend ClassMethods
    base.class_eval do
      scope :disabled, -> { where(disabled: true) }
    end
  end

  module ClassMethods
    ...
  end
end

```

By using `ActiveSupport::Concern` the above module could instead be written as:

```ruby
require "active_support/concern"

module M
  extend ActiveSupport::Concern

  included do
    scope :disabled, -> { where(disabled: true) }
  end

  class_methods do
    ...
  end
end
```

https://api.rubyonrails.org/v6.1.0/classes/ActiveSupport/Concern.html

## TODO
Services
- What is ActiveJob? When should we use it?
- What is Asset Pipeline?
- Explain the difference between Page, Action, Fragment, Low-Level, SQL caching types.
- What is a Rails engine?
- Migrations?

Architecture Components:
1. Models, representation of business domain.
2. Rails Server, accepts requests from browser.
3. Routes, informs app which peice of code should handle requests.
4. Controllers and Actions, handles data from corresponding requests.
5. Views, handles content being sent back from to browser that issued request.
6. Assets, view content embedded into the layout.

Routing, Controllers, Views:
- Provide an example of RESTful routing and controller.
- Describe CRUD verbs and actions.
- How should you test routes?
- How should you use filters in controllers?
- What are Strong Parameters?
- What do we need to test in controllers?
- How should you use content_for and yield?
- How should you use nested layouts?


- Explain the Active Record pattern.
- What is Arel?
- What is Object-Relational Mapping? Indicate that your classes are mapped to the table in the database, and objects are directly mapped to the rows in the table.
- Describe Active Record conventions.
- Explain the Migrations mechanism.
- Describe types of associations in Active Record.
- What is Scopes? How should you use it?
- Explain the difference between optimistic and pessimistic locking.
