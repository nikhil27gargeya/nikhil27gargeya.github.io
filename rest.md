# REST

**REST** is an architectural style that provides high-level guidelines for client-server communication. 

6 constraints declared by Roy Fielding (Cacheable, Layered System, Uniform interface, Client-Server, Code on Demand, Stateless).
CLUCCS
Cacheable: Clients can cache (stored and reused) resources to improve performance
Layered System: Layers are modular. Clients are unaware to how the system is organized and where things are being handled.
Uniform Interface: All communications must follow the same protocol. For REST, this is HTTP. Additionally, every resource should have one clear URI by which it can be used as an endpoint.
Client-Server: Decoupled. A client and server can scale independently. A client should only know resource URIs.
Code on Demand (optional): Most of the time, the format sent by server will be JSON/XML, but it could designed to produce code. JSON is javascript object notation which is a data interchange format where messages consists of name value pairs which are objects, and ordered collection of of values which are arrays).
Stateless: Server does not maintain or update state. Each request is standalone and contains all the information to conduct the request and elicit a response. There is no "session" like in older frameworks. 
The term is loosely used and typically means HTTP-based API. You have an endpoint (digital location where an API receives calls). REST APIs use HTTP methods to perform database operations (POST, GET, PUT, DELETE).

What is required in a request:
1. HTTP verb (GET (retrieve), POST (create), PUT (update), DELETE(remove)) a resource or collection
2. Header 
3. Path
4. Message body


What is a resource (the what, ie. a book):
specific piece of data/object identified through a URI (ie. Invoice)

What is a URI:
Uniform Resource Identifier: a string that identifies a resource

What is an endpoint (the where, ie. library shelf):
digital location that identifies a resource. Used to access an operation to be perform on an API resource. Best practices are to use plural nouns with hierarchical structure (ie. /api/users/123/orders)

What is a collection:
group of resources (ie. /invoices)

https://www.codecademy.com/article/what-is-rest?utm_source=pepperjam&utm_medium=affiliate&utm_term=122858&clickId=5076558013&pj_creativeid=8-12462&pj_publisherid=122858


SharedTab API:
1. HTTP verb (POST)
2. Header (using api key and json)
3. Path (/openai/v1/chat/completions)
4. Message Body(let parameters: [String: Any] = [
  "messages": [
    ["role": "user", "content": prompt]
  ],
  "model": "llama3-8b-8192",
  "temperature": 1,
  ...
])

The resource here is conceptually the receipts, but the text from the receipt is processed by the Groq API as a text completion.

Some developers choose to keep collection responses minimal which prevents showing inconsistent data when there are updates.

Criteria for a good API:
1. Not confusing the client
2. Consistency (in naming, structure, and behavior of client/server)
3. Documentation

Creating REST APIs in Flask (microframework):
from flask import Flask, jsonify, request
app = Flask(__name__) #shortcut to the package
users = [
  {'email': 'john@gmail.com', 'name': 'John'}
]
@app.route('/users')
def get_users():
    return jsonify(users)
    
@app.route('/users', methods=['POST'])
def add_user():
    users.append(request.get_json())
    return '', 204 #no content code



