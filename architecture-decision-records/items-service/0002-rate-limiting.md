# 2. Rate Limiting in Items Service

Date: 2024-03-21

## Status

Accepted

## Context

The Items Service needs rate limiting to:
- Prevent abuse and DoS attacks
- Ensure fair resource allocation
- Maintain service stability under high load
- Control costs of external service calls
- Protect downstream dependencies

## Decision

We will implement a multi-tiered rate limiting strategy:

1. API Gateway Level:
   - Global rate limits per IP address
   - Configurable limits per endpoint
   - Default: 1000 requests per minute per IP

2. Service Level:
   - Per-user rate limits using Redis
   - Sliding window algorithm
   - Default limits:
     - 100 read operations per minute
     - 50 write operations per minute
     - 10 bulk operations per minute

3. Implementation Details:
   - Use Redis for distributed rate limiting
   - Token bucket algorithm for fine-grained control
   - Rate limit headers in responses:
     - X-RateLimit-Limit
     - X-RateLimit-Remaining
     - X-RateLimit-Reset

4. Enforcement Policy:
   - HTTP 429 (Too Many Requests) for exceeded limits
   - Exponential backoff recommended in error response
   - Whitelist for internal services

## Consequences

### Positive
- Protected service stability
- Fair resource allocation
- Clear client feedback
- Predictable scaling behavior

### Negative
- Additional operational complexity
- Redis dependency
- Potential false positives
- Client implementation overhead

### Mitigations
- Comprehensive monitoring
- Adjustable limits per environment
- Clear documentation for clients
- Support for emergency limit adjustments