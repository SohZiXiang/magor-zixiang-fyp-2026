# MAGOR – System Enhancements

This Final Year Project enhances MAGOR, a web-based speech transcription platform, by improving reliability, maintainability, and usability while introducing AI-assisted features.

- Focus: system stabilization, feature completion, and AI extension
- Deliverables: implementation updates, project plan, weekly progress demos

## FYP Information

| Field | Details |
|---|---|
| Name | Soh Zi Xiang |
| Matriculation ID | U2321798D |
| Project # | CCDS25-1034 |
| Project Title | Full Stack Development and Deployment of a Web-Based Speech Recognition System |
| Project Summary | Here the student will work with the team for full stack development of speech recognition system. The front end is [Meadow9 App](https://apps.apple.com/sg/app/meadow9/id6740014005), and the back end is a speech recognition engine hosted to service transmitted speech recordings for transcription task. |
| Start Date | 12 January 2026 |
| End Date | 13 November 2026 |

## Plan of Work

[Project Plan](./FYP_Soh_Zi_Xiang_Project_Plan.pdf)

## Project Overview

MAGOR is a web-based audio and video transcription application that supports the upload and processing of recordings, utilizing advanced speech-to-text models for automatic speech recognition. MAGOR provides an array of features, including transcript generation and editing, captioning of audio and image content, speaker detection, and tagging of recordings.

Although MAGOR currently provides a functional transcription system, several components remain incomplete or unstable. This project focuses on improving the system’s robustness, maintainability, and usability, while incorporating new artificial intelligence (AI) features to enhance the platform’s recording analysis capabilities.

## Architecture Overview

The system follows a proxy-based full-stack architecture. Client requests from the frontend are routed through NGINX to either Magor Backend or Magor Studio, depending on the requested function.

Magor Studio manages upload management, media, and transcript workflows, and stores related data in MongoDB.

Magor Backend handles authentication and search queries, and retrieves data from MongoDB.

Both Magor Backend and Magor Studio connect to the ASR Gateway Service for transcription processing. In addition, Magor Studio integrates with the Image Captioning Service and backs up media and transcript assets to Azure Blob Storage for frontend retrieval.

![Architecture Overview](./img/Architecture%20Overview.png)

## Project Objectives

The primary objectives of this project are:

- Resolve existing system bugs and restore system functionalities.
- Improve user experience and system usability.
- Improve system maintainability and support future scalability.
- Extend the capabilities of existing pages with AI features.


## Scope of Enhancement
This project extends the existing MAGOR platform and focuses on the following areas:

### 1. System Stabilization
- Debugging broken or unstable components
- Restoring incomplete features

### 2. AI Feature Integration
- Transcript summarization
- Interactive chatbot 

### 3. Maintainability Improvements
- Update deprecated dependencies
- Resolve version conflicts
- Improve Docker configuration

### 4. Usability Improvements
- UI adjustments for clarity and consistency

## Project Components
- **[Magor Root](https://github.com/ntuspeechlab/magor-root/tree/ZiXiang-2026)**
- **[Magor Backend](https://github.com/ntuspeechlab/magor-backend/tree/ZiXiang-2026)**
- **[Magor Studio](https://github.com/ntuspeechlab/magor-studio/tree/ZiXiang-2026)**
- **[Magor Frontend](https://github.com/ntuspeechlab/magor-frontend/tree/ZiXiang-2026)**


## Progress Updates (Ongoing Development)

### Week 3
- Implemented transcript download on the Studio page
- Enabled transcript downloads in multiple formats
- Implemented media download on the Studio page
- Recording List UI refinement (column alignment)


### Week 4
- Fixed TextGrid and srt conversion format
- Verified transcript edits reflect in downloads
- Fixed recording list media type display
- Fixed unintended tag removal on backspace
- Removed download button when uploading media

### Week 5-6 
- Set Textgrid files xmin to 0
- Modified download transcript button to support multi-select file options
- Fixed video playback subtitle overflow and incorrect displays
- Implemented download transcript button in Magor Transcript Studio

### Week 7 
- Further investigate video playback issues
- Fixed dropdown unable to open when video is playing
- Modified download button to return ZIP file when multiple files selected
- Update libraries to package json

### Week 8 
- Transcript studio download button reordered to be after publish button
- Filtered empty strings from top words in recordings page
- Restore Admin page functionality
    - Recordings Tab
        - Restored Upload Date display and sorting
        - Restored Path display 
        - Fixed recording edits and deletes to successfully update

### Week 9
- Admin Recording Page:
    - Remove create recording button 
    - Fixed overflowing table due to long displays
- Admin User Page:
    - Fixed user creation errors
    - Resolved status update errors for unverified users
    - Improved user feedback messages (errors and success notifications)
    - Implement email and password format validation on frontend
- Data volumes 
    - Update recordings and transcripts to be stored in code base local files
    - Verify functionalities are not affected due to change in stored location

### Week 10
- Admin Recording Edit Page:
    - Restore retrieval of transcripts
- Data volumes
    - Delete associated files from storage upon file deletion (transcripts, captions etc..)
- Implemented transcript name display and edit in Transcript Studio

### Week 18-19
- Data Volumes
    - Delete image file upon recording deletion 
- Admin ASR Request Page
    - Fixed errors when loading ASR requests
    - Updated the system to retrieve transcription jobs from the correct source
    - Fixed deletion of ASR requests 
    - Update transcript job status of deleted recordings to “deleted” 
    - Performed UI updates and functionality verification

### Week 20
- Admin ASR Request Page
    - Automated deletion of ASR requests
- Admin Recording Page
    - Update recording deletes to also delete associated files
- Restored Admin Statistics Page
- Magor Studio
    - Updated transcription job submission to include speaker count (WIP)

### Weeks 21-23
- Admin User Management Page
    - Fixed error when deleting users using multi-select
- Magor Studio
    - Updated transcription job submission to successfully process speaker count through speechlabs gateway
    - Verified tag metrics on the Statistics page
- Magor Recordings Manager
    - Implemented speaker name change functionality in transcript editing pages
    - Updated UI for Transcript Editor
    - Duplicate speaker name protection feature (add suffix to duplicate names)

### Weeks 24-25
- Added set default button in transcript studio
- Tested project rebuild behavior on a new project copy
- Added "Ask AI" placeholder button to the Recordings page for AI-assisted functionalities

### Weeks 26-28
- Updated Transcript Studio default sorting to display the latest recordings first
- Implemented the "Ask AI" summarization feature
    - Implemented authentication token generation and the core summarization workflow
    - Enhanced the UI, implemented manual polling, and added database persistence for summary results

### Weeks 29-30
- Ask AI Summary Generation Improvements:
    - Improved Summary UI: 
        - Redesigned summary generation to display side-by-side with the recording
        - Added a copy button to copy generated summary text
    - Custom Summary Generation: 
        - Added Custom summary option to specify preferred summary formats 
    - Enhanced Default Summary Prompt: 
        - Refined the default prompt to produce summaries more closely aligned with the YouTube Ask AI format (with timestamps and in concise bullet points)
- Improved Space Utilization on the Recording Page



## Weekly Video Updates
- Full Playlist: [Click to view](https://www.youtube.com/playlist?list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf)
- Week 3: [Click to view](https://www.youtube.com/watch?v=YFmng6AZweY&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=2&t=3s)
- Week 4: [Click to view](https://www.youtube.com/watch?v=uhZ8QfyCrAs&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=1&t=2s)
- Weeks 5-6: [Click to view](https://www.youtube.com/watch?v=Q_wS6xrqj6Y&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=3)
- Week 7: [Click to view](https://www.youtube.com/watch?v=rhO2eFZRLQI&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=4)
- Week 8: [Click to view](https://www.youtube.com/watch?v=fZkDFtAYcSQ&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=5)
- Week 9: [Click to view](https://www.youtube.com/watch?v=lxp7tnyUFRM&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=6)
- Week 10: [Click to view](https://www.youtube.com/watch?v=rXTdchG63Eo&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=7)
- Weeks 18-19: [Click to view](https://www.youtube.com/watch?v=iIJRV6Vm0W4&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=8)
- Week 20: [Click to view](https://www.youtube.com/watch?v=bcWgRbZfMNc&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=9)
- Weeks 21-23: [Click to view](https://www.youtube.com/watch?v=Em2cCCnZ3XE&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=10)
- Weeks 24-25: [Click to view](https://www.youtube.com/watch?v=e-QcabR4aQI&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=11)
- Weeks 26-28: [Click to view](https://www.youtube.com/watch?v=u9uMRD5rS-k&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=12)
- Weeks 29-30: [Click to view](https://www.youtube.com/watch?v=dHhvd4fLUVY&list=PL57jZrvXqjRZAEu3gZtYnKM6Ygbu6mhMf&index=13)
