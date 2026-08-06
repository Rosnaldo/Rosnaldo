## Callqueue

### Manage customer waiting queue
Redirects each customer to match an available attendant. <br />
Once a match was found, both participants are notified and connected to a video call session. <br />

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/callqueue/blob/main/assets/architecture.png" width="100%">
  <img src="https://github.com/Rosnaldo/callqueue/blob/main/assets/architecture.png" width="50%">
</picture>

https://github.com/Rosnaldo/callqueue

<br />

## Call-Center

### Manage session credits
Track and audit call sessions for per-minute credit billing. <br />

<br />

<picture>
  <source media="(max-width: 768px)" srcset="https://github.com/Rosnaldo/call-center/blob/main/assets/architecture.png" width="100%">
  <img src="https://github.com/Rosnaldo/call-center/blob/main/assets/architecture.png" width="50%">
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
