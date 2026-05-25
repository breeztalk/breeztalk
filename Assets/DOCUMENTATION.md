# BreezTalk Documentation

## Table of Contents

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [API Reference](#api-reference)
4. [Architecture](#architecture)
5. [Development Guide](#development-guide)
6. [Deployment](#deployment)
7. [Troubleshooting](#troubleshooting)

## Installation

### Prerequisites

- Node.js 18.x or higher
- npm or yarn
- Git

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/breeztalk.git
cd breeztalk
```

2. Install dependencies:
```bash
npm install
```

3. Start the server:
```bash
node server.js
```

The application will be available at `http://localhost:3000`

## Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
PORT=3000
ADMIN_PASSWORD=your_admin_password_here
VAPID_PUBLIC_KEY=your_vapid_public_key
VAPID_PRIVATE_KEY=your_vapid_private_key
```

### Server Configuration

Edit `server.js` to configure:

- **PORT**: Server port (default: 3000)
- **ADMIN_PASSWORD**: Admin panel password
- **VAPID keys**: For push notifications

## API Reference

### Authentication

#### Admin Authentication

All admin endpoints require authentication via `x-admin-pass` header:

```http
GET /api/admin/users
Headers:
  x-admin-pass: your_admin_password
```

### User Endpoints

#### Register User

```http
POST /api/register
Content-Type: application/json

{
  "name": "John Doe",
  "username": "johndoe",
  "password": "securepassword"
}
```

#### Login User

```http
POST /api/login
Content-Type: application/json

{
  "username": "johndoe",
  "password": "securepassword"
}
```

#### Get User Profile

```http
GET /api/user/:username
```

#### Update User Profile

```http
POST /api/user/update
Content-Type: application/json

{
  "username": "johndoe",
  "name": "John Smith",
  "bio": "New bio"
}
```

### Message Endpoints

#### Send Message

```http
POST /api/message
Content-Type: application/json

{
  "from": "sender_username",
  "to": "recipient_username",
  "text": "Hello!",
  "type": "dm"
}
```

#### Get Messages

```http
GET /api/messages/:chatId
```

### Admin Endpoints

#### Get All Users

```http
GET /api/admin/users
Headers:
  x-admin-pass: your_admin_password
```

#### Block User

```http
POST /api/admin/action
Content-Type: application/json
Headers:
  x-admin-pass: your_admin_password

{
  "username": "johndoe",
  "action": "block",
  "value": true
}
```

#### Verify User

```http
POST /api/admin/action
Content-Type: application/json
Headers:
  x-admin-pass: your_admin_password

{
  "username": "johndoe",
  "action": "verify",
  "value": true
}
```

#### Clear All Data

```http
Socket.IO Event: adminClearAll
{
  "adminPassword": "your_admin_password"
}
```

### File Upload

#### Upload File

```http
POST /api/upload
Content-Type: multipart/form-data

file: <binary file>
```

## Architecture

### Project Structure

```
breeztalk/
├── server.js           # Main server file
├── index.html          # Main application
├── admin.html          # Admin panel
├── package.json        # Dependencies
├── db.json            # Database (JSON)
├── uploads/           # Uploaded files
├── en/               # English documentation
└── ru/               # Russian documentation
```

### Technology Stack

- **Backend**: Node.js, Express, Socket.IO
- **Frontend**: Vanilla JavaScript, HTML5, CSS3
- **Database**: JSON files
- **Real-time**: WebSocket (Socket.IO)
- **Encryption**: Web Crypto API (E2EE)

### Security Architecture

1. **Transport Layer**: HTTPS/TLS
2. **Application Layer**: E2EE encryption
3. **Authentication**: Password-based
4. **Authorization**: Admin password check

### Encryption System

BreezTalk uses end-to-end encryption (E2EE) with Diffie-Hellman key exchange:

1. **Key Generation**: Each user generates DH key pair
2. **Key Exchange**: Public keys are exchanged via server
3. **Message Encryption**: Messages encrypted with recipient's public key
4. **Message Decryption**: Recipient decrypts with private key

## Development Guide

### Adding New Features

1. **Backend Changes**: Modify `server.js`
2. **Frontend Changes**: Modify `index.html` or `admin.html`
3. **Database Changes**: Modify `db.json` structure
4. **Testing**: Test thoroughly before deployment

### Code Style

- Use camelCase for variables
- Use PascalCase for classes
- Use UPPER_CASE for constants
- Add comments for complex logic

### Git Workflow

1. Create feature branch: `git checkout -b feature-name`
2. Make changes and commit: `git commit -m "Description"`
3. Push to remote: `git push origin feature-name`
4. Create pull request

## Deployment

### Production Setup

1. **Environment Variables**: Set production environment variables
2. **HTTPS**: Configure SSL/TLS certificates
3. **Database**: Use proper database (PostgreSQL, MongoDB)
4. **Process Manager**: Use PM2 or similar
5. **Monitoring**: Set up logging and monitoring

### PM2 Setup

```bash
npm install -g pm2
pm2 start server.js --name breeztalk
pm2 save
pm2 startup
```

### Nginx Configuration

```nginx
server {
    listen 80;
    server_name yourdomain.com;
    
    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

## Troubleshooting

### Common Issues

#### Server won't start

**Problem**: Server fails to start
**Solution**: Check if port 3000 is already in use

```bash
netstat -ano | findstr :3000
```

#### Database errors

**Problem**: Database file corruption
**Solution**: Restore from backup or recreate `db.json`

#### Socket.IO connection issues

**Problem**: Real-time features not working
**Solution**: Check firewall settings and WebSocket support

#### File upload failures

**Problem**: Files not uploading
**Solution**: Check `uploads/` directory permissions

### Debug Mode

Enable debug logging by setting:

```javascript
const DEBUG = true;
```

### Logs

Check server logs for errors:

```bash
pm2 logs breeztalk
```

## Support

For additional help:
- Email: official.breeztalk@gmail.com
- GitHub Issues: [repository issues]
- Documentation: [full documentation link]

## License

AGPL-3.0 License - see LICENSE file for details
