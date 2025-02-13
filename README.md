# Zooms - Virtual Meeting Space (Demo)

This project is a **single-page HTML/CSS/JavaScript demo** that creates a *simulated* video conferencing experience inspired by applications like Jitsi Meet. It's important to understand that **this is not a functional video conferencing system**.  It uses Web APIs and URL parameters creatively to mimic the user interface and some behaviors, but it does *not* actually transmit audio or video between users.

## Features (Simulated)

*   **Role-Based UI:**  The interface changes depending on the `role` specified in the URL:
    *   `A`:  The meeting host.  This role gets:
        *   An audio input selection dropdown.
        *   A read-only meeting ID field (auto-generated if not provided in the URL, or can take from URL).
    *   `B`:  A special "auto-join" device.  This role:
        *   Automatically "joins" the meeting specified by `roomId`.
        *   Simulates audio device selection using the optional `audioId` parameter.
        *   Does *not* show the audio input selection dropdown.
    *   `C`:  A standard participant. This role gets:
        *  An audio input selection dropdown.
        *  Joins the meeting based on the provided `roomId`.
    *   `guest`: A standard participant, similar to C, used if no role is provided.

*   **Meeting ID:** The `roomId` URL parameter is used to simulate joining a specific meeting room.
*  **A Role Creates Room ID:** If A role is selected, and no `roomId` is provided, it is auto generated.

*   **Mock Audio Input Selection:**  Presents a dropdown with *predefined, fun-named* audio input options (e.g., "Echo Chamber," "Robot Voice").  These are not real devices.

*   **Connection Simulation:**  A loading overlay with a spinner and a `setTimeout` function are used to simulate the process of connecting to a meeting.

*   **"Auto-Join" for Role B:**  If the `role` is set to 'B', the demo immediately simulates joining the meeting, bypassing the "Join Meeting" button.

*   **Leave Meeting Simulation:** The "Leave Meeting" button simulates leaving the call, hiding the "remote video" and returning to the initial state.

## How to Use / URL Parameters

1.  **Open `demo.html` in a modern web browser.**  (Chrome, Firefox, or Edge are recommended).
2.  **Use URL parameters to control the demo:**
    *   **`role` (Required):**  `A`, `B`, `C`, or `guest`.  Sets the user's role.
    *   **`roomId` (Required, except when role A generates):** The ID of the simulated meeting room.
    *   **`audioId` (Optional, only used by `B`):**  The `deviceId` (from the mock audio device list) to "select" for the auto-joining device.

**Example URLs:**

*   **Role A (Host - generates new Room ID):**  `demo.html?role=A`
*   **Role A (Host - uses provided ID):** `demo.html?role=A&roomId=my-cool-meeting`
*   **Role B (Auto-Join Device - uses provided ID and audio):** `demo.html?role=B&roomId=my-cool-meeting&audioId=mic2`
*   **Role C (Participant):** `demo.html?role=C&roomId=my-cool-meeting`
*  **Guest:** `demo.html?roomId=my-cool-meeting`

## Important Disclaimers

*   **DEMO ONLY:** This is a *demonstration* and *not* a working video conferencing application.  Real video conferencing requires a complex backend infrastructure.
*   **NO REAL-TIME COMMUNICATION:**  No actual audio or video data is transmitted.  The "remote video" is just a placeholder.
*   **NO SERVER:**  The demo is entirely client-side (HTML, CSS, JavaScript).  There is no server-side component.
*   **MOCK DATA:**  Audio devices are hardcoded for the demo.
*   **NO SECURITY/PRIVACY:**  No security or privacy features are implemented.
*   **BROWSER SUPPORT:** The demo is best viewed in modern browsers that support the WebRTC APIs (even though we are not *actually* using the real-time communication parts).

## Technologies Used (for the Simulation)

*   **HTML5:**  Structure of the page.
*   **CSS3:**  Styling and layout, including Flexbox and basic responsiveness.
*   **JavaScript:**  Handles URL parameter parsing, UI updates, and the "fake" connection logic.
*   **Web APIs (limited use, mostly for show):**
    *   `URLSearchParams`:  For parsing URL parameters.
    *   `navigator.mediaDevices.getUserMedia()`:  To access the *local* camera and microphone (only the local video is displayed).
    *   `setTimeout()`:  To create the illusion of connection delays.

This demo focuses on demonstrating a potential front-end user interface and interaction flow. It is *not* a substitute for a real, functional video conferencing application. Building a real application would require a significant backend component (signaling server, media server, etc.) and proper use of the WebRTC APIs for actual data transmission.
