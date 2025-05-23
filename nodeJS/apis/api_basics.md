### Introduction

In recent years, a new pattern for developing websites has been gaining popularity. Instead of creating an app that hosts both the database and view templates, many developers are separating these concerns into separate projects, hosting their backend and database on a server (either on something like [Heroku](https://www.heroku.com/) or on a VPS like [Digital Ocean](https://www.digitalocean.com/)), then using a service such as [GitHub Pages](https://pages.github.com/) or [Netlify](https://www.netlify.com/) to host their frontend. This technique is sometimes referred to as the [Jamstack](https://jamstack.org/what-is-jamstack/).

Organizing your project this way can be beneficial because it allows your project to be more modular instead of combining business logic with view logic. This also allows you to use a single backend source for multiple frontend applications, such as a website, a desktop app, or a mobile app. Other developers enjoy this pattern because they like using frontend frameworks such as React or Vue to create nice frontend-only, single-page applications.

Frontend and backend applications usually talk to each other using JSON, which you have already encountered if you've gone through our frontend JavaScript course. So at this point, all you really need to learn is how to get your Express application to speak JSON instead of HTML. The assignment at the end of this lesson will take you through a tutorial, but essentially all you have to do is pass your information into [`res.json()`](https://expressjs.com/en/api.html#res.json) instead of [`res.send()`](https://expressjs.com/en/api.html#res.send) or [`res.render()`](https://expressjs.com/en/api.html#res.render). How easy is that?

If you think back to the organization of the routes in the [Routes lesson](https://www.theodinproject.com/lessons/nodejs-routes#routers), we grouped related routes together and extracted each group into its own file. This approach allowed us to more easily modify specific routes without impacting others.

### Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Know what `REST` stands for.
- Explain the purpose of using REST when structuring an API.
- Detail the REST naming conventions for your API endpoints.
- Have a reinforced understanding of the HTTP Methods/Verbs.
- Describe the Same Origin Policy.
- Explain the purpose of CORS.
- Use CORS as middleware in Express (Globally and on a single route).
- Configure CORS to only allow certain origins to access our API.
- Explain CORS headers.

### REST

The structure of an API can take many forms, for example you could have routes named `/api/getAllPostComments/:postid` or `/api/posts/:postid/comments`.
*However*, it's conventional to follow REST (an acronym for Representational State Transfer), a popular and common organizational method for your APIs which corresponds with [CRUD actions](https://www.codecademy.com/article/what-is-crud). Following established patterns such as REST make your API more maintainable and make it easier for other developers to integrate with your API. Software development is often about clear communication which is aided by following expectations.

The actual technical [definition of REST](https://en.wikipedia.org/wiki/Representational_state_transfer) is a little complicated, but for our purposes, most of the elements (statelessness, cacheability, etc.) are covered by default just by using Express to output JSON. The piece that we specifically want to think about is how to **organize our endpoint URIs** (Uniform Resource Identifier).

REST APIs are resource based, which basically means that instead of having names like `/getPostComments` or `/savePostInDatabase` we refer **directly to the resource** (in this case, the blog post) and use HTTP verbs such as GET, POST, PUT, and DELETE to determine the action.
Typically this takes the form of 2 URI's per resource, one for the whole collection and one for a single object in that collection, for example, you might get a list of blog-posts from `/posts` and then get a specific post from `/posts/:postid`. You can also nest collections in this way. To get the list of comments on a single post you would access `/posts/:postid/comments` and then to get a single comment: `/posts/:postid/comments/:commentid`. Below are some other basic examples of endpoints you could have.

#### HTTP Verbs Table

| Verb   | Action | Example                                       |
| ------ | ------ | --------------------------------------------- |
| POST   | Create | `POST /posts` Creates a new blog post         |
| GET    | Read   | `GET /posts/:postid` Fetches a single post    |
| PUT    | Update | `PUT /posts/:postid` Updates a single post    |
| DELETE | Delete | `DELETE /posts/:postid` Deletes a single post |

Each part of an API URI specifies the resource. For example, `GET /posts` would return the entire list of blog posts while `GET /posts/:postid` specifies the exact blog post we want. We could nest further with `GET /posts/:postid/comments` to return a list of comments for that blog post or even `GET /posts/:postid/comments/:commentid` for a very specific blog post comment.

### CORS

The [Same Origin Policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy) is an important security measure that basically says "Only requests from the same origin (the same IP address or URL) should be allowed to access this API". (Look at the link above for a couple of examples of what counts as the 'same origin'.) This is a big problem for us because we are specifically trying to set up our API so that we can access it from different origins, so to enable that we need to set up Cross-origin resource sharing, or CORS.

[Setting up CORS in Express](https://expressjs.com/en/resources/middleware/cors.html#enabling-cors-pre-flight) is very easy, there’s a middleware that does the work for us.

For now, it is acceptable to just allow access from any origin. This makes development quite a bit easier but for any *real* project, once you deploy to a production environment you will probably want to specifically block access from any origin *except* your frontend website. The documentation above explains how to do this.

### Assignment

<div class="lesson-content__panel" markdown="1">

1. Read about [RESTful API design](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design). If you want to code along with the first article, please note this includes the body-parser middleware to parse JSON data on the request body, however since Express 4.16.0 this parsing functionality has been incorporated directly into the Express package itself.
1. Read and code along with this tutorial on [setting up a REST API in Express](https://www.robinwieruch.de/node-express-server-rest-api/). This is one of the best Express tutorials we've come across, it also talks about modular code organization, writing middleware, and links to some great extra info at the end.

</div>

### Knowledge check

The following questions are an opportunity to reflect on key topics in this lesson. If you can't answer a question, click on it to review the material, but keep in mind you are not expected to memorize or master this knowledge.

- [What does REST stand for?](#rest)
- [What are HTTP verbs and why are they important to an API?](#rest)
- [What is the Same-Origin Policy?](#cors)
- [How do you enable CORS in your Express app?](https://expressjs.com/en/resources/middleware/cors.html)
- [Which HTTP verb does each letter in CRUD (Create, Read, Update, Delete) correspond to?](#http-verbs-table)

### Additional resources

This section contains helpful links to related content. It isn't required, so consider it supplemental.

- A simple [example-based definition of REST](https://simple.wikipedia.org/wiki/Representational_state_transfer).
