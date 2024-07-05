# Get a package version for a user

Gets a specific package version for a public package owned by a specified user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "Get a package version for a user",
    "description": "Gets a specific package version for a public package owned by a specified user.\n\nOAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/get-package-version-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#get-a-package-version-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/package-type"
        },
        {
            "$ref": "#/components/parameters/package-name"
        },
        {
            "$ref": "#/components/parameters/package-version-id"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/package-version"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/package-version-user"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "packages",
        "subcategory": "packages"
    }
}
```

## References

### `#/components/parameters/package-type`

```json
{
    "name": "package_type",
    "description": "The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string",
        "enum": [
            "npm",
            "maven",
            "rubygems",
            "docker",
            "nuget",
            "container"
        ]
    }
}
```

### `#/components/parameters/package-name`

```json
{
    "name": "package_name",
    "description": "The name of the package.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/package-version-id`

```json
{
    "name": "package_version_id",
    "description": "Unique identifier of the package version.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/package-version`

```json
{
    "title": "Package Version",
    "description": "A version of a software package",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the package version.",
            "type": "integer",
            "example": 1
        },
        "name": {
            "description": "The name of the package version.",
            "type": "string",
            "example": "latest"
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/packages/container/super-linter/versions/786068"
        },
        "package_html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/package/super-linter"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/super-linter/786068"
        },
        "license": {
            "type": "string",
            "example": "MIT"
        },
        "description": {
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-10T20:09:31Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2014-03-03T18:58:10Z"
        },
        "deleted_at": {
            "type": "string",
            "format": "date-time",
            "example": "2014-03-03T18:58:10Z"
        },
        "metadata": {
            "type": "object",
            "title": "Package Version Metadata",
            "properties": {
                "package_type": {
                    "type": "string",
                    "example": "docker",
                    "enum": [
                        "npm",
                        "maven",
                        "rubygems",
                        "docker",
                        "nuget",
                        "container"
                    ]
                },
                "container": {
                    "type": "object",
                    "title": "Container Metadata",
                    "properties": {
                        "tags": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        }
                    },
                    "required": [
                        "tags"
                    ]
                },
                "docker": {
                    "type": "object",
                    "title": "Docker Metadata",
                    "properties": {
                        "tag": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        }
                    },
                    "required": [
                        "tags"
                    ]
                }
            },
            "required": [
                "package_type"
            ]
        }
    },
    "required": [
        "id",
        "name",
        "url",
        "package_html_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/package-version-user`

```json
{
    "value": {
        "id": 387039,
        "name": "0.2.0",
        "url": "https://api.github.com/users/octocat/packages/rubygems/octo-name/versions/387039",
        "package_html_url": "https://github.com/octocat/octo-name-repo/packages/40201",
        "license": "MIT",
        "created_at": "2019-12-01T20:49:29Z",
        "updated_at": "2019-12-01T20:49:30Z",
        "description": "Octo-name client for Ruby",
        "html_url": "https://github.com/octocat/octo-name-repo/packages/40201?version=0.2.0",
        "metadata": {
            "package_type": "rubygems"
        }
    }
}
```