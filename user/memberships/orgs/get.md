# List organization memberships for the authenticated user

Lists all of the authenticated user's organization memberships.

## Operation Object

```json
{
    "summary": "List organization memberships for the authenticated user",
    "description": "Lists all of the authenticated user's organization memberships.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-memberships-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/members#list-organization-memberships-for-the-authenticated-user"
    },
    "parameters": [
        {
            "name": "state",
            "description": "Indicates the state of the memberships to return. If not specified, the API returns both active and pending memberships.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "active",
                    "pending"
                ]
            }
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/org-membership"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-membership-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "members"
    }
}
```

## References

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
    }
}
```

### `#/components/schemas/org-membership`

```json
{
    "title": "Org Membership",
    "description": "Org Membership",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat/memberships/defunkt"
        },
        "state": {
            "type": "string",
            "description": "The state of the member in the organization. The `pending` state indicates the user has not yet accepted an invitation.",
            "example": "active",
            "enum": [
                "active",
                "pending"
            ]
        },
        "role": {
            "type": "string",
            "description": "The user's membership type in the organization.",
            "example": "admin",
            "enum": [
                "admin",
                "member",
                "billing_manager"
            ]
        },
        "organization_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat"
        },
        "organization": {
            "$ref": "#/components/schemas/organization-simple"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "can_create_repository": {
                    "type": "boolean"
                }
            },
            "required": [
                "can_create_repository"
            ]
        }
    },
    "required": [
        "state",
        "role",
        "organization_url",
        "url",
        "organization",
        "user"
    ]
}
```

### `#/components/examples/org-membership-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/orgs/octocat/memberships/defunkt",
            "state": "active",
            "role": "admin",
            "organization_url": "https://api.github.com/orgs/octocat",
            "organization": {
                "login": "github",
                "id": 1,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
                "url": "https://api.github.com/orgs/github",
                "repos_url": "https://api.github.com/orgs/github/repos",
                "events_url": "https://api.github.com/orgs/github/events",
                "hooks_url": "https://api.github.com/orgs/github/hooks",
                "issues_url": "https://api.github.com/orgs/github/issues",
                "members_url": "https://api.github.com/orgs/github/members{/member}",
                "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "description": "A great organization"
            },
            "user": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            }
        },
        {
            "url": "https://api.github.com/orgs/invitocat/memberships/defunkt",
            "state": "pending",
            "role": "admin",
            "organization_url": "https://api.github.com/orgs/invitocat",
            "organization": {
                "login": "github",
                "id": 1,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
                "url": "https://api.github.com/orgs/github",
                "repos_url": "https://api.github.com/orgs/github/repos",
                "events_url": "https://api.github.com/orgs/github/events",
                "hooks_url": "https://api.github.com/orgs/github/hooks",
                "issues_url": "https://api.github.com/orgs/github/issues",
                "members_url": "https://api.github.com/orgs/github/members{/member}",
                "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "description": "A great organization"
            },
            "user": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            }
        }
    ]
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```