# Get a branch



## Operation Object

```json
{
    "summary": "Get a branch",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-branch",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branches#get-a-branch"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/branch"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/branch-with-protection"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/branch-get"
                        }
                    }
                }
            }
        },
        "301": {
            "$ref": "#/components/responses/moved_permanently"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "branches",
        "subcategory": "branches"
    }
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/branch`

```json
{
    "name": "branch",
    "description": "The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/branch-with-protection`

```json
{
    "title": "Branch With Protection",
    "description": "Branch With Protection",
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "commit": {
            "$ref": "#/components/schemas/commit"
        },
        "_links": {
            "type": "object",
            "properties": {
                "html": {
                    "type": "string"
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "html",
                "self"
            ]
        },
        "protected": {
            "type": "boolean"
        },
        "protection": {
            "$ref": "#/components/schemas/branch-protection"
        },
        "protection_url": {
            "type": "string",
            "format": "uri"
        },
        "pattern": {
            "type": "string",
            "example": "\"mas*\""
        },
        "required_approving_review_count": {
            "type": "integer",
            "example": 1
        }
    },
    "required": [
        "name",
        "commit",
        "_links",
        "protection",
        "protected",
        "protection_url"
    ]
}
```

### `#/components/examples/branch-get`

```json
{
    "value": {
        "name": "main",
        "commit": {
            "sha": "7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
            "node_id": "MDY6Q29tbWl0MTI5NjI2OTo3ZmQxYTYwYjAxZjkxYjMxNGY1OTk1NWE0ZTRkNGU4MGQ4ZWRmMTFk",
            "commit": {
                "author": {
                    "name": "The Octocat",
                    "email": "octocat@nowhere.com",
                    "date": "2012-03-06T23:06:50Z"
                },
                "committer": {
                    "name": "The Octocat",
                    "email": "octocat@nowhere.com",
                    "date": "2012-03-06T23:06:50Z"
                },
                "message": "Merge pull request #6 from Spaceghost/patch-1\n\nNew line at end of file.",
                "tree": {
                    "sha": "b4eecafa9be2f2006ce1b709d6857b07069b4608",
                    "url": "https://api.github.com/repos/octocat/Hello-World/git/trees/b4eecafa9be2f2006ce1b709d6857b07069b4608"
                },
                "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
                "comment_count": 77,
                "verification": {
                    "verified": false,
                    "reason": "unsigned",
                    "signature": null,
                    "payload": null
                }
            },
            "url": "https://api.github.com/repos/octocat/Hello-World/commits/7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
            "html_url": "https://github.com/octocat/Hello-World/commit/7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
            "comments_url": "https://api.github.com/repos/octocat/Hello-World/commits/7fd1a60b01f91b314f59955a4e4d4e80d8edf11d/comments",
            "author": {
                "login": "octocat",
                "id": 583231,
                "node_id": "MDQ6VXNlcjU4MzIzMQ==",
                "avatar_url": "https://avatars.githubusercontent.com/u/583231?v=4",
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
            },
            "committer": {
                "login": "octocat",
                "id": 583231,
                "node_id": "MDQ6VXNlcjU4MzIzMQ==",
                "avatar_url": "https://avatars.githubusercontent.com/u/583231?v=4",
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
            },
            "parents": [
                {
                    "sha": "553c2077f0edc3d5dc5d17262f6aa498e69d6f8e",
                    "url": "https://api.github.com/repos/octocat/Hello-World/commits/553c2077f0edc3d5dc5d17262f6aa498e69d6f8e",
                    "html_url": "https://github.com/octocat/Hello-World/commit/553c2077f0edc3d5dc5d17262f6aa498e69d6f8e"
                },
                {
                    "sha": "762941318ee16e59dabbacb1b4049eec22f0d303",
                    "url": "https://api.github.com/repos/octocat/Hello-World/commits/762941318ee16e59dabbacb1b4049eec22f0d303",
                    "html_url": "https://github.com/octocat/Hello-World/commit/762941318ee16e59dabbacb1b4049eec22f0d303"
                }
            ]
        },
        "_links": {
            "self": "https://api.github.com/repos/octocat/Hello-World/branches/main",
            "html": "https://github.com/octocat/Hello-World/tree/main"
        },
        "protected": false,
        "protection": {
            "enabled": false,
            "required_status_checks": {
                "enforcement_level": "off",
                "contexts": [],
                "checks": []
            }
        },
        "protection_url": "https://api.github.com/repos/octocat/Hello-World/branches/main/protection"
    }
}
```

### `#/components/responses/moved_permanently`

```json
{
    "description": "Moved permanently",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```