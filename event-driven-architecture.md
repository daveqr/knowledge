# Event-Driven Architecture

Software architecture pattern that focuses on the generation, detection, consumption, and reaction to events. Events are occurrences or notifications of significant changes or interactions within a system. In EDA, the flow of data and control is determined by events, allowing for decoupled and asynchronous communication between various components or services

## Design patterns

### Write-audit-publish pattern 

Describes the flow of data or events through various stages, where data is initially written to a source, audited for tracking and compliance purposes, and then published to one or more consumers. This pattern is commonly used in scenarios where data needs to be logged for auditing, compliance, or monitoring purposes before being consumed or processed by other components or systems.