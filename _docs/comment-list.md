---
layout: docs
title:  "List comments"
---

You can get a list of comments to a contribution via three different endpoints.

**All users:**

``````
GET /api/projects/:project_id/data-groupings/all-contributions/contributions/:contribution_id/comments/
``````

**Contributors:**

``````
GET /api/projects/:project_id/maps/data-groupings/my-contributions/contributions/:contribution_id/comments/
``````

**Users that have been granted access to a data grouping:**

``````
GET /api/projects/:project_id/data-groupings/:grouping_id/contributions/:contribution_id/comments/
``````

#### URL parameters

Parameter         | Type        | Description
------------------|-------------|--------------------------------------
`project_id`      | `Integer`   | Unique identifier for the project.
`grouping_id`     | `Integer`   | Optional. Unique identifier for the data grouping.
`contribution_id` | `Integer`   | Unique identifier for the contribution.

#### Example response

The response contains an array of all [comments](comment-response.html) made to the contribution.

{% highlight json %}
[
    {
        "id": 66,
        "text": "Good food",
        "creator": {
            "id": 422,
            "display_name": "Peter Schmeichel"
        },
        "respondsto": null,
        "created_at": "2014-06-05T11:31:02.613Z",
        "responses": [
            {
                "id": 67,
                "text": "Really? I think the smørrebrød is not authentic",
                "creator": {
                    "id": 423,
                    "display_name": "Brian Laudrup"
                },
                "respondsto": 66,
                "created_at": "2014-06-05T11:31:02.615Z",
                "responses": []
            }
        ]
    },
    {
        "id": 70,
        "text": "You crazy danish folks and your smørrebrød",
        "creator": {
            "id": 426,
            "display_name": "Mehmet Scholl"
        },
        "respondsto": null,
        "created_at": "2014-06-05T11:31:02.622Z",
        "responses": []
    }
]
{% endhighlight %}

#### Response codes

Code  |  Reason
------|-----------------------------------------
 200  | The comments has been returned successfully.
 404  | The project or contribution was not found. For security reasons we do not leak information about private projects, hence we don't confirm existence private projects to unauthorised users.