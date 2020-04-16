## API endpoint

### A hostname for an API in API Gateway that is deployed to a specific Region. The hostname is of the form {api-id}.execute-api.{region}.amazonaws.com. The following types of API endpoints are supported:

1. Edge-optimized API endpoint

2. Private API endpoint

3. Regional API endpoint

### API Gateway Regional vs. Edge-Optimized Endpoints

- When to use regional endpoints
  - your clients are predominantly located in the same AWS regions (i.e. running in EC2 or Lambda)
  - you want to manage your own CloudFront distribution and use CloudFront features such as custom routing rules, edge caching, WAF, Lambda@Edge, etc
  - you want to take advantage of DNS routing for your custom domain name
  
- When to use edge-optimized endpoints
  - You have geographically distributed clients
  - You don’t want to pay for and manage your own CloudFront distribution

### Results
A common pattern I’ve seen is for developers to conduct performance tests against API Gateway with traffic originating from a single EC2 region, or worse, from a single development machine. These types of tests will likely produce better latency results using regional endpoints. However, keep in mind that if you have geographically distributed clients, synthetic tests will not represent the client experience. The best way to truly measure this is to track client-side latency metrics from your API clients

---
## References
- https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html
- http://blog.ryangreen.ca/2017/11/03/api-gateway-regional-vs-edge-optimized-endpoints/
