# ADR 003: Use the Wrapper pattern
Farmacy Food interacts with many third-party partner systems. The interfaces of these external systems are bound to
 differ greatly. Such variety emerges both from a standards and a technology point of view.

Non-standardized contracts are a challenge. Direct linking of internal business services to third-party
 apps hinders their stability and enable implementation details coupling. It is undesirable that every change
 on partner systems affect our most fundamental services. 
 
## Decision 
We will use the [Wrapper pattern](https://patterns.arcitura.com/soa-patterns/design_patterns/legacy_wrapper) to
encapsulate external services into standardized interfaces.

The standardized contracts should adhere to our internal design decisions and practices while reducing or eliminating
external influences as much as possible.

We will design our internal logic so that they interact with partner systems only through wrappers.

## Rationale
We expect there will be many vendor-specific systems our platform will have to interact with.
Adoption and removal of vendors should be simple. Our internal systems should be affected the least possible by
changes in vendors, their technology, or by the details of their specific tools.
 
## Status
Proposed 

## Consequences
- Farmacy Food will have a greater degree of freedom to evolve independently of partner systems.
- Every external service should have a corresponding wrapper service.
- The wrapper services will translate the external contracts to meet our internal needs and standards.
- The additional processing may incur in some performance overhead, though generally not significant.
