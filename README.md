# AI Product Video Generator | n8n Automation

Automatically transform product images into AI-generated marketing videos using n8n, Google Sheets, and AI video generation APIs.

## Overview

This workflow automates the process of creating short promotional videos from product images.

Simply add a product's information and image to Google Sheets. The AI Agent analyzes the product details and generates a tailored video prompt. The workflow then sends the prompt and reference image to an AI video generation API, waits for the generation process to complete, and saves the resulting video URL back into the same Google Sheets row.

No manual video editing is required.
## 🎥 Project Demo

Watch the full project walkthrough on YouTube:

[![Watch the Demo](https://img.youtube.com/vi/30fqafoE4Co/maxresdefault.jpg)](https://youtu.be/30fqafoE4Co)

## 🔄 Workflow Preview

![n8n Workflow Preview](docs/workflow-overview.png)
## Workflow Architecture

```text
Manual Trigger
      |
      v
Google Sheets
(Get Product Data)
      |
      v
AI Agent
(Generate Video Prompt)
      |
      v
AI Video Generation API
(Image-to-Video)
      |
      v
Wait
      |
      v
Get Video Status
      |
      v
IF (Check Generation Status)
      |
      +---- Completed
      |         |
      |         v
      |    Update Google Sheets
      |    (Save Video URL)
      |
      +---- Not Completed
                |
                v
           Wait / Retry
```

## Features

- **Automated Prompt Generation:** Uses an AI Agent to create product-specific video prompts.
- **Image-to-Video Generation:** Converts product reference images into short promotional videos.
- **Google Sheets Integration:** Reads product information and updates the original row.
- **Asynchronous Processing:** Waits for the video generation API to finish processing.
- **Status Checking:** Checks the generation status before updating the spreadsheet.
- **Reusable Workflow:** Supports multiple products using the same workflow structure.

## Technologies Used

- [n8n](https://n8n.io/) — Workflow automation.
- [Google Sheets](https://www.google.com/sheets/about/) — Product data management.
- AI Agent — Product analysis and prompt generation.
- AI Video Generation API — Image-to-video generation.
- HTTP Request — API communication.

## Google Sheets Structure

Create a Google Sheet with the following columns:

| Column | Description |
|---|---|
| Product | Product name |
| Product Photo | Publicly accessible product image URL |
| ICP | Ideal Customer Profile |
| Product Features | Main product features |
| Video Setting | Duration, aspect ratio, and video style |
| Status | Processing status |
| Finished Video | Generated video URL |

### Example Product

| Field | Example |
|---|---|
| Product | Digital Tasbih Counter |
| ICP | Muslims interested in daily Dhikr |
| Product Features | Digital counter, LCD screen, ergonomic finger ring |
| Video Setting | 5s, 9:16, luxury Islamic product advertisement |
| Status | Ready |

## Setup Instructions

### 1. Import the Workflow

1. Download the workflow JSON file from this repository.
2. Open your n8n instance.
3. Select **Import from File**.
4. Choose the downloaded JSON file.

### 2. Configure Google Sheets

1. Create your Google Sheets product database.
2. Add the required columns.
3. Configure Google Sheets credentials in n8n.
4. Select your spreadsheet and worksheet.
5. Make sure product images are accessible to the video generation provider.

### 3. Configure the AI Agent

Connect your preferred AI model and configure its credentials.

The AI Agent uses product information to generate a video prompt based on:

- Product name.
- Target audience.
- Product features.
- Video style and technical settings.
- Product reference image.

### 4. Configure the Video Generation API

Add your video generation API credentials through n8n credentials.

Configure the HTTP Request node according to your selected provider's API documentation.

The request typically includes:

- Generated video prompt.
- Product reference image URL.
- Aspect ratio.
- Video duration.
- Resolution.

### 5. Run the Workflow

1. Add a new product row to Google Sheets.
2. Set its status to `Ready`.
3. Execute the workflow.
4. Wait for the video generation process.
5. The generated video URL will be saved in the `Finished Video` column.

## Example Output

Input:

- Product image.
- Product name.
- Product features.
- Target audience.

Output:

- AI-generated video prompt.
- AI-generated product video.
- Video URL saved in Google Sheets.

## Security Notes

- Never commit API keys or access tokens to GitHub.
- Configure credentials directly inside n8n.
- Remove personal spreadsheet IDs and private URLs from exported workflow files.
- Review exported JSON files before publishing.
- Use environment variables or n8n credentials for sensitive configuration.

## Project Purpose

This project demonstrates how AI agents and workflow automation can simplify product marketing content creation.

It can be adapted for:

- E-commerce stores.
- Product advertising.
- Social media content creation.
- Marketing agencies.
- Automated product video production.

## License

This project is available for educational and personal use. Add or update the license file according to your preferred distribution terms.

---

**Built with n8n and AI-powered automation.**
