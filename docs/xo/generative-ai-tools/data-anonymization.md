
# PII and Sensitive Data Anonymization

Personally identifiable information (PII), or sensitive personal information (SPI), refers to information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. Some examples of PII include Social Security Number, email address, credit card numbers, passport number, home address, and so forth.

Kore.ai allows you to redact any sensitive information that users share with your bots. When you enable redaction for an information type, you can transform its value into a pattern that doesn’t contain comprehensible data. Any end-user input that matches the PII pattern gets redacted by the platform in the context object, chat logs, and all other places. [Learn More](../app-settings/advanced-settings/pii-data-masking.md).


## Protecting Sensitive Data in LLM Interactions

In LLM interactions, the platform maintains the conversation context by anonymizing data instead of redacting it. Sensitive data is replaced with descriptive placeholders in LLM calls. For example, if the Phone Number is configured for redaction in the global PII Settings, it will be replaced with "[Phone Number]". This enhances privacy and security, reducing the risk of exposing personal information to external LLM services.

!!! note

    Data anonymization is automatically applied to all the Dynamic Conversation features except the GenAI node.