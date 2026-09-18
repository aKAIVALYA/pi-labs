# LinkedIn Auto

## AI-Powered LinkedIn Content and Publishing Automation with n8n

LinkedIn Auto is an n8n workflow for automating LinkedIn publishing through the LinkedIn API. It provides a single workflow that can route different content formats through the correct publishing process, including text posts, articles, image posts, and video posts.

The project is designed to reduce repetitive publishing work while keeping the workflow configurable and easy to extend. It combines n8n orchestration, LinkedIn API execution, and a structure that can later support AI-assisted content generation, review, scheduling, and engagement workflows.

> **Core idea:** AI prepares the content, n8n manages the workflow, LinkedIn executes the action, and humans retain control over important communication decisions.

## What Problem Does It Solve?

Maintaining a consistent LinkedIn presence often requires repetitive manual work:

- Preparing content for different post formats
- Choosing the correct publishing path
- Uploading images and videos
- Building LinkedIn API request bodies
- Handling different media registration steps
- Repeating the same process for every post

LinkedIn Auto centralizes these operations in one n8n workflow. Instead of maintaining separate workflows for every content type, the workflow uses configuration fields and routing logic to send each request through the appropriate branch.

## Current Workflow Capabilities

The current n8n workflow includes:

- Manual workflow execution through an n8n trigger
- Centralized post configuration
- Smart routing with an n8n Switch node
- Text post publishing
- Article publishing
- Article publishing with an image thumbnail
- Image upload and publishing
- Video upload and publishing
- LinkedIn member information lookup
- LinkedIn API HTTP Request nodes
- Native LinkedIn nodes for selected publishing paths
- Support for publicly reachable image and video URLs

## Supported Post Types

Set the `post_type` value in the **Configure Post Settings** node to one of the following values:

| Value | Purpose |
| --- | --- |
| `text` | Publish a text-only LinkedIn post |
| `article` | Publish a post containing an article URL |
| `article_image` | Publish an article with an image thumbnail |
| `image` | Upload an image and publish it with a post |
| `video` | Download, upload, and publish a video |

The `node_type` field controls whether the workflow uses the HTTP API route or a native LinkedIn node where that branch supports it. The HTTP route uses the value `http`.

## Workflow Architecture

The workflow follows this general process:

```text
Manual Trigger
    ↓
Configure Post Settings
    ↓
Smart Content Router
    ↓
Post-Type Branch
    ↓
LinkedIn API Request
    ↓
Published LinkedIn Content
```

Media posts use an extended process:

```text
Media URL
    ↓
Register Upload with LinkedIn
    ↓
Download Media
    ↓
Upload Media File
    ↓
Create LinkedIn Post
```

The Switch node is the central routing layer. It selects the publishing branch based on the configured post type, while HTTP Request nodes perform the LinkedIn API operations.

## Technologies

- [n8n](https://n8n.io/) for workflow orchestration
- LinkedIn API for authentication, media upload, and publishing
- HTTP Request nodes for custom LinkedIn API operations
- Native n8n LinkedIn nodes for supported actions
- Optional AI integration as a future content and quality-control layer

## Setup

### Requirements

- A running n8n instance
- A LinkedIn Developer application
- LinkedIn API access with the required permissions
- A LinkedIn OAuth2 or HTTP Header credential configured in n8n
- Publicly reachable URLs for images and videos

### Import the Workflow

1. Open n8n.
2. Select **Import from File**.
3. Choose `kaivalya.json`.
4. Open the imported workflow.
5. Configure your LinkedIn credentials on the LinkedIn and HTTP Request nodes.
6. Open **Configure Post Settings**.
7. Select a supported `post_type`.
8. Add the required media URL for image or video posts.
9. Execute the workflow manually and test the selected branch.

## Configuration Fields

The **Configure Post Settings** node contains these fields:

| Field | Description |
| --- | --- |
| `post_type` | Selects the publishing format |
| `node_type` | Selects the HTTP or native-node route |
| `image_url` | Public URL of the image to upload |
| `video_url` | Public URL of the video to upload |

Before using the workflow in production, replace sample post text, article URLs, media metadata, and account values with your own content.

## Authentication and Security

Never publish or share exported workflow files containing real credentials, access tokens, or private account identifiers.

Recommended practices:

- Store credentials in n8n's credential manager.
- Use the minimum LinkedIn permissions required by the workflow.
- Do not hard-code access tokens in HTTP Request nodes.
- Use a test LinkedIn account while developing.
- Review every post before enabling automatic execution.
- Respect LinkedIn API permissions, rate limits, and platform policies.
- Keep API configuration and credentials separate from reusable workflow templates.

LinkedIn may require application review or additional permissions for certain member, organization, media, or publishing operations.

## Planned Extensions

The workflow provides the publishing foundation for a broader LinkedIn operating system. Possible future modules include:

- AI-assisted topic research and content generation
- Brand voice and quality checks
- Human approval before publication
- Founder profile and company page routing
- Content calendar integration
- Scheduled publishing with n8n Schedule or Wait nodes
- Comment classification and response drafting
- Sensitive-content detection
- Retry, error handling, and alert notifications
- Publishing history and analytics storage

These extensions should be added as separate modules so content generation, approval, publishing, engagement, and analytics can evolve independently.

## Human-in-the-Loop Principle

Automation should handle repetitive execution, not replace strategic judgment. Important content, sensitive topics, negative feedback, customer conversations, investor communication, and reputation-sensitive replies should remain subject to human review.

The recommended operating model is:

```text
AI prepares
n8n orchestrates
LinkedIn executes
Humans approve important decisions
```

## Troubleshooting

### The workflow does not publish

Check that:

- The LinkedIn credential is connected and active.
- The LinkedIn application has the required permissions.
- The `post_type` value exactly matches one of the supported values.
- The selected media URL is publicly reachable.
- The LinkedIn API response is available in the failed node's execution data.

### Image or video upload fails

Check that:

- The media URL returns the correct file.
- The file is available without local-machine authentication.
- The upload registration request returns an upload URL and asset identifier.
- The binary property passed to the upload node is named `data`.
- The LinkedIn application is approved for the relevant media operation.

### The wrong branch runs

Check the value in **Configure Post Settings** and confirm that there are no extra spaces or spelling differences. The Switch node uses exact string comparisons.

## Project Structure

```text
linkedin-auto/
├── kaivalya.json    # n8n workflow export
└── README.md        # Project documentation
```

## Disclaimer

This project is an automation template and is not affiliated with LinkedIn. API availability, permissions, endpoints, and publishing requirements may change. Test carefully and use the official LinkedIn API documentation for current requirements.

## License

Add the license that best matches how you want to distribute this workflow.
