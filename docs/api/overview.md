# API

## APIs
[JSON API](https://jsonapi.org/format/)
: A specification for building APIs in JSON

[FHIR](https://www.hl7.org/fhir/http.html)
: FHIR is described as a 'RESTful' specification based on common industry level use of the term REST.

## RESTful
REST (REpresentational State Transfer), is basically an architectural style of development having some principles:

- It should be stateless.
- It should access all the resources from the server using only URI.
- It does not have inbuilt encryption.
- It does not have session.
- It uses one and only one protocol - HTTP.
- For performing CRUD operations, it should use HTTP verbs such as get, post, put and delete.
- It should return the result only in the form of JSON or XML, atom, OData etc. (lightweight data)

**REST based services** follow some of the above principles and not all

**RESTful services** means it follows all the above principles.

MVC supports only some of the above REST principles whereas WEB API supports all the above REST Principles.

MVC only supports the following from the REST API:

- We can access the resource using URI
- It supports the HTTP verb to access the resource from server
- It can return the results in the form of JSON, XML, that is the HTTPResponse.

However, at the same time in MVC:

- We can use the session
- We can make it stateful
- We can return video or image from the controller action method which violates the REST principle of returning lightweight data.

## GraphQL
GraphQL was developed to cope with the need for more flexibility and efficiency! It solves many of the shortcomings and inefficiencies that developers experience when interacting with REST APIs.