Janforum.AI --- Your Complaints, Our Priority
Janforum.AI is a civic grievance reporting and tracking frontend
designed to connect citizens with municipal officers. Citizens can
report local problems in their preferred language, attach photographs,
share the issue location, and follow complaint progress. Officers can
review, prioritize, and update complaints through a dashboard.
Project status: This repository currently contains the frontend
HTML file. The page supports a browser-only demo mode and can connect
to a compatible backend API when one is available.

Overview
The goal of Janforum.AI is to make civic issue reporting more accessible
and transparent. It provides a common interface for reporting problems
such as water-supply interruptions, street-light failures, drainage
issues, garbage accumulation, and road damage.
Key Features
Citizen portal
- Citizen registration and login interface.
- Submit complaints with a written or spoken description.
- Language selection for nine Indian languages: English, Hindi,
  Marathi, Gujarati, Tamil, Telugu, Kannada, Malayalam, and Bengali.
- Upload an issue photograph or capture one using the device camera.
- Capture the current GPS coordinates, or provide a landmark and
  administrative area.
- View the complaint location on a map.
- Receive a complaint tracking ID and follow its status.
- View general and department-wise civic statistics.
- Browse community posts showing completed work, with likes and
  comments.
Officer portal
- Separate officer login and dashboard.
- View complaints and filter the action queue by district.
- Review priority, urgency indicators, complaint details, photographs,
  and location.
- Update complaint status through the workflow.
- Review reports held in the junk/spam queue.
- Record work updates and completion information.
- View general and department-wise statistics.
Complaint workflow
The interface includes these main stages:

Submitted → AI Verified → Assigned → In Progress → Resolved

It also supports rejected and failed outcomes, with reasons displayed to
the citizen.
Location and mapping
- Browser geolocation can capture latitude and longitude.
- Citizens can select district, urban local body, sub-district
  (taluka), and ward.
- Google Maps embeds are used for location previews and route viewing.
- Leaflet is included in the page for map functionality.
Built-in analysis and validation
The browser demo includes JavaScript logic for language handling,
complaint categorization, urgency scoring, duplicate-report matching,
and photo/text checks. The source also includes an image-analysis
heuristic intended to flag suspicious or AI-generated-looking images.

Important: These are prototype/demo checks implemented in the
frontend, not a guarantee of accurate AI detection or an independently
validated AI model. Results should be reviewed by an authorized person
before real-world decisions are made.
Technology Stack
  Technology                          Purpose
  HTML5                               Page structure and forms

  CSS3                                Responsive layout, styling, and
dashboard components

  JavaScript                          UI interactions, complaint
workflow, validation, and demo data
handling

  Browser Local Storage               Saves demo-mode data in the current
browser

  Browser Geolocation API             Captures the citizen's location

  MediaDevices / Camera API           Captures a live complaint
photograph

  Web Speech API                      Voice input for complaint
descriptions

  Google Maps embeds                  Displays complaint locations and
routes

  Leaflet 1.9.4                       Mapping library included by the
page
Google Fonts (Poppins)              Interface typography
External browser libraries and fonts are loaded from CDNs, so an
internet connection is required for those resources.
Project Structure
Janforum.AI/
├── abhijeet frontend.html   # Main application frontend
└── README.md                # Project documentation
You can rename abhijeet frontend.html to index.html if you want it
to be the default page on a static hosting service.
Getting Started
Option 1: Run the browser demo
1. Download or clone the project.
2. Open the project folder.
3. Open abhijeet frontend.html in a modern browser such as Google
   Chrome, Microsoft Edge, or Safari.
For camera, microphone, and location features, browsers generally
require a secure context. Use localhost or HTTPS and grant the
relevant browser permissions.

A simple local server can be started from the project directory with
Python:
python -m http.server 8000
Then open:
http://localhost:8000/abhijeet%20frontend.html
In browser-only demo mode, data is stored in that browser using Local
Storage. It is not automatically shared with other devices or users.
Clearing browser site data may remove demo records.
Option 2: Connect a backend
On startup, the frontend checks:
GET /api/health
If the endpoint returns a successful response with JSON containing
{"ok": true}, the frontend switches to server mode and uses the
backend API.

The frontend references these API routes:
  Method                  Endpoint                    Purpose
  GET                     /api/health               Detect backend
availability

  GET                     /api/me                   Retrieve the current
session

  GET                     /api/state                Retrieve complaint and
community-post state

  GET                     /api/stats?days={days}    Retrieve dashboard
statistics

  POST                    /api/auth/register        Register a citizen

  POST                    /api/auth/login           Citizen login

  POST                    /api/auth/officer         Officer login

  POST                    /api/auth/logout          End the session

  POST                    /api/complaints           Submit a complaint

  POST                    /api/posts/{id}/like      Like or unlike a
community post

  POST                    /api/posts/{id}/comment   Add a comment

  PATCH                   Used by complaint/status    Update complaint
update logic                information
DELETE                  /api/admin/reset          Admin demo-data reset
The backend is not included in the supplied HTML file. To enable
server mode, build or provide a compatible backend implementing the
routes and request/response formats expected by the frontend. Serve the
frontend and API from the same origin, or configure an appropriate
deployment proxy.
Demo Officer Accounts
The HTML file contains the following demo officer credentials:

  Officer ID   Password       Access shown in the interface
  pmc        pmc@2026     Pune Municipal Corporation
bmc        bmc@2026     BMC
admin      sevify2026   All districts / admin

These credentials are for demonstration only. Do not use them in a
production deployment. The browser-only demo also does not provide
production-grade authentication or access control.
Browser Permissions
Some features depend on browser support and user permission:
- Location: Allow location access to capture GPS coordinates.
- Camera: Allow camera access to take a live issue photograph.
- Microphone: Allow microphone access for voice complaint entry.
- Internet: Required for CDN-hosted fonts, mapping resources, and
  browser speech services.
If a permission is unavailable, the interface provides alternatives such
as uploading a photograph or entering a place/landmark manually.
Privacy and Security Notes
The interface is designed to keep citizen contact details separate from
the officer-facing complaint view. However, the supplied file alone
cannot guarantee privacy or security in a real deployment.

Before production use: - Implement secure server-side authentication and
role-based authorization. - Validate and sanitize all submitted text and
uploaded files on the server. - Protect personal information and define
retention/deletion policies. - Use HTTPS and secure session cookies. -
Restrict administrative actions and log important status changes. -
Review photo-validation and urgency results manually; do not treat
heuristic scores as proof. - Obtain consent before collecting precise
location, photographs, or contact information.
Future Improvements
- Connect a production-ready backend and database.
- Add verified AI/NLP services for multilingual complaint
  understanding and classification.
- Improve duplicate detection and image verification using tested
  models.
- Add notifications through email, SMS, or WhatsApp.
- Add audit logs, service-level timelines, and department-level
  performance reports.
- Conduct accessibility, security, and usability testing with citizens
  and municipal staff.
Contributing
Contributions and suggestions are welcome. For changes:
1. Fork the repository.
2. Create a feature branch.
3. Make and test your changes.
4. Submit a pull request with a clear description.
License
No license information was included in the supplied project file. Add a
LICENSE file before distributing or reusing the project publicly.
