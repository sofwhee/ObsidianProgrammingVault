Microservices are an architectural and organizational approach to software development where software is composed of small independent services that communicate over well-defined APIs. These services are owned by small, self-contained teams.

Microservices architectures make applications easier to scale and faster to develop, enabling innovation and accelerating time-to-market for new features.

![[Pasted image 20250115125958.png]]
### Monolithic vs. Microservices Architecture

With monolithic architectures, all processes are tightly coupled and run as a single service. This means that if one process of the application experiences a spike in demand, the entire architecture must be scaled. Adding or improving a monolithic application’s features becomes more complex as the code base grows. This complexity limits experimentation and makes it difficult to implement new ideas. Monolithic architectures add risk for application availability because many dependent and tightly coupled processes increase the impact of a single process failure.

With a microservices architecture, an application is built as independent components that run each application process as a service. These services communicate via a well-defined interface using lightweight APIs. Services are built for business capabilities and each service performs a single function. Because they are independently run, each service can be updated, deployed, and scaled to meet demand for specific functions of an application.

## Characteristics of Microservices

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_deployment2.c68823bf6f80f3f85c4fff89410069de9a1bd60c.png)

### Autonomous

Each component service in a microservices architecture can be developed, deployed, operated, and scaled without affecting the functioning of other services. Services do not need to share any of their code or implementation with other services. Any communication between individual components happens via well-defined APIs.

![](https://d1.awsstatic.com/product-marketing/Serverless/benefit_85x85_gear-2.f27f2d94fe6897e2785603c4a7715d18173ff71a.png)

### Specialized

Each service is designed for a set of capabilities and focuses on solving a specific problem. If developers contribute more code to a service over time and the service becomes complex, it can be broken into smaller services.

# Benefits of Microservices

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_Low-Latency.2e96f1de3dacb3bda2a679b372d04c104718be02.png)

### Agility

Microservices foster an organization of small, independent teams that take ownership of their services. Teams act within a small and well understood context, and are empowered to work more independently and more quickly. This shortens development cycle times. You benefit significantly from the aggregate throughput of the organization.  

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_scalable.f24d5f6848364dc06c177951f15f29c63fd22f41.png)

### Flexible Scaling

Microservices allow each service to be independently scaled to meet demand for the application feature it supports. This enables teams to right-size infrastructure needs, accurately measure the cost of a feature, and maintain availability if a service experiences a spike in demand.  

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_delivery-pipeline.1e300fd9b26f94b1865ffe571f81eef55c833d38.png)

### Easy Deployment

Microservices enable continuous integration and continuous delivery, making it easy to try out new ideas and to roll back if something doesn’t work. The low cost of failure enables experimentation, makes it easier to update code, and accelerates time-to-market for new features.  

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_code-configuration.29104e7e882b2a715b6284a4352abfc97f9a60fc.png)

### Technological Freedom

Microservices architectures don’t follow a “one size fits all” approach. Teams have the freedom to choose the best tool to solve their specific problems. As a consequence, teams building microservices can choose the best tool for each job.  

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_transparency.d2636d5bf5c2cfe25a70cc7f7bac5b22fb8cc547.png)

### Reusable Code

Dividing software into small, well-defined modules enables teams to use functions for multiple purposes. A service written for a certain function can be used as a building block for another feature. This allows an application to bootstrap off itself, as developers can create new capabilities without writing code from scratch.  

![](https://d1.awsstatic.com/icons/benefit-icons/100x100_benefit_durable.54299a12d07fd6a95f634ea029ec94a6609f8eb6.png)

### Resilience

Service independence increases an application’s resistance to failure. In a monolithic architecture, if a single component fails, it can cause the entire application to fail. With microservices, applications handle total service failure by degrading functionality and not crashing the entire application.