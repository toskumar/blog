# RAML 1.0 (RESTful API Modeling Language)
## Root of the RAML document

```
#%RAML 1.0
title: Hello World API
version: v1
protocols: https
baseUri: https://api-{env}.hello.com/{version}/
baseUriParameters:
  env:
    description: Name of the environment
mediaType: [application/json, application/xml]
/hello:
  get:
```

Types 

```
#%RAML 1.0
title: Type and security usage
mediaType: application/json
types:
  Person:
    type: object
    properties:
      firstName: string
      lastName: string
      age: number
/persons:
  get:
    responses:
      200:
        body: Person[]
  /{id}:
    get:
      responses:
        200:
          body: Person
  post:
    body:
      application/json:
        type: Person
```

