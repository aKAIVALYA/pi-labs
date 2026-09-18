# PI Labs Project Submissions

This repository contains two separate project submissions developed for PI Labs.

## Submission 1: LinkedIn Auto

Location: [`submissions/linkedin-auto`](submissions/linkedin-auto)

LinkedIn Auto is an n8n workflow for automating LinkedIn publishing through the LinkedIn API. It routes requests by content type and supports text, article, article-with-image, image, and video publishing flows.

The workflow combines:

- n8n workflow orchestration
- LinkedIn API HTTP requests
- LinkedIn media registration and upload
- Configurable post settings
- Smart routing through an n8n Switch node
- Native LinkedIn nodes for selected publishing paths

The project is designed to reduce repetitive publishing work while keeping important communication decisions under human control. Its README contains setup instructions, supported values, authentication guidance, media requirements, and planned extensions for AI generation, scheduling, engagement, and approval workflows.

Main files:

- [`submissions/linkedin-auto/kaivalya.json`](submissions/linkedin-auto/kaivalya.json): n8n workflow export
- [`submissions/linkedin-auto/README.md`](submissions/linkedin-auto/README.md): detailed project documentation

## Submission 2: STARLight x NVIDIA Founder's Office Brief

Location: [`submissions/starlight-nvidia`](submissions/starlight-nvidia)

This submission is a research and communications brief about the STARLight silicon-photonics consortium and its relevance to NVIDIA, AI infrastructure, and European semiconductor manufacturing.

The brief explains:

- Why AI scaling is becoming an interconnect and power problem
- How co-packaged optics can improve data-center networking efficiency
- The difference between an EU-led consortium and a bilateral NVIDIA partnership
- The role of STMicroelectronics and the wider 24-partner consortium
- Why STARLight represents an industrialization milestone rather than a new physics breakthrough
- The strategic implications for GPUs, networking, optics, and European semiconductor supply chains

Main files:

- [`submissions/starlight-nvidia/README.md`](submissions/starlight-nvidia/README.md): research summary and founder talking points
- [`submissions/starlight-nvidia/pi_labs_STARLight_NVIDIA_Founders_Office_Brief.pdf`](submissions/starlight-nvidia/pi_labs_STARLight_NVIDIA_Founders_Office_Brief.pdf): source brief

## Repository Structure

```text
pi-labs/
├── README.md
└── submissions/
    ├── linkedin-auto/
    │   ├── README.md
    │   └── kaivalya.json
    └── starlight-nvidia/
        ├── README.md
        └── pi_labs_STARLight_NVIDIA_Founders_Office_Brief.pdf
```

## Notes

The LinkedIn workflow requires a configured n8n instance, LinkedIn Developer application, approved API permissions, and credentials stored in n8n. Do not commit access tokens or private credentials.

The two submissions are intentionally kept separate because they represent different kinds of work: an automation implementation and a research-led strategic communications brief.
