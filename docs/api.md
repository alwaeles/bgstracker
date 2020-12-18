---
layout: page
title: API
permalink: /api/
---

# API definition

The primary target of the API is to allow communication
between the webapp and the EDMC plugin

The API is divided into two different parts: the messaging
interface, and the RESTful interface.

The message interface is mainly used for event publication
from the plugin to the webapp, and the RESTful
interface is either used to alter stored data or to
fetch stored data.

## General communication scheme

The communication scheme is mostly oriented on privacy.
A session starts when the EDMC plugin is initiated and
stops when the plugin is destroyed.

Any communication between the webapp and the plugin or
any other third-party tool must succeed a session
negotiation as soon as an event should be published through
the message interface.

## Messaging interface

The messaging transport is currently undefined, but
the following sections describe the serialization of
messages.

### Session negotiation

The session negotiation starts with an empty `GET` HTTP
request to the `/session` endpoint.

~~The endpoint will answer with a `200` response with a
set of supported events encoded as a JSON array as body.~~ _TODO:_ rewrite this.

_Example:_

```
GET /session HTTP/1.1
Host: example.com

HTTP/1.1 200 OK
...
Content-Type: text/json

[
  "SomeEvent",
  "..."
]
```

This set must be presented to the end-user to choose
which event can be sent to the server and will be used
by the plugin to filter, according to the user choices,
the events sent through the message interface.

#### Message authentication and identification

Every message must have a session identifier, and an
authentication code. A session identifier is present
in the session negotiation response.

### Message structure

_TODO:_ Fill this section.

## RESTful HTTP API

_TODO:_ Fill this section.
