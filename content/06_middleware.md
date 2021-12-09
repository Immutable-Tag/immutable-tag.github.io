---
weight: 6
title: "Middleware"
draft: false
---

## Middleware

Our middleware layer is a RESTful API server built using Node.js. The APIs provided by the server are consumed by our React front-end.

The server also calls GitHub APIs to verify the existence of a commit to which a tag will point, and optionally, to create tags in the GitHub repository using GitHub personal access tokens.

### Connecting Node.js server to the blockchain

In the previous section, we described how we deploy our smart contract to Ganache and get a contract address once the deployment succeeds. We use this address to connect the middleware to the smart contract using [web3.js](https://web3js.readthedocs.io/) and invoke smart contract functions for tag creation and tag retrieval.

### Creating a Tag

This API creates a new tag on the blockchain. It first checks if the tag already exists in the blockchain by invoking the `checkTag` smart contract function. If the tag does not exist, it makes a request to GitHub to verify the existence of the commit that is being mapped to the tag. If the commit is valid, it proceeds to create the tag in the blockchain by invoking the `createTag` smart contract function. (Please see the previous section on Smart contracts to understand more.)

If a GitHub personal access token is passed to it, then the API also creates the tag in the GitHub repository.

#### API endpoint

```http
POST /v1/tags
```

#### Parameters

| Name         | Type   | In     | Description      |
|--------------|--------|--------|------------------|
| Content-Type | string | header | application/json |
| repo_url     | string | body   | repository URL   |
| tag_id       | string | body   | tag name         |
| commit_id    | string | body   | commit hash      |

#### Example

```bash
curl -i -X POST "http://localhost:5000/v1/tags" \
    -H 'Content-Type: application/json' \
    -d '{"repo_url": "https://github.com/Immutable-Tag/SmartContacts",\
        "tag_id": "v1.0.0",\
        "commit_id": "66190b9fc987cb12c3a302c84123122e68ef6450"}'
```

Response:

```http
HTTP/1.1 201 Created
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 39
ETag: W/"27-p5b2vwAQyjd8Enu5ruBWmlgkkzw"
Date: Wed, 24 Nov 2021 04:58:54 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"message":"Successfully created tag."}
```

If we try to map an existing tag to a different commit, the response looks like:

```http
HTTP/1.1 400 Bad Request
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 30
ETag: W/"1e-KM94dQmY+pgv0Ecd8L77N5qIs0c"
Date: Wed, 24 Nov 2021 04:58:27 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"error":"Tag already exists"}
```

If the commit doesn't exist, the response looks like: 

```http
HTTP/1.1 400 Bad Request
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 30
ETag: W/"1e-KM94dQmY+pgv0Ecd8L77N5qIs0c"
Date: Wed, 24 Nov 2021 04:58:27 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"error":"Commit does not exist"}
```

### Retrieving a Tag

This API retrieves a tag and its related information from the blockchain. For this, we invoke the `getTag` smart contract function which returns the `Tag` object if it exists in the `mapping`. (Please see the previous section on Smart contracts to understand more.)

#### API endpoint

```http
POST /v1/tags/{tag_id}
```

#### Parameters

| Name         | Type   | In     | Description      |
|--------------|--------|--------|------------------|
| Content-Type | string | header | application/json |
| tag_id       | string | path   | tag name         |
| repo_url     | string | body   | repository URL   |

#### Example

```bash
curl -i -X POST "http://localhost:5000/v1/tags/v1.0.0" \
    -H 'Content-Type: application/json' \
    -d '{"repo_url": "https://github.com/Immutable-Tag/SmartContacts"}'
```

Response:

```http
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 134
ETag: W/"86-aGtC1lmpzo6bWnvAnDjnyX41gHg"
Date: Wed, 24 Nov 2021 04:57:49 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"repo_url":"https://github.com/Immutable-Tag/SmartContacts","tag_id":"v1.0.0","commit_id":"66190b9fc987cb12c3a302c84123122e68ef6450"}
```

If we try to get a non-existent tag, the response looks like:

```http
HTTP/1.1 404 Not Found
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 30
ETag: W/"1e-Tox4M2y0N7WkRGDAFErMm9hsPbA"
Date: Wed, 24 Nov 2021 04:57:36 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"error":"Tag does not exist"}
```

You can find the entire code and documentation for our middleware in [this GitHub repository](https://github.com/Immutable-Tag/Middleware).