# Zooms - Jitsi Meet Inspired Demo

This project is a **single-page HTML/CSS/JavaScript demo** that mimics the core features of a Jitsi Meet-powered video conferencing application.  It is **not a functional video conferencing system**; it uses Web APIs and URL parameters to simulate the user experience.

## Features (Simulated)

*   **Role-based UI:**  The interface adapts based on the `role` URL parameter:
    *   `A`:  The meeting initiator.  Gets an audio input selector and a read-only meeting ID field (auto generated if not in the URL).
    *   `B`:  An auto-joining device.  Automatically "joins" the meeting specified by `roomId` and simulates audio device selection using the `audioId`.
    *   `C`:  A regular participant.  Gets an audio input selector and joins a meeting based on `roomId`.
    *  `guest`: If no role, default.
*   **Meeting ID:** Uses the `roomId` URL parameter to "join" a specific meeting.
*   **Audio Input Selection:**  Displays a *mock* list of audio input devices.  (Uses `getMockAudioDevices()` function).
*   **"Connecting" Simulation:** Uses a loading overlay and `setTimeout` to simulate the connection process.
*   **"Auto-Join" for Role B:**  If the `role` is 'B', the demo automatically simulates joining the meeting.
*   **Leave meeting:** Simulates leaving.

## How to Use

1.  **Open `demo.html` in a browser.**
2.  **Use URL parameters:**
    *   **`role` (Required):**  `A`, `B`, `C`, or `guest`.  Determines the user's role.
    *   **`roomId` (Required, except for generating A):**  The ID of the meeting to join.
    *   **`audioId` (Optional, for `B`):** The ID of the audio input device to "select" for role 'B'.

**Example URLs:**

*   **Role A (Initiator):**  `demo.html?role=A` or `demo.html?role=A&roomId=my-meeting`
*   **Role B (Auto-Join Device):** `demo.html?role=B&roomId=my-meeting&audioId=mic2`
*   **Role C (Participant):** `demo.html?role=C&roomId=my-meeting`
*   **Guest:** `demo.html?roomId=my-meeting`

## Important Notes

*   **This is a *DEMO*.** It does not provide real video conferencing functionality.
*   **No Server-Side Code:** This demo is entirely client-side, using only HTML, CSS, and JavaScript. A real video conferencing application *requires* a server.
*   **Mock Audio Devices:** The audio device list is hardcoded for demonstration purposes.  A real application would use `navigator.mediaDevices.enumerateDevices()` to get the actual device list.
*   **No Security/Privacy:** This demo does *not* include any security or privacy measures.
*   **Limited Error Handling:** The demo has very basic error handling.

## Technologies Used (in the Demo)

*   **HTML5:** Structure
*   **CSS3:** Styling
*   **JavaScript:** Logic and "simulation"
*   **Web APIs (used for simulation/mock):**
    *   `URLSearchParams`: To parse URL parameters.
    *   `navigator.mediaDevices.getUserMedia()`:  To access the user's camera and microphone (for the local video feed).
    *   `setTimeout()`: To simulate connection delays.

## Disclaimer

This demo is for illustrative purposes only and should not be used as a basis for a real-world video conferencing application without significant modification and the addition of a robust backend infrastructure. It is intended to show how a simplified UI *could* be structured and how URL parameters *could* be used to control the user experience, but it is not a replacement for a properly engineered video conferencing system.
