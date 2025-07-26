# PatientPrep-SL

## Project Description

This project develops an edge-based AI assistant designed to help patients in Sri Lanka prepare effectively for their medical consultations. Recognizing that many patients face challenges in clearly communicating their symptoms, medication details, and concerns—due to forgetfulness, poor organization, nervousness, and limited consultation time—the assistant provides proactive guidance to gather and organize essential health information in advance.

The AI assistant enables patients to log symptoms, record medications, and prepare questions, generating a clear, structured summary to share with their doctors. This improves communication quality, enhances diagnostic accuracy, and increases consultation efficiency. By processing and storing all personal health data locally on the device, the solution ensures patient privacy and complies with Sri Lankan data protection laws.

Designed as a mobile application, the assistant is accessible, user-friendly, and fits naturally into patients’ daily routines. It complements existing healthcare tools by filling the critical gap in consultation preparation, ultimately empowering patients and supporting better healthcare outcomes.

## User App (React Native with Expo Go):

1. User Authentication & On-Device Storage:

Simple email/password signup/login for app access.
Crucial: All user-inputted health data (symptoms, notes, medications, questions) is stored encrypted locally on the user's device only. The app will explicitly inform the user of this.

2. Appointment Planner:
   Ability to add upcoming doctor's appointments (date, time, doctor's name, specialty).

3. Symptom Log & Detailer:

Users can log symptoms, indicating onset, duration, severity, and any aggravating/alleviating factors.
Agentic Nudge: The AI agent can prompt users with general questions like
"When did this symptom start?" or "Does anything make it better or worse?"

4. Medication List Manager:

Record current medications, dosage, and frequency.
Agentic Nudge: "Don't forget to list any over-the-counter medicines you're taking!"

5. Questions for Doctor Builder:

Users can list specific questions they want to ask their doctor.
gentic Nudge: Based on logged symptoms (e.g., "If you're experiencing [symptom], consider asking about [common lifestyle factor] or [next steps if symptoms worsen]."). These are general prompts, not medical advice.

6. "Consultation Summary" Generator (Pre-Consultation):

A consolidated, easy-to-read summary of symptoms, medications, and questions that the patient can review before the appointment.
No sharing functionality for MVP beyond showing on screen. Patient can read it out, or ideally, the doctor might view it on the patient's phone if they choose to
show it.

7. Post-Consultation Notes (Local):

Users can jot down notes or action points after their consultation for personal reference.

## Admin Panel (None for MVP relevant to sensitive data):

• For this highly constrained MVP, there is no admin panel that interacts with or views user-inputted health data, as it's all local.

• A basic admin panel might exist for managing app-level static content (e.g., general wellness tips) if any are pushed via the app.

## Technology Stack (Optimized for Solo Developer)

• Front-end (Mobile App):
React Native with Expo Go (JavaScript/TypeScript).

    Rationale:
    Rapid prototyping, single codebase for iOS/Android, managed workflow, and robust SDK.
    Local Storage: Heavily rely on Expo's SecureStore, AsyncStorage, or a local database library (e.g., SQLite via Expo's expo-sqlite) for all patient-entered data.

    Crucial: Data must be stored securely and encrypted locally.

• Backend & Cloud Services:
Firebase (Google Cloud Platform).

    Rationale: Used ONLY for user authentication (email/password), non-sensitive app-level configuration (e.g., list of pre-approved generic wellness tips), and analytics (e.g., app usage, feature engagement, not health data).

    Firebase Authentication: For app access.

    Cloud Firestore (NoSQL Database): For non-sensitive app data (user preferences for general nudges, app versioning, general content). NO PHI.

    Cloud Functions for Firebase: For serverless backend logic for generic agentic nudges (e.g., push notification reminders for appointments), not processing PHI.

    Firebase Cloud Messaging (FCM): For general app reminders (e.g., "Your appointment is tomorrow! Have you prepared your questions?").

    Firebase Analytics: For tracking app usage patterns and feature adoption (e.g., how many users use the symptom logger), but not collecting or analyzing actual symptom data.

    Firebase Hosting: For hosting the privacy policy and disclaimers.

• Agentic Logic: Initially rule-based logic implemented directly in React Native code or as part of very simple Cloud Functions that trigger general reminders. These are general prompts based on common user actions or time-based triggers, not analyzing patient's specific health inputs.

## Architecture Overview

![Architecture](https://github.com/Yuraj-Isurinda/PatientPrep-SL/blob/main/Architecture%20(3).png)
