# 🌾 AgriChain - Blockchain-Powered Agricultural Supply Chain

<div align="center">

![AgriChain Logo](https://img.shields.io/badge/AgriChain-Blockchain%20Supply%20Chain-16a34a?style=for-the-badge&logo=blockchain)

**Transparent, Traceable, and Trustworthy Farm-to-Table Food System**

[![Node.js](https://img.shields.io/badge/Node.js-22.x-339933?style=flat-square&logo=node.js)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Hyperledger Fabric](https://img.shields.io/badge/Hyperledger-Fabric-2F313A?style=flat-square&logo=hyperledger)](https://www.hyperledger.org/use/fabric)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

**Developed by: Abitha B**

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [User Roles](#user-roles)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## 🎯 Overview

**AgriChain** is an enterprise-grade blockchain supply chain management system designed to bring transparency and trust to agricultural produce tracking from farm to consumer. Built on Hyperledger Fabric blockchain technology, it ensures immutable records of every transaction in the food supply chain, enabling complete traceability and authenticity verification.

The platform connects farmers, quality inspectors, processors, distributors, retailers, and consumers on a single decentralized network, providing real-time visibility into product origins, handling conditions, and journey history.

### Why AgriChain?

- **🔒 Immutable Records**: Every transaction is cryptographically secured on blockchain
- **🌍 End-to-End Traceability**: Track products from harvest to retail shelf
- **✅ Quality Assurance**: Digital quality certifications with tamper-proof records
- **🚛 Real-Time Monitoring**: IoT sensor integration for temperature and humidity tracking
- **👥 Multi-Stakeholder Platform**: Role-based access for all supply chain participants
- **📱 Consumer Transparency**: QR code scanning for instant product verification

---

## ✨ Key Features

### 🔐 Authentication & Authorization
- JWT-based secure authentication
- Role-based access control (RBAC)
- Multi-organization support via Hyperledger Fabric MSPs

### 📦 Product Lifecycle Management
- **Harvest Recording**: Farmers register produce with location and quantity data
- **Quality Inspection**: Certified inspectors grade products with digital certificates
- **Processing Tracking**: Monitor transformation from raw to processed goods
- **Shipment Management**: Real-time logistics tracking with GPS and IoT sensors
- **Retail Inventory**: Store-level inventory management with pricing
- **Consumer Verification**: Public-facing product authenticity checks

### 🌡️ IoT Integration
- Temperature monitoring during transit
- Humidity tracking for perishable goods
- Automated alerts for threshold violations
- Simulated sensor data for development

### 🔍 Blockchain Transparency
- Complete product journey history
- Cryptographic verification of each step
- Immutable audit trail
- Smart contract-based business logic

### 📊 Analytics & Reporting
- Supply chain performance metrics
- Quality trend analysis
- Shipment tracking dashboards
- Audit-ready reports

---

## 🛠 Technology Stack

### Backend
- **Runtime**: Node.js 22.x
- **Framework**: Express.js
- **Blockchain**: Hyperledger Fabric 2.x
- **Authentication**: JWT (JSON Web Tokens)
- **Password Security**: bcryptjs
- **Real-time Communication**: Socket.IO
- **Security**: Helmet.js, CORS

### Frontend
- **Framework**: React 18.x
- **Build Tool**: Vite 5.x
- **State Management**: Zustand
- **Routing**: React Router v6/v7
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Animations**: Framer Motion
- **HTTP Client**: Axios
- **QR Scanning**: html5-qrcode
- **Maps**: Leaflet + React-Leaflet
- **Notifications**: React Hot Toast

### Blockchain
- **Platform**: Hyperledger Fabric
- **Chaincode**: Node.js
- **Consensus**: Raft ordering service
- **Organizations**: FarmerOrg, ProcessorOrg, DistributorOrg, RetailerOrg

### Development Tools
- **Containerization**: Docker & Docker Compose
- **Package Manager**: npm
- **Environment Management**: dotenv

---

## 🏗 System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Frontend (React + Vite)                   │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐   │
│  │  Farmer  │ │Processor │ │Distribut-│ │   Retailer   │   │
│  │Dashboard │ │Dashboard │ │ or      │ │   Dashboard  │   │
│  └──────────┘ └──────────┘ └──────────┘ └──────────────┘   │
└────────────────────────┬────────────────────────────────────┘
                         │ REST API + WebSocket
┌────────────────────────▼────────────────────────────────────┐
│                 Backend (Node.js + Express)                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │ Auth Service │  │ Business     │  │  IoT Simulator   │  │
│  │   (JWT)      │  │ Controllers  │  │  (Sensor Data)   │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
│                           │                                  │
│  ┌────────────────────────▼──────────────────────────────┐  │
│  │         Hyperledger Fabric Gateway                     │  │
│  │    (Mock Mode for Development / Real for Production)  │  │
│  └────────────────────────┬──────────────────────────────┘  │
└───────────────────────────┼──────────────────────────────────┘
                            │ gRPC
┌───────────────────────────▼──────────────────────────────────┐
│              Hyperledger Fabric Network                       │
│  ┌─────────────┐ ┌─────────────┐ ┌──────────────────────┐   │
│  │  Peer Nodes  │ │Orderer Node │ │  Certificate Auth    │   │
│  │  (4 Orgs)    │ │  (Raft)     │ │   Authority (CA)     │   │
│  └─────────────┘ └─────────────┘ └──────────────────────┘   │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐   │
│  │          AgriChain Smart Contract (Chaincode)         │   │
│  │  • addProduct • conductInspection • initiateShipment │   │
│  │  • processProduct • receiveAtRetail • sellProduct    │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** >= 22.x
- **npm** >= 10.x
- **Docker** & **Docker Compose** (for production blockchain deployment)
- **Git**

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/abitha-balakrishnan/agrichain.git
cd agrichain
```

#### 2. Install Dependencies

**Backend:**
```bash
cd backend
npm install
```

**Frontend:**
```bash
cd frontend
npm install
```

#### 3. Environment Configuration

Create `.env` files in both backend and frontend directories:

**backend/.env:**
```env
PORT=5000
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRES_IN=24h
NODE_ENV=development
MOCK_MODE=true
```

**frontend/.env:**
```env
VITE_API_URL=http://localhost:5000/api
```

#### 4. Run the Application

**Development Mode (with Mock Blockchain):**

Start Backend:
```bash
cd backend
npm start
```

Start Frontend (in a new terminal):
```bash
cd frontend
npm run dev
```

**Production Mode (with Real Blockchain):**

Set `MOCK_MODE=false` in `backend/.env` and ensure Hyperledger Fabric network is running:
```bash
cd blockchain/scripts
./network.sh up
```

Then start the application as above.

#### 5. Access the Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:5000/api

---

## 📁 Project Structure

```
agrichain/
├── backend/                    # Node.js Backend
│   ├── src/
│   │   ├── controllers/       # Request handlers
│   │   │   ├── auth.js        # Authentication
│   │   │   ├── farmer.js      # Farmer operations
│   │   │   ├── quality.js     # Quality inspection
│   │   │   ├── processor.js   # Processing operations
│   │   │   ├── distributor.js # Shipment management
│   │   │   ├── retailer.js    # Retail operations
│   │   │   ├── consumer.js    # Public queries
│   │   │   └── ...
│   │   ├── fabric/            # Blockchain integration
│   │   │   ├── gateway.js     # Fabric gateway
│   │   │   ├── mockGateway.js # Mock implementation
│   │   │   └── eventListener.js
│   │   ├── middleware/        # Express middleware
│   │   │   ├── auth.js        # JWT verification
│   │   │   └── upload.js      # File uploads
│   │   ├── routes/            # API routes
│   │   ├── services/          # Business services
│   │   │   └── iotSimulator.js
│   │   └── server.js          # Express app entry
│   ├── tests/                 # Test files
│   ├── .env                   # Environment variables
│   └── package.json
│
├── frontend/                   # React Frontend
│   ├── src/
│   │   ├── components/        # Reusable components
│   │   │   ├── Navbar.jsx
│   │   │   ├── DashboardLayout.jsx
│   │   │   └── NotificationPanel.jsx
│   │   ├── pages/             # Page components
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── farmer/        # Farmer dashboard
│   │   │   ├── quality/       # Inspector dashboard
│   │   │   ├── processor/     # Processor dashboard
│   │   │   ├── distributor/   # Distributor dashboard
│   │   │   ├── retailer/      # Retailer dashboard
│   │   │   └── admin/         # Admin dashboard
│   │   ├── services/          # API services
│   │   │   └── api.js         # Axios instance
│   │   ├── store/             # Zustand stores
│   │   │   ├── authStore.js
│   │   │   └── notificationStore.js
│   │   ├── App.jsx            # Main app component
│   │   └── main.jsx           # Entry point
│   ├── public/                # Static assets
│   └── package.json
│
├── blockchain/                 # Hyperledger Fabric
│   ├── chaincode/             # Smart contracts
│   │   └── agriChaincode.js
│   ├── network/               # Network configuration
│   │   ├── configtx.yaml
│   │   └── crypto-config.yaml
│   └── scripts/               # Deployment scripts
│       └── network.sh
│
├── docker-compose.yml          # Docker orchestration
└── README.md                   # This file
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Authentication Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/auth/register` | Register new user | No |
| POST | `/auth/login` | Login user | No |
| GET | `/auth/me` | Get current user | Yes |

### Farmer Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/farmer/harvest` | Record harvest | Farmer |
| GET | `/farmer/:farmerId/products` | Get farmer's products | Farmer/Admin |

### Quality Inspection Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/quality/inspect` | Conduct inspection | Inspector |
| GET | `/quality/pending` | Get pending inspections | Inspector |
| POST | `/quality/flag` | Flag product issue | Inspector |

### Processor Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/process/add` | Add processed product | Processor |
| GET | `/process/active` | Get active processing | Processor |

### Distributor Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/ship/create` | Create shipment | Distributor |
| PUT | `/ship/:id/location` | Update location | Distributor |
| GET | `/ship/active` | Get active shipments | Distributor |

### Retailer Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/retail/receive` | Receive shipment | Retailer |
| PUT | `/retail/:id/sell` | Sell product | Retailer |
| GET | `/retail/inventory` | Get inventory | Retailer |

### Consumer Endpoints (Public)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/consumer/:productId` | Get product journey | No |
| GET | `/trace/:productId` | Alias for above | No |

### Example Request

```bash
# Login
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"ravi@farmer.com","password":"farmer123"}'

# Use token in subsequent requests
curl -X GET http://localhost:5000/api/farmer/FARMER-TN-001/products \
  -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"
```

---

## 👥 User Roles

### Demo Accounts

| Role | Email | Password | Organization |
|------|-------|----------|--------------|
| **Farmer** | ravi@farmer.com | farmer123 | FarmerOrgMSP |
| **Inspector** | anjali@quality.com | insp123 | ProcessorOrgMSP |
| **Processor** | ops@freshfoods.com | proc123 | ProcessorOrgMSP |
| **Distributor** | dispatch@rapidlogistics.com | dist123 | DistributorOrgMSP |
| **Retailer** | store1@citysupermart.com | ret123 | RetailerOrgMSP |
| **Admin** | admin@agrichain.com | admin123 | AdminOrgMSP |

### Role Permissions

- **Farmer**: Record harvests, view own products
- **Inspector**: Conduct quality checks, flag issues
- **Processor**: Process raw materials, track inventory
- **Distributor**: Manage shipments, update locations
- **Retailer**: Receive goods, manage sales
- **Admin**: Full system access, audit logs

---

## 🧪 Testing

### Manual Testing

1. **Registration Flow**:
   ```
   Navigate to /register → Fill form → Verify email check → Auto-redirect to login
   ```

2. **Complete Supply Chain**:
   ```
   Farmer (harvest) → Inspector (quality check) → 
   Processor (processing) → Distributor (shipment) → 
   Retailer (receive & sell) → Consumer (verify via QR)
   ```

3. **WebSocket Connection**:
   ```
   Open Distributor Map → Check console for socket connection → 
   Verify no "Invalid namespace" errors
   ```

4. **QR Scanner**:
   ```
   Login as Retailer → POS page → Start Camera → 
   Verify camera initializes without "element not found" error
   ```

### API Testing

Use Postman or curl to test endpoints. All protected routes require JWT token in Authorization header.

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow existing code style and conventions
- Write meaningful commit messages
- Add comments for complex logic
- Test your changes thoroughly
- Update documentation if needed

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Abitha B**

- 💼 Full Stack Developer
- 🔗 [GitHub Profile](https://github.com/abitha-balakrishnan)
- 📧 Contact: abithabalakrishnan2005@gmail.com

---

## 🙏 Acknowledgments

- **Hyperledger Fabric** for enterprise blockchain infrastructure
- **React Team** for the amazing UI framework
- **Tailwind CSS** for utility-first styling
- **Open Source Community** for invaluable tools and libraries

---

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/abithab/agrichain/issues) page
2. Create a new issue with detailed description
3. Include steps to reproduce the problem
4. Mention your environment (OS, Node version, etc.)

---

<div align="center">

**Made with ❤️ by Abitha B**

⭐ Star this repository if you found it helpful!

</div>
