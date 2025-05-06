# Logging Guidelines

<!-- Logging Guidelines Metadata - Do not remove -->
```
{
  "project_name": "[Project Name]",
  "version": "0.0.1",
  "last_updated": "YYYY-MM-DD",
  "update_author": "[Name/ID]"
}
```
<!-- End Metadata -->

## Introduction

### Purpose
This document provides comprehensive guidelines for implementing effective logging throughout the application. Proper logging is essential for debugging, monitoring, performance analysis, and security auditing.

### Scope
These guidelines apply to all components of the application, including server-side code, client-side code, infrastructure scripts, and automated testing.

## Logging Format Standards

### Standard Log Structure
All log entries should follow a consistent structure to enable effective parsing, filtering, and analysis:

```
[TIMESTAMP] [LOG_LEVEL] [COMPONENT] Operation: Message - Details: {context_data}
```

Example:
```
2025-05-01T12:34:56.789Z [INFO] [AUTH_SERVICE] Login: Successful login - Details: {"user_id": "user123", "ip": "192.168.1.1", "method": "password"}
```

### Required Fields
| Field | Description | Example |
|-------|-------------|---------|
| Timestamp | ISO 8601 format with timezone | `2025-05-01T12:34:56.789Z` |
| Log Level | Severity level | `INFO`, `WARNING`, `ERROR` |
| Component | System component generating the log | `[AUTH_SERVICE]`, `[PAYMENT_API]` |
| Operation | Action being performed | `Login`, `Database query`, `API request` |
| Message | Human-readable description | `Successful login`, `Failed to process payment` |
| Details | Structured contextual data as JSON | `{"user_id": "user123", "ip": "192.168.1.1"}` |

### Additional Context
When applicable, include the following context information:
- Request/Transaction ID for tracing requests across components
- User/Account ID (never include personally identifiable information)
- Resource identifiers (order ID, product ID, etc.)
- Performance metrics (duration, size, count)
- Environment information

## Log Level Usage

### DEBUG
- Purpose: Detailed information for debugging during development
- Audience: Developers
- Example: `[DEBUG] [CART_SERVICE] Cart calculation: Applying discount - Details: {"cart_id": "cart123", "discount_rule": "SUMMER10", "original_amount": 100.00, "discount_amount": 10.00}`
- When to use:
  - Detailed function entry/exit
  - Variable values during processing
  - Intermediate calculation results
  - Flow control decisions

### INFO
- Purpose: Confirmation that things are working as expected
- Audience: Operations, System Administrators
- Example: `[INFO] [ORDER_SERVICE] Order created: New order successfully created - Details: {"order_id": "ord123", "items_count": 5, "total_amount": 125.50}`
- When to use:
  - Successful API calls
  - User actions completion
  - System startup/shutdown
  - Configuration loading
  - Routine operations completion

### WARNING
- Purpose: Indication of potential issues that might require attention
- Audience: Operations, System Administrators
- Example: `[WARNING] [PAYMENT_SERVICE] Payment retry: Retrying failed payment - Details: {"payment_id": "pay123", "attempt": 2, "reason": "gateway_timeout"}`
- When to use:
  - Deprecated feature usage
  - Expected retries
  - Resource usage approaching limits
  - Unexpected but handled conditions
  - Performance degradation

### ERROR
- Purpose: Error conditions that prevent normal operation but allow the application to continue
- Audience: Operations, Support
- Example: `[ERROR] [INVENTORY_SERVICE] Stock update: Failed to update inventory - Details: {"product_id": "prod123", "error_type": "database_connection", "message": "Connection timeout after 30s"}`
- When to use:
  - API call failures
  - Database errors
  - Network timeouts
  - Business rule violations
  - Authentication failures

### CRITICAL
- Purpose: Critical conditions that require immediate attention
- Audience: Operations, Support, Leadership
- Example: `[CRITICAL] [DATABASE_SERVICE] Database corruption: Data integrity check failed - Details: {"table": "orders", "error_type": "checksum_mismatch", "affected_records": 1250}`
- When to use:
  - Application crashes
  - Data corruption
  - Security breaches
  - Complete feature unavailability
  - System-wide failures

## Content Requirements

### Do Include
- Specific identifiers (IDs, references, URLs without sensitive data)
- Technical details (status codes, error types, operation counts)
- Contextual information (operation being performed, resource type)
- Error details (exception messages, error codes)
- Performance metrics (duration, size, quantity)

### Never Include
- Passwords, authentication tokens, or credentials
- Personally identifiable information (SSN, full names, addresses)
- Financial data (credit card numbers, bank account details)
- Health or other sensitive personal data
- Session tokens or cookies
- Encryption keys or secrets

### Decorative Formatting
- **NEVER** use decorative formatting such as:
  - Multiple exclamation points (`!!!!!!`)
  - Decorative separators (`********`, `========`)
  - ASCII art or emoticons
  - UPPERCASE FOR EMPHASIS

## Implementation Guidelines

### Language-Specific Implementations

#### [Language/Framework 1]
```javascript
// Example for Node.js with winston
const logger = winston.createLogger({
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.json()
  ),
  transports: [new winston.transports.Console()]
});

// Correct usage
logger.info({
  component: 'USER_SERVICE',
  operation: 'User registration',
  message: 'New user registered',
  details: { user_id: 'user123', plan_type: 'premium' }
});

// Incorrect usage - avoid
console.log('User registered: user123 !!!!!!');
```

#### [Language/Framework 2]
```python
# Example for Python with structlog
import structlog

logger = structlog.get_logger()

# Correct usage
logger.info(
    "New user registered",
    component="USER_SERVICE",
    operation="User registration",
    user_id="user123",
    plan_type="premium"
)

# Incorrect usage - avoid
print("User registered: user123 !!!!!!")
```

### Configuration Management
- Configure log levels appropriately for each environment
- Use environment variables or configuration files for log settings
- Lower log level (more verbose) in development/testing
- Higher log level (less verbose) in production
- Enable additional context in development environments

## Security Considerations

### Log Storage and Access
- Protect log storage with appropriate access controls
- Encrypt logs containing sensitive information
- Implement log rotation and retention policies
- Ensure compliance with data protection regulations

### Log Sanitization
- Implement filters to redact sensitive information
- Use pattern matching to identify and mask PII
- Create allowlists for fields that can be logged
- Audit logging code in security reviews

## Monitoring and Analysis

### Log Aggregation
- Forward logs to a central log management system
- Use structured logging for easier parsing and analysis
- Implement log correlation with request IDs
- Maintain consistent timestamp format for time-series analysis

### Alerting
- Configure alerts for ERROR and CRITICAL log levels
- Set up anomaly detection for unusual log patterns
- Create dashboards for visualization of log trends
- Implement log-based monitoring of key business metrics

## Best Practices

### Effective Logging Strategies
- Log at service boundaries and key integration points
- Include context that will help diagnose problems
- Be consistent with log level usage across components
- Focus on quality over quantity of logs
- Log both success and failure paths

### Common Pitfalls to Avoid
- Excessive logging causing performance issues
- Insufficient logging in critical flows
- Inconsistent formatting making parsing difficult
- Missing context in error logs
- Logging sensitive information

## Appendix

### Glossary
| Term | Definition |
|------|------------|
| Structured Logging | Logging in a consistent, machine-readable format (usually JSON) |
| Log Aggregation | Collecting logs from multiple sources into a central system |
| Log Correlation | Connecting related log entries across different components |
| PII | Personally Identifiable Information |

### References
- [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
- [Logging Best Practices](https://example.com/logging-best-practices)
- [Data Protection Regulations](https://example.com/data-protection) 