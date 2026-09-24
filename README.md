# SMSMobileAPI Postman collection

Explore SMSMobileAPI in minutes with organized requests for SMS, connected devices, calls, WhatsApp, notifications and e-mail.

SMSMobileAPI turns a real phone—with its SIM and existing number—into a programmable communication endpoint. This collection helps developers test the API safely before integrating it into a CRM, ERP, e-commerce platform, support tool or custom application.

## Included files

| File | Purpose |
| --- | --- |
| [`SMSMobileAPI.postman_collection.json`](SMSMobileAPI.postman_collection.json) | Requests grouped by communication channel. |
| [`SMSMobileAPI.postman_environment.json`](SMSMobileAPI.postman_environment.json) | Safe variable template without credentials. |

## Import and configure

1. Download or clone this repository.
2. In Postman, select **Import**.
3. Import both JSON files.
4. Select the **SMSMobileAPI Local** environment.
5. Set `apiKey` to the key from your dashboard.
6. Set `recipient` to a test number in international format.
7. Connect a mobile and confirm that it is online.
8. Run **SMS → Send SMS**.

The environment contains placeholders only. Do not export or commit a populated environment.

## Collection structure

- **SMS** — send a message, retrieve replies and inspect sent logs.
- **Devices** — list connected mobile gateways and their identifiers.
- **Calls** — retrieve missed, incoming and outgoing activity.
- **WhatsApp** — send, activate collection, request synchronization and retrieve messages.
- **Notifications** — send an internal mobile notification and inspect distribution.
- **Email** — send and retrieve e-mail through a configured mailbox.

## WhatsApp receiving workflow

WhatsApp message retrieval is consent-based and is not continuously active by default:

1. Connect WhatsApp in the SMSMobileAPI dashboard.
2. Run **Activate incoming retrieval** once.
3. Run **Request synchronization window** whenever you want to collect new messages.
4. Wait for the requested synchronization to complete.
5. Run **Retrieve synchronized messages**.

The synchronization response includes its expiry. Request another window when you need to collect newer activity.

## Useful collection behavior

- Requests use `{{baseUrl}}` and environment variables.
- Send requests use form encoding to preserve message content.
- Basic tests check for an HTTP success response.
- The send request stores a returned message ID in `lastMessageId` when available.
- Query values remain editable for dates, filters, pagination and device routing.

## Production guidance

- Keep the API key in a protected secret store.
- Use a dedicated test recipient while developing.
- Prefer `POST` for message and e-mail bodies.
- Use international phone-number format.
- Apply timeouts and exponential backoff for temporary errors.
- Do not retry authentication or validation failures blindly.
- Store message identifiers for correlation.
- Use signed Webhook V2 events for real-time processing instead of frequent polling.

## Documentation

- [API documentation](https://smsmobileapi.com/documentations-api-smsmobileapi/)
- [Webhook V2 overview](https://smsmobileapi.com/webhook/)
- [Dashboard](https://dashboard.smsmobileapi.com/)
- [API examples](https://github.com/SmsMobileApi/smsmobileapi-api-examples)
- [OpenAPI specification](https://github.com/SmsMobileApi/smsmobileapi-openapi)

## Support

Open an issue for a collection problem or documentation improvement. Sanitize all examples and never share API keys, customer numbers, message bodies or mailbox credentials.

Released under the MIT License.
