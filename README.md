# Project 01 - Daily Task Reminder

## Description
Automatically sends pending task reminders to Slack every morning at 9 AM.

## Technologies Used
- n8n (workflow automation)
- Airtable (task database)
- Slack (notifications)

## Setup Instructions
1. Import `project-01-daily-task-reminder.json` into n8n
2. Configure Airtable credentials with your API token and Base ID
3. Configure Slack credentials with your Bot Token and Channel ID
4. Activate the workflow

## How It Works
- Schedule Trigger runs daily at 9:00 AM
- Airtable node fetches tasks where Status ≠ "Done"
- Slack node sends each task as a message to your channel

## Author
Shuaib