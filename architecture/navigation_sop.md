# SOP: Navigation Layer (Decision Making)

## Overview
This SOP defines how the System Pilot navigates between the User's source code and the Conversion Tools.

## 1. Request Handling
- When a user provides Selenium code via the UI or chat:
    1. Read the code and identify TestNG/Selenium patterns.
    2. Reference `architecture/conversion_sop.md` for specific mapping rules.
    3. Use the defined JSON Data Schema in `gemini.md` for internal payloads.

## 2. Model Selection
- **Requested Model:** Gemini 3 Flash.
- **Role:** High-speed, high-accuracy code translation following the conversion SOP.

## 3. Output Delivery
- If the request is for a whole directory, use `tools/converter.py` logic to write files.
- If the request is for an immediate snippet, return the Playwright TS formatted code directly.
- Ensure the result is displayed in the UI as per the "Delivery Payload" discovery.

## 4. Error Handling
- If the source code is not Selenium Java or is malformed, identify the specific line and request clarification from the user before proceeding.
