# REST 
## Cons 

1. Multiple Endpoints (Multiple Round Trips)
In RESTful services an URL just denotes a single resource. So when there is an need for accessing multiple resources you need to call multiple endpoints and therefore leading to multiple round trips for getting all the necessary data.
```
GET /posts/<postId> - To fetch a particular post
GET /posts/<postId>/comments - To fetch all comments related to a post
GET /posts/<postId>/comments/<commentId> - To fetch a particular comment of a particular post
```
You can see that the length of the endpoints getting increased. As the relations between entities increases so does the amount endpoint URLs.

2. Overfetching/Underfetching Data
There are times when you interface with an API that you get unnecessary data along with the relevant ones and sometimes you don't receive enough data so you end up making multiple trips. This is a common problem in RESTful services. There are situations where you may need only 2-3 values but you get around 20-25 values as the response. This just leads to a transferring large amounts of unused data there by increasing the response time. In the latter case you may need more information than what you get from a single endpoint so therefore it's necessary to make multiple round trips. This also leads to increase in the overall time taken for the client to have all the required data.

3. API Versioning
API versioning is a method followed to avoid breaking the client application with the changes in response format. When there is an change in the API response format a new version is created. This is done so that production client applications can run as expected and giving some breathing time to developers to migrate to the new API version.

But this versioning becomes a problem as when a new version is released it means new endpoints. Maintenance and consuming of API becomes tough and also often leads to duplicated code.

4. Weak Typing
Not all the data we receive from RESTful service are strongly typed i.e. they are not properly given a particular data. This becomes a problem while documenting APIs as we have to specify what kind of data the client can expect by calling the endpoint.

5. Client Kept In The Dark
The client isn't aware of the response structure until it receives it. So the client is kept in the dark regarding what kind of response it can expect. This might often lead to some errors and data not handled properly thus bringing the reliability of the consuming the API low.

# GraphQL
## Pros

1. One Request To Get Them All
A GraphQL service exposes only one endpoints through which the client can pass the necessary query to retrieve the data. With the same example that was considered previously let's look at the GraphQL query
```
{
    findPost(id: <postId>) {
        id
        title
        content
        author
        comments {
            id
            comment
            commentedBy
        }
    }
}
```
As you see we get all the necessary data in just a single request. So when you want a new field you just add it to the query and it will start appearing in the response.

2. Strongly Typed
GraphQL is dominated by schema which are strongly typed. These types can either be primitive or derived. The strong typing system allows the API to be self documented thus making the client aware on what response he will get when querying a particular query.

3. Client Is The Driver
GraphQL provides a declarative syntax that allows clients to specify which fields they need exactly. This eliminates the possibility of overfetching and underfetching of data as it's client who states his data requirements to the GraphQL server based on the schema.

4. API Evolution
Since everything in GraphQL is schema driven extending it won't be a problem as the new field won't affect the existing fields and also GraphQL introduces @deprecated annotation to deprecate fields. This eliminates the need for versioning the API.

5. Transport Layer Agnostic
This is a very nice advantage of GraphQL. The API server can exchange information over any protocol HTTP, HTTPS, WebSockets, TCP, UDP etc. This is because GraphQL is least bothered about how the information is exchanged between the client and server.

## Cons

1. Non-Existent Caching
GraphQL doesn't have support for browser and mobile caching unlike RESTful service which uses native HTTP caching mechanisms. This leads to a developmental effort in order to achieve caching. Although tools like Relay give some support for caching they are not as mature as the caching mechanisms used by RESTful services.

2. Monitoring and Error Reporting
RESTful services leverage the HTTP status codes for different errors that can be encountered. This makes the monitoring the APIs very easy and effortless for the developer. But with GraphQL services always return 200 OK response. A typical GraphQL error message looks like this with status code 200 OK.
```
{
    errors: [
        { 
            message: 'Some error occurred'
        }
    ]
}
```
This is makes it very difficult to handle the error scenarios and the makes the monitoring process cumbersome.

3. Exposed Schema and Resource Attacks
Unlike RESTful services GraphQL services mandates that the client has to know about the data schema to query. If you are exposing your API to a third party you are basically exposing your internal data structure. A great care has to be taken care so that the client doesn't create expensive join queries that can potentially lead to Denial of Service (DoS) attacks on your server.

4. Security - Authentication and Authorization
There is still a confusion going on among the GraphQL community on how to handle the security part of the GraphQL server. There is still not a native solution to integrate authentication and authorization. It is usually abstracted to the business logic layer to authorize user but do we really have to parse and validate the query for an unauthenticated user is still a question in the realm of GraphQL.

5. N + 1 Query Problem
In RESTful services it's very easy to log the SQL query performed and further optimize it. But in the case of GraphQL where the resolving nature is dynamic it's very tough to get the exact query and optimize it further. Sometimes the field resolvers might lead to N + 1 query problems and expensive join operations. But Facebook is developing tools like DataLoader to solve this exact problem. So maybe in the future this won't be a disadvantage.

6. Young Ecosystem
GraphQL is pretty much like a baby in this API ecosystem which means there will be issues and breaking changes every now and then so we have to be very diligent while using any libraries and modules associated with GraphQL.
