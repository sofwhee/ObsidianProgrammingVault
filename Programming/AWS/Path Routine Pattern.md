Routing by paths is the mechanism of grouping multiple or all APIs under the same hostname, and using a request URI to isolate services; for example, `api.example.com/service-a` or `api.example.com/service-b`.

(Can be used instead of a port number)
## Typical use case

Most teams opt for this method because they want a simple architecture―a developer has to remember only one URL such as `api.example.com` to interact with the HTTP API. API documentation is often easier to digest because it is often kept together instead of being split across different portals or PDFs.

Path-based routing is considered a simple mechanism for sharing an HTTP API. However, it involves operational overhead such as configuration, authorization, integrations, and additional latency due to multiple hops. It also requires mature change management processes to ensure that a misconfiguration doesn't disrupt all services.