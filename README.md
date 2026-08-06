## Callqueue

### Manage customer waiting queue
Redirects each customer to match an available attendant. <br />
Once a match was found, both participants are notified and connected to a video call session. <br />

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/callqueue/blob/main/assets/architecture.png" width="100%">
  <img src="https://github.com/Rosnaldo/callqueue/blob/main/assets/architecture.png" width="70%">
</picture>

https://github.com/Rosnaldo/callqueue

<br />

## Call-Center

### Manage session credits
Track and audit call sessions for per-minute credit billing. <br />

<br />

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/call-center/blob/main/assets/architecture.png" width="100%">
  <img src="https://github.com/Rosnaldo/call-center/blob/main/assets/architecture.png" width="70%">
</picture>

https://github.com/Rosnaldo/call-center

<br />

## My Friends
The project is just a compile setup of everything I have being learning in the process.


<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/my-friends/blob/main/assets/wireframe.png" width="100%">
  <img src="https://github.com/Rosnaldo/my-friends/blob/main/assets/wireframe.png" width="50%">
</picture>

<br />

### Architecture decisions
- containerized services. 
- `keycloak` (manage user authentication, registration and sessions).
- `API` protected by authentication middleware. 
- `DB` only accessable via service. 
- `nginx` redirects domain access to internal services. 
- dockerfiles supports three environments: `local`, `development`, and `production`. 
- frontends are provisioned by `cloudfront`. 
- special `admin` frontend for easy UI management. 
- `monorepo` sharing dependencies between multiple modules.

<br />

https://github.com/Rosnaldo/call-center

<br />

## Two tier VPC

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/aws-labs/blob/main/two-tier/simple/image.png" width="100%">
  <img src="https://github.com/Rosnaldo/aws-labs/blob/main/two-tier/simple/image.png" width="50%">
</picture>

### Considerations
• Backend can only be ssh accessed via bastion host.  
• Backend allows frontend http requests on port 80.  
• Frontend and bastion host inside a public subnet and backend inside a private subnet.  
• Nginx redirects frontend requests to Api in a isolated URL.  
• Nginx allow https access to frontend on port 443.  
• IG allows public subnet to access internet.  
• NAT Gateway allows private subnet to access internet.  
• Api access DynamoDB via VPC endpoint.  

https://github.com/Rosnaldo/aws-labs/tree/main/two-tier/simple

<br />

## Pdf Generator Microservice

A microservice high scalable to convert HTML into PDF.  

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/aws-labs/blob/main/pdf-generator/image.png" width="100%">
  <img src="https://github.com/Rosnaldo/aws-labs/blob/main/pdf-generator/image.png" width="50%">
</picture>

### Considerations
• The `SQS` receives a HTML as input.  
• `SQS` triggers `EventBridge Pipe` which then creates `ECS Controller`.  
• `ECS controller` manages the `ECS Generate PDF` and `ECS Merge PDF`.   
• `ECS controller` pulls `SQS` and creates `ECS Generate PDF` instances and wait them to finish the tasks.   
• The number of `ECS Generate` instances depends on the number of PDF pages.  
• `ECS Generate PDF` polls `SQS` messages and uses the HTML to generate PDF using puppetter browser chromium and then stores on `S3`.  
• Once all PDF pages are created `ECS Controller` creates the `ECS Merge PDF`.    
• `ECS Merge PDF` merges all pages into one final PDF.   

https://github.com/Rosnaldo/aws-labs/tree/main/pdf-generator
