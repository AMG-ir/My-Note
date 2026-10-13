# Rate Limiting in Web Applications

**Category:** Web Security  
**Type:** Technical Research  
**Status:** Research Notes

## Research Question

What is rate limiting, how is it used on websites and APIs, and what should be checked when reviewing its effectiveness?

## Purpose

Understand how websites control repeated requests, protect application resources, and reduce automated abuse of sensitive endpoints.

## Background

Rate limiting is a server-side control that restricts how many requests a client can make within a defined period. When a client exceeds the configured limit, the server may delay, reject, or otherwise restrict additional requests.

For example, a website might allow a limited number of login attempts within a short period or place a quota on API requests. The appropriate limit depends on the endpoint, normal traffic patterns, and the cost of processing each request.

## Why It Matters

Rate limiting can help reduce:

- Excessive automated requests that consume CPU, memory, database connections, or bandwidth.
- Repeated login and account-recovery attempts.
- API abuse and unexpectedly high resource consumption.
- Automated activity such as excessive form submissions or repeated searches.

Rate limiting is one layer of protection. It does not, by itself, prevent every denial-of-service attack or every form of automation.

## Where It Can Be Implemented

Rate limits may be enforced at multiple layers:

- **Edge/CDN/WAF:** filters or limits traffic before it reaches the application.
- **Web server or reverse proxy:** applies request controls at the HTTP entry point.
- **Application:** applies rules based on routes, authenticated users, sessions, or business logic.
- **API gateway:** applies shared limits and quotas to API consumers.

For sensitive operations, application-level checks may be necessary even when a web server or CDN already has general limits.

## Common Limiting Strategies

- **Per IP address:** easy to apply, but shared networks can group many legitimate users together, and distributed clients may use different IPs.
- **Per account or authenticated identity:** useful for account-specific operations such as login and password recovery.
- **Per session or API key:** useful when a client has a stable session or API credential.
- **Per endpoint:** allows stricter rules for expensive or sensitive routes than for ordinary pages.
- **Global or resource-based limits:** protect a shared service or expensive operation from excessive total demand.

A robust design may combine more than one key. For example, login protection can apply both an account-based limit and an IP-based limit, rather than relying on a single combined IP-and-username key.

## Algorithms at a Glance

- **Fixed window:** counts requests in fixed time intervals. It is simple, but bursts near a window boundary can allow more requests in a short period than expected.
- **Sliding window:** estimates or counts requests over a moving time period, producing smoother enforcement.
- **Token bucket:** replenishes tokens over time and allows a controlled burst while enforcing a longer-term rate.

The best choice depends on the application's traffic and operational requirements.

## HTTP Response

When a request is rejected because a client has sent too many requests, the standard response status is:

```http
HTTP/1.1 429 Too Many Requests
```

A server may also include a `Retry-After` header to indicate when the client can try again. Clients should respect the response rather than immediately retrying in a tight loop.

## Example Configuration: Nginx

The following is an illustrative configuration for a lab or a server you administer. It defines a shared request-rate zone and applies it to a location. It is not a universal production policy; choose a suitable rate for the application's legitimate traffic.

```nginx
http {
    limit_req_zone $binary_remote_addr zone=per_ip:10m rate=5r/s;

    server {
        listen 80;
        server_name example.test;

        location /api/ {
            limit_req zone=per_ip burst=10 nodelay;
            proxy_pass http://app_backend;
        }
    }
}
```

In this example:

- `limit_req_zone` defines a rate-limiting zone keyed by client IP address.
- `rate=5r/s` sets the configured average rate to five requests per second.
- `burst=10` allows a limited burst above the average rate.
- `nodelay` controls how requests within the permitted burst are handled.

Before using a configuration, check the official Nginx documentation, adapt the server and upstream settings, and validate the configuration with the server's configuration-test command. This example has not been deployed or tested as part of this research note.

## Security Review Checklist

For an authorized review of a website or API:

1. Identify sensitive or resource-intensive endpoints, such as login, password recovery, search, uploads, and API routes.
2. Read the site's published policy and documentation where available.
3. Determine whether rate limits are enforced server-side and whether different endpoints need different policies.
4. Check how the application responds when a documented limit is exceeded, including whether it returns an appropriate status such as `429 Too Many Requests`.
5. Consider whether the rule is based only on IP address or also on account, session, API key, or resource.
6. Review how limits interact with reverse proxies, CDNs, and multiple application instances.
7. Check logs and metrics for false positives and legitimate users being throttled.
8. Record the exact scope, method, and observed response. Do not label the site vulnerable based only on a missing visible header or a single observation.

Only perform active verification against systems you own or have explicit permission to test. Avoid sending high volumes of requests to production systems.

## Limitations and Common Mistakes

- Limits that are too strict can block legitimate users, especially behind shared IP addresses.
- Limits that are too generous may not sufficiently reduce abuse.
- IP-only rules can be less effective when requests originate from many addresses.
- A limit at the HTTP request-count level may not protect against a single request that triggers expensive database or application work.
- In a multi-instance application, independent in-memory counters may produce inconsistent limits unless the design uses a shared or coordinated counter.
- Rate limiting should be combined with authentication protections, input and payload-size limits, timeouts, monitoring, and other controls as appropriate.
- The presence or absence of rate limiting is not, by itself, proof that a website is secure or vulnerable.

## Practical Verification

This note documents the concept and an illustrative configuration for further study. It does not claim that the example configuration was deployed, that a specific website was tested, or that any rate-limit behavior was confirmed in a live environment.

## Conclusion

Rate limiting controls how frequently clients can access web routes and APIs. A good implementation uses limits appropriate to the endpoint, considers more than one client identity where necessary, responds clearly when a limit is exceeded, and is monitored to balance abuse prevention with legitimate access.

## References

- [OWASP Denial of Service Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Denial_of_Service_Cheat_Sheet.html)
- [OWASP REST Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html)
- [OWASP API Security: API4 - Lack of Resources and Rate Limiting](https://owasp.org/API-Security/editions/2019/en/0xa4-lack-of-resources-and-rate-limiting/)
- [Nginx ngx_http_limit_req_module documentation](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html)

---

Part of [My-Note](../../README.md) — personal technical knowledge base.
