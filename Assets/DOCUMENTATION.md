📚 BreezTalk Documentation
🌟 Messenger Overview
BreezTalk is a modern messenger featuring end-to-end encryption (E2EE), designed for secure and private communication. The messenger ensures complete confidentiality of correspondence and robust user data protection.

🎯 Core Features
💬 Communication
Private Messages – One-on-one private chats between two users.

Group Chats – Communication in groups with an unlimited number of participants.

Channels – Public channels for broadcasting and subscriptions.

Calls – Audio and video calls protected by E2EE encryption.

🔐 Security
E2EE Encryption – All messages are encrypted end-to-end.

Diffie-Hellman Keys – Secure key exchange protocol.

MITM Protection – Man-in-the-middle attacks are impossible.

Privacy – The server has no access to message content.

🎨 Interface
Dark/Light Theme – Switchable UI themes.

Responsive Design – Optimized for all devices.

Push Notifications – Instant alerts for new messages.

Online Status – Real-time visibility of user activity.

🏗️ Architecture
🖥️ Backend
Node.js – Server runtime.

Express – Web framework for the HTTP API.

Socket.IO – WebSockets for real-time communication.

JSON Database – Simple and reliable data storage.

🌐 Frontend
Vanilla JavaScript – Dependency-free logic.

HTML5 – Modern semantic markup.

CSS3 – Advanced styling and animations.

WebPush API – Native push notifications.

🔐 Encryption
Diffie-Hellman – Key exchange mechanism.

AES Encryption – Message content encryption.

WebRTC – Encrypted audio/video streaming.

📋 Functional Requirements
🔑 Registration and Authentication
Username – Minimum 5 English letters.

Password – Minimum 6 digits.

Name – Any name, supports Cyrillic characters.

Auto Key Generation – Keys are generated automatically during registration.

💬 Messaging
Text Messages – No character length limits.

Files – Exchange files of any type.

Media – Images, video, and audio support.

Delivery – Instant message delivery.

👥 Users
Profiles – Name, username, avatar, and bio.

Online Status – Real-time activity tracking.

Search – Find users by their username.

Blocking – Ability to block unwanted users.

🏢 Administration
Admin Panel – User management interface.

Moderation – Blocking and verification tools.

Statistics – User activity and growth data.

Backup – Automatic database backups.

🔄 Processes
📝 User Registration
Data Entry – User enters name, username, and password.

Validation – System checks data requirements.

Key Generation – DH encryption keys are created.

Storage – Data is saved to the database.

Authentication – User is logged into the system.

💬 Sending a Message
Creation – User writes the text.

Encryption – Message is encrypted using the recipient's public key.

Transmission – The encrypted data is sent to the server.

Delivery – The server forwards the message to the recipient.

Decryption – The recipient decrypts the message using their private key.

📞 Calling
Initiation – User starts a call.

WebRTC Connection – A P2P connection is established.

E2EE Media – Audio/video streams are encrypted.

Connection – Direct link between participants.

Termination – Connection is closed.

🗂️ Project Structure
breeztalk/
├── server.js                 # Main server file
├── index.html                # Main interface
├── admin.html                # Admin panel
├── download.html             # Download page
├── package.json              # Project dependencies
├── db.json                   # Database file
├── uploads/                  # Uploaded files
├── vps-setup/                # VPS configuration
│   └── installation-guide    # VPS setup instructions
└── DOCUMENTATION.md          # This documentation
🔧 Technical Details
🌐 API Endpoints
POST /auth – Authentication.

POST /register – Registration.

GET /users/:username – User profile retrieval.

POST /upload – File uploading.

GET /rooms – List of available rooms.

📡 WebSocket Events
connection – New connection established.

message – New message received.

typing – User is typing indicator.

online – Online status update.

call – Call event.

🔐 Encryption Logic
JavaScript
// Key Generation
const privKey = generateDHPrivateKey();
const pubKey = generateDHPublicKey(privKey);

// Message Encryption
const encrypted = encrypt(message, recipientPublicKey);

// Message Decryption
const decrypted = decrypt(encrypted, privateKey);
🛡️ Security
🔒 Layers of Protection
Transport Layer – HTTPS/TLS for all connections.

Application Layer – E2EE for messages and media.

Server-Side – Protection against DDoS and injections.

Client-Side – XSS and CSRF protection.

🚫 What is NOT stored
Message Text – Only encrypted data passes through.

Media Files – Encrypted before uploading.

Encryption Keys – Stored locally on user devices only.

Private Info – Minimal metadata collection.

✅ What IS stored
Public Keys – Necessary for encryption.

File Hashes – For integrity verification.

Metadata – Timestamp and delivery status.

Statistics – General usage information.

📱 User Interface
🏠 Home Screen
Chat List – All active user dialogues.

Search – Quick user lookup.

Menu – Settings and profile access.

Navigation – Switching between app sections.

💬 Chat Screen
Message History – All messages in the dialogue.

Input Field – Text and media input.

Action Buttons – Send, attach files, call.

Info – Details about the chat partner.

⚙️ Settings
Profile – Edit name, avatar, and bio.

Security – Change password.

Privacy – Access and visibility settings.

Theme – Toggle Dark/Light mode.

🚀 Deployment
🖥️ Server Requirements
Node.js 18+ – Runtime environment.

Nginx – Web server.

SSL Certificate – Required for HTTPS.

Ports 80/443/3000 – For web and application traffic.

📦 Installation
Bash
# Clone the repository
git clone https://github.com/username/breeztalk.git
cd breeztalk

# Install dependencies
npm install

# Start the application
npm start
🔧 Configuration
JavaScript
// server.js
const PORT = 3000;
const DB_FILE = 'db.json';
const UPLOAD_DIR = 'uploads/';
🔄 Updates and Support
📅 Versions
v1.0.0 – Base functionality.

v1.1.0 – Calls and media support.

v1.2.0 – Mobile-optimized version.

v2.0.0 – Federation and bots.

🐛 Bugs and Fixes
GitHub Issues – Problem tracking.

Pull Requests – Community contributions.

Changelog – History of changes.

📞 Support
🆘 Contacts
Email: official.breeztalk@gmail.com

Official Channel: @breeztalk

GitHub: Project repository.

📚 Resources
Documentation: Full API documentation.

Code Samples: Pre-built solutions.

Community: Support forum and chat.

📄 License
MIT License – Free and open-source software.

🌟 Conclusion
BreezTalk is a messenger that prioritizes privacy and security. Built with open-source code and modern encryption technologies, it provides reliable protection for user communications.

Key Advantages:

✅ Full message privacy.

✅ Open-source code.

✅ Modern technology stack.

✅ User-friendly experience.

✅ Active development.

BreezTalk – The messenger you can trust!
