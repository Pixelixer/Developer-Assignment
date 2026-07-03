1. Table for Event tracking schema
| Event Name            | Trigger Type   | Key Parameters                             | GA4 Report/Audience |
|:---                   |:---            |:---                                        |:---                 |
| booking_step_complete | Custom Event   | step_number, step_name, clinic_location    | Funnel Exploration  |
| call_button_click     | Click (Button) | button_location, clinic_name, phone_number | Engagement/Calls    |
| whatsapp_chat_click   | Click (Link)   | button_type, page_url, click_timestamp     | Engagement/WhatsApp |




2. Booking Form Funnel Tracking (JSON DataLayer)To track funnel drop-off, I implemented a dataLayer push at the completion of every step of the 3-step booking form.  
Step 1: Clinic & Specialty Selected

JSON
{
  "event": "booking_step_complete",
  "step_number": 1,
  "step_name": "location_specialty_selected",
  "clinic_location": "Bengaluru_Indiranagar"
}
Step 2: Details Entered

JSON
{
  "event": "booking_step_complete",
  "step_number": 2,
  "step_name": "details_entered",
  "clinic_location": "Bengaluru_Indiranagar"
}
Step 3: Booking Confirmed

JSON
{
  "event": "booking_step_complete",
  "step_number": 3,
  "step_name": "booking_confirmed",
  "clinic_location": "Bengaluru_Indiranagar"
}
3. Google Ads Conversion Action
Action: booking_confirmed. 
Why: This is the final step in our funnel. Importing this event helps the Google Ads algorithm focus on users who actually complete an appointment, rather than just clicking through the first few steps. This results in much better lead quality for the client.  
4. Technical Implementation
I wrrote the dataLayer pushes directly into the front-end code myself. GTM cannot automatically track multi-step form interactions on its own, so I manually placed triggers at every state-change of the form. This allows me to accurately see where users are dropping off in the GA4 Funnel Exploration.