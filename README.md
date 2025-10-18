# 🛡️ ZeroBot - Advanced Anti-Bot Protection System (Uncompleted) 

A comprehensive, intelligent anti-bot protection system built with Node.js, Express, MongoDB, and AdminJS. ZeroBot provides real-time bot detection, proxy blocking, geographic restrictions, and advanced behavioral analysis to protect your websites from automated threats.

![ZeroBot Dashboard](https://img.shields.io/badge/Dashboard-AdminJS-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Node.js](https://img.shields.io/badge/Node.js-18+-brightgreen)
![MongoDB](https://img.shields.io/badge/Database-MongoDB-green)

## 🌟 Features

### 🤖 Advanced Bot Detection
- **Browser Fingerprinting**: Canvas, WebGL, and audio fingerprinting
- **Behavioral Analysis**: Mouse movements, clicks, and scrolling patterns
- **Network Analysis**: Datacenter IP detection, proxy/VPN identification
- **User Agent Analysis**: Suspicious browser signatures and automation tools
- **Custom Rules Engine**: Priority-based blocking rules with conditions

### 🌍 Geographic Control
- **Country-based Blocking**: Allow/block traffic by country codes
- **IP Geolocation**: Real-time location detection using GeoIP
- **Time Zone Restrictions**: Access control by time zones and hours

### 🛡️ Proxy & VPN Protection
- **Datacenter Detection**: Identifies hosting providers and cloud services
- **Proxy/VPN Blocking**: Detects and blocks anonymous networks
- **Tor Network Detection**: Identifies Tor exit nodes
- **Custom IP Blacklists**: Maintain custom blocked IP ranges

### 📊 Real-time Analytics
- **Live Dashboard**: Monitor threats and statistics in real-time
- **Detection Logs**: Detailed request analysis and blocking reasons
- **User Management**: Customer accounts with API key authentication
- **Performance Metrics**: Request processing times and success rates

### � Easy Integration
- **Simple JavaScript Tag**: One-line integration for any website
- **REST API**: Complete programmatic access
- **Webhook Support**: Real-time notifications for security events
- **Multiple Subscription Tiers**: Free, Pro, and Enterprise plans

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- MongoDB Atlas account or local MongoDB installation
- NPM or Yarn package manager

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/zerobot.git
cd zerobot
```

2. **Install dependencies**
```bash
npm install
```

3. **Configure environment variables**
Create a `.env` file in the root directory:
```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/zerobot
JWT_SECRET=your-secret-key-here
NODE_ENV=development
PORT=3000
```

4. **Initialize the database**
```bash
# Create admin user and sample data
node setup-admin.js
node setup-rules.js
```

5. **Start the server**
```bash
npm start
```

6. **Access the application**
- **Main Website**: http://localhost:3000
- **Admin Dashboard**: http://localhost:3000/admin (admin@zerobot.com / admin123)
- **API Documentation**: http://localhost:3000/api

## 📖 Usage Guide

### For Website Owners

#### 1. Register for Free Account
Visit http://localhost:3000 and click "Get Started Free" to create your account.

#### 2. Get Your API Key
After registration, copy your unique API key from the dashboard.

#### 3. Add Protection Script
Add this single line to your website's `<head>` section:

```html
<script src="http://localhost:3000/zerobot.js" 
        data-api-key="YOUR_API_KEY_HERE"></script>
```

#### 4. Configure Protection Settings
Use the dashboard to customize:
- Bot detection sensitivity
- Geographic restrictions
- Time-based access control
- Custom blocking rules

### Admin Dashboard Features
- **User Management**: View and manage customer accounts
- **Detection Logs**: Real-time request monitoring and analysis  
- **Bot Rules**: Configure custom detection rules with priorities
- **Analytics**: Visual charts and statistics
- **System Health**: Monitor server performance

## 🔧 Bot Detection Configuration

### Detection Methods & Scoring
- **Fingerprint Analysis** (30 points): Browser uniqueness detection
- **Behavioral Analysis** (25 points): Mouse movement and interaction patterns  
- **Network Analysis** (30 points): IP reputation and datacenter detection
- **User Agent Analysis** (15 points): Browser signature validation

### Thresholds
- **Bot Threshold**: 70 points (request blocked)
- **Suspicious Threshold**: 40 points (logged for review)
- **Human Threshold**: <40 points (request allowed)

## 📊 API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile

### Protection Endpoints  
- `POST /api/protection/check` - Check if request should be blocked
- `GET /api/stats` - Get dashboard statistics (authenticated)
- `GET /api/logs` - Get detection logs (authenticated)

### Example API Usage
```javascript
// Check request protection
const response = await fetch('/api/protection/check', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-API-Key': 'your-api-key'
  },
  body: JSON.stringify({
    ip: '192.168.1.1',
    userAgent: 'Mozilla/5.0...'
  })
});

const result = await response.json();
if (result.blocked) {
  console.log('Blocked:', result.reason);
}
```

## 🏗️ Project Structure

```
zerobot/
├── config/                 # Configuration files
│   └── admin.js            # AdminJS dashboard setup
├── middleware/             # Express middleware
│   └── auth.js             # JWT authentication
├── models/                 # MongoDB schemas
│   ├── User.js             # User accounts
│   ├── DetectionLog.js     # Request logs
│   └── BotRule.js          # Detection rules
├── routes/                 # API endpoints
│   ├── auth.js             # Authentication routes
│   ├── protection.js       # Bot detection API
│   └── dashboard.js        # Dashboard API
├── services/               # Business logic
│   └── botDetection.js     # Core detection engine
├── public/                 # Static files
│   ├── index.html          # Landing page
│   ├── login.html          # Login page
│   ├── signup.html         # Registration page
│   ├── dashboard.html      # User dashboard
│   └── zerobot.js          # Client-side script
└── server.js               # Main application
```

## 🛡️ Security Features

### Authentication & Data Protection
- JWT token-based authentication
- API key authentication for client requests
- Password hashing with bcrypt (12 rounds)
- Request rate limiting and DDoS protection
- Input validation and sanitization

## 🧪 Testing

### Test Pages
- **Auth Test**: http://localhost:3000/test-auth.html
- **Detection Test**: http://localhost:3000/test-detection.html  
- **Integration Example**: http://localhost:3000/integration-example.html

### Manual Testing
```bash
# Test authentication
node test-auth.js

# Test API endpoint
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","password":"test123"}'
```

## 🚀 Deployment

### Environment Variables for Production
```env
NODE_ENV=production
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/zerobot
JWT_SECRET=your-super-secret-jwt-key
PORT=3000
```

### Production Checklist
- [ ] Change default admin password
- [ ] Set strong JWT secret
- [ ] Configure MongoDB Atlas with authentication
- [ ] Set up SSL/TLS certificates
- [ ] Configure reverse proxy (nginx)
- [ ] Set up monitoring and logging

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

- [GitHub Issues](https://github.com/yourusername/zerobot/issues)
- Email: support@zerobot.com
- Complete API documentation available at `/api`

## 🙏 Acknowledgments

- [AdminJS](https://adminjs.co/) - Beautiful admin interface
- [Express.js](https://expressjs.com/) - Web framework  
- [MongoDB](https://www.mongodb.com/) - Database
- [Mongoose](https://mongoosejs.com/) - MongoDB ODM

---

**Built with ❤️ for web security**

*Protecting websites from automated threats, one request at a time.*

### Blocking Options
1. **Country Blocking** - Whitelist/blacklist countries
2. **Time Restrictions** - Allow access only during specific hours
3. **IP Blocking** - Block specific IP addresses
4. **User Agent Blocking** - Block specific user agents
5. **Custom Rules** - Advanced rule engine

## Admin Dashboard Features

- User management (customers, subscriptions, API keys)
- Real-time detection logs and analytics  
- Bot rule configuration
- Country and IP blocking management
- Usage statistics and reporting
- System health monitoring

## Subscription Tiers

- **Free**: 1,000 requests/day, basic bot detection
- **Basic**: 10,000 requests/day, country blocking, basic analytics
- **Premium**: 100,000 requests/day, advanced features, detailed logs
- **Enterprise**: Unlimited requests, custom rules, priority support

## Database Schema

### Users Collection
- User information, API keys, subscription details
- Protection settings (country blocking, time restrictions, etc.)
- Usage statistics

### Detection Logs Collection  
- All bot detection attempts and results
- Detailed fingerprinting and behavior data
- Performance metrics

### Bot Rules Collection
- Custom detection rules
- Conditions and actions
- Priority and severity levels

## Development

### Project Structure
```
zerobot/
├── config/           # Configuration files
│   ├── database.js   # MongoDB connection
│   └── admin.js      # AdminJS setup
├── models/           # Mongoose schemas  
│   ├── User.js       # User model
│   ├── DetectionLog.js # Detection logs
│   └── BotRule.js    # Bot rules
├── routes/           # API routes
│   ├── auth.js       # Authentication
│   └── protection.js # Protection API
├── services/         # Business logic
│   └── botDetection.js # Bot detection service
├── middleware/       # Express middleware
│   └── auth.js       # Authentication middleware
├── public/           # Static files
│   ├── zerobot.js    # Client script
│   └── integration-example.html
├── package.json      # Dependencies
└── server.js         # Main server file
```

### Running in Development
```bash
# Install dependencies
npm install

# Start with nodemon for auto-restart
npm run dev

# Run tests (if available)
npm test
```

## Security Considerations

1. **API Key Security** - Store API keys securely, rotate regularly
2. **Rate Limiting** - Implement proper rate limiting on all endpoints  
3. **Input Validation** - Validate all user inputs
4. **HTTPS Only** - Use HTTPS in production
5. **CORS Policy** - Configure CORS appropriately
6. **Session Security** - Secure session configuration

## Deployment

### Production Setup
1. Set environment variables
2. Configure reverse proxy (nginx)
3. Enable HTTPS/SSL  
4. Set up monitoring and logging
5. Configure backup strategy

### Docker Deployment
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

## Support

- Documentation: Visit the integration example at `/`
- API Reference: `/api` endpoint  
- Admin Dashboard: `/admin`
- GitHub Issues: [Create an issue](https://github.com/your-repo/zerobot/issues)

## License

MIT License - see LICENSE file for details.

---

**ZeroBot** - Advanced Anti-Bot Protection System 🤖🛡️
