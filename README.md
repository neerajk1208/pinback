# Pinback API Documentation

Our Pinback API allows you to perform all the operations required to interact with our web client. The API utilizes REST principles to ensure clear and predictable paths that make writing applications straightforward. 

# HTTP Methods

We use the following HTTP verbs for actions: 

GET - Used for retrieving data
POST - Used for adding data and performing associated actions
DELETE - Used for deleting data and performing associated actions

# Response Format


Responses will be in JSON format. 

Our status codes will be one of the following: 
  200: ok
  201: created/updated
  204: deleted
  400: bad request
  401: unauthorized
  404: url not found
  500: internal error


# User

Request Type: POST

This request will include the following params: 
  name: ‘STRING’

Here is an example request: 

{
name: ‘Test name’, 
}

Sample response: 

Status Code: 201

Search

Request TYPE: POST

This request will include the following params: 
  city: ‘STRING’, 
  state: ‘STRING’, 
  fromDate: ‘STRING’, 
  toDate: ‘STRING’

Here is an example request: 

{
city: ‘Los Angeles’, 
state: ‘CA’, 
fromDate: ‘2016-01-12’, 
toDate: ‘2016-01-13’
}


*fromDate and toDate need to be dates in the future, and must follow chronological order. 

Sample response: 

Status Code: 201

# Venue

Request TYPE: POST

This request will include the following params: 
  id: ‘STRING’, 
  url: ‘STRING’, 
  name: ‘STRING’, 
  city: ‘STRING’, 
  region: ‘STRING’, 
  country: ‘STRING’, 
  latitude: ‘STRING’, 
  longitude: ‘STRING’

*fromDate and toDate need to be dates in the future, and must follow chronological order. 

Here is an example request: 

{
id: '55',
url: 'http://www.venue.com',
name: 'new venue',
city: 'San Francisco',
region: 'CA',
country: 'USA',
latitude: '43434.32',
longitude: '4343434.232'
}

Sample response: 

Status Code: 201

Event

Request TYPE: POST

This request will include the following params: 
  id: ‘STRING’, 
  artists: ‘ARRAY OF STRINGS’, 
  date-time: ‘STRING’, 
  ticket-url: ‘STRING’, 
  venue-id: ‘STRING’

*Venue-ID must already exist in the database. 

Here is an example request: 

{
id: '14',
artists: 'http://www.venue.com',
date-time: ‘9-28-2016’, 
ticket_url: ‘http://www.eventbrite.com’, 
venue_id: ‘55’
}

Sample response: 

Status Code: 201

# User Events

Request TYPE: POST

This request will include the following params: 
  user_id: ‘STRING’, 
  event_id: ‘STRING’

Here is an example request: 

{
user_id: '14', 
event_id: '20'
}

Sample response: 

Status Code: 201

Request TYPE: GET

No params for get request. 

Sample response: 

The response will contain an array of objects. Each object represents an event. 
[
  {
    id: 5, 
    artists: [‘Test’, ‘Test2’, ‘Test3’], 
    date-time: ‘2016-09-28T07:00:00.000Z’, 
    ticket-url: ‘http://www.eventbrite.com’, 
    venue_id: '55', 
    name: ‘venue’
  }, 
  {
    id: 5, 
    artists: [‘Test’, ‘Test2’, ‘Test3’], 
    date-time: ‘2016-09-28T07:00:00.000Z’, 
    ticket-url: ‘http://www.eventbrite.com’, 
    venue_id: '55', 
    name: ‘venue’
  }
]

Status Code: 200

Request TYPE: DELETE

Request params: 
  user_id: ‘INTEGER’, 
  ‘event_id: ‘INTEGER’

Here is a sample request: 

{
  user_id: '55', 
  event_id: '14'
}

Sample response: 

Status Code: 204

# Project Setup

```
npm install
cd client
bower install
```

create mysql database named "greenfield"
run server/data/greenfield-schema.sql

update server/models/db/index.js with db connect info

running the tests: `npm test`

starting the web server: `nodemon`

point browser to: `http://localhost:3000/#/search`

