# tyk-api-gateway  (https://github.com/TykTechnologies/tyk)
https://www.youtube.com/watch?v=48UzMOqVq4k&list=PLjCJtqjjSdAe9ZfkbbK_kuzUJD5_nMpIJ

![image](https://github.com/user-attachments/assets/94cf0496-33e5-42ba-84bb-da4165d9d026)

## Components and Features

![image](https://github.com/user-attachments/assets/bb8131ec-5a34-4e06-9f05-55ae56d68fbf)

### Licensed edition's benefits and features

On the left, you'll see API Gateway:
- it's written in GO
- Free and open source and always will be... our open source users are running the same gateways as our enterprise partners
- Code open for auditing and evaluation, gateway features out of the box include: access control, rate limits,...  (GO, Python, TS, gRPC language), it can be scaled both horizontally and vertically as powerful as the gateway however it is headless and must be managed through the gateway apis

On the right, this is where the license component comes in, you get the dashboard and the developer portal. In addition to the GUI the dashboard apis provide a programmatic way for you to manage your gateways making them easier to scale providing role-based access control the ability to document your apis publication and monetization and so much more

## Deployment Strategies

![image](https://github.com/user-attachments/assets/aaadd6d7-0750-498e-b50a-43075cb925df)

- We offer our customers the flexibility to deploy tyke in a variety of configurations should you choose to go with self-managed tyke is cloud native which means one can install tyke on bare metal or any cloud provider tyke
- tyke offers true hybrid deployments where the customer can choose to manage the gateways and delegate the control plane orchestration to tyke
- Fully managed solution, we offer tight cloud as a sas, here is our architecture for a single region on-premise installation

### Single-Region On-Premise
  
![image](https://github.com/user-attachments/assets/9a4c26e3-dc5b-4191-be0c-3fe5b08e1122)

- At the top you'll notice that the api developers and api owners interact with the dashboard and portal to configure the gateway.
- The gateway itself has only one dependency which is redis, we use redis to store things such as tokens, oauth clients as well as leverage it to perform things such as caching rate limiting and temporary analytic storage our dash board has only one dependency which is mongodb, this db is where our long-lived api definitions and api policies live.
- in the middle, we have an open source component known as type pump which is appropriately named for its ability to pump analytics from redis to mongodb or a sql db 

### Analytics

![image](https://github.com/user-attachments/assets/ebef8e0b-31c9-438d-a5aa-95348b7286da)

mongodb isn't the only back-end we support for analytics we have a variety of connectors that we integrate with natively some of these include statsd, logz.io, graffana,... and the list goes on check out our github for an up-to-date list of all the supported backends

### Multi-Region On-premise

![image](https://github.com/user-attachments/assets/88b5b9e7-3eca-46de-b225-35efb7d9c89c)

Where we position our enterprise offering using multi-data center bridge or mdcb for short, allow customers to manage gateways through a single pane of glass in either region or separate regions. The regions you'll notice that there are redis instances located next to the edge gateways. These instances are completely ephemeral, they receive all updates from the primary redis through a pub sub pattern and can operate even if the master controlplane goes down

### Hybrid architecture (hybrid deployment)

![image](https://github.com/user-attachments/assets/a05b922e-720b-4200-b2c9-ed1910f36631)

Tyk manages the controlplane --> the customer only needs to manage the gateways and their corresponding ephemeral redis instances. 

### Cloud architure

![image](https://github.com/user-attachments/assets/65353339-5449-4065-ae5d-29a86b8f6a5c)

Architecture is flexible enough to allow for edge deployments within tight cloud and that ties into those who are looking for a fully managed solution in this instance we manage everything except for your backend services for those who are deploying using kubernetes

![image](https://github.com/user-attachments/assets/11c45eed-890a-48c6-ae1f-5dcbb1b0e50e)


## Installing Tyk
- Sign up for a trial (2 weeks free trial)
- Sign up Tyk locally
- Sign up for Tyk Cloud
- You will need Docker and Docker Compose

### The API Flow 

![image](https://github.com/user-attachments/assets/9cccbc44-52c9-4ff3-a5c9-3ca3620d3835)

If we were just to make a request and view the response and at the bottom we'll be managing our backend service through tyke

## Developer Portal
- Bootstrap developer portal
- Publish a configured API
- As an API developer:
   - Request a key
   - Send a request
   - View analytics
 

## Cache response (caching)
The Tyk Gateway can cache responses from your upstream services.

API Clients which make subsequent requests to a cached endpoint will receive the cached response directly from the Gateway, which:
- reduces load on the upstream service
- provides a quicker response to the API Client (reduces latency)
- reduces concurrent load on the API Gateway
  
Caching is best used on endpoints where responses infrequently change and are computationally expensive for the upstream service to generate.

### Caching with Tyk
Tyk uses Redis to store the cached responses and, as you’d expect from Tyk, there is lots of flexibility in how you configure caching so that you can optimize the performance of your system.

There are two approaches to configure caching for an API deployed with Tyk:
- Basic or Safe Request caching is applied at the API level for all requests for which it is safe to do so.
- Advanced caching options can be applied at the endpoint level.

### Cache Terminology and Features
#### Cache Key





