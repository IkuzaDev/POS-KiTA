 # POS-kita - Point of Sale System

[![Node.js](https://img.shields.io/badge/Node.js-18.x-green.svg)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-4.18.2-blue.svg)](https://expressjs.com/)
[![SQLite](https://img.shields.io/badge/SQLite-3.x-orange.svg)](https://sqlite.org/)
[![License](https://img.shields.io/badge/License-ISC-yellow.svg)](LICENSE)

A comprehensive, enterprise-grade Point of Sale system with advanced inventory management, recipe tracking, and multi-role user access control. Built with modern web technologies and designed for restaurants, cafes, and retail businesses.

## 🚀 Features

### Core Functionality
- **🛒 Transaction Processing**: Complete POS interface with real-time cart management
- **👥 Multi-Role Access Control**: Admin, Manager, and Cashier roles with granular permissions
- **📦 Inventory Management**: Real-time stock tracking with low-stock alerts
- **📋 Recipe Management**: Ingredient-based product recipes with automatic stock deduction
- **📊 Advanced Reporting**: Sales, inventory, and cost analysis reports
- **🔒 Security**: CSRF protection, secure sessions, and bcrypt password hashing
- **⚡ Real-time Updates**: Socket.IO for live inventory and transaction updates

### Business Intelligence
- **📈 Sales Analytics**: Daily, monthly, and custom date range reports
- **💰 Cost Analysis**: Product profitability and ingredient cost tracking
- **📋 Inventory Reports**: Stock levels, usage patterns, and reorder alerts
- **🎯 Product Performance**: Best-selling products and revenue analysis

## 🏗️ Architecture Overview

### Technology Stack

| Component | Technology | Version | Purpose |
|-----------|------------|---------|----------|
| **Runtime** | Node.js | 18.x+ | Server-side JavaScript runtime |
| **Framework** | Express.js | 4.18.2 | Web application framework |
| **Database** | SQLite | 3.x | Lightweight, file-based database |
| **Template Engine** | Pug | 3.0.2 | Server-side HTML templating |
| **Authentication** | Express-session + bcrypt | Latest | Secure session management |
| **Real-time** | Socket.IO | 4.7.5 | WebSocket communication |
| **File Upload** | Multer | 1.4.5 | Multipart form data handling |
| **Security** | CSRF Tokens | Custom | Cross-site request forgery protection |
| **Styling** | Tailwind CSS | 3.x | Utility-first CSS framework |
| **Icons** | Boxicons | Latest | Icon library |

### System Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Client Side   │    │   Server Side   │    │   Data Layer    │
├─────────────────┤    ├─────────────────┤    ├─────────────────┤
│ • Pug Templates │◄──►│ • Express.js    │◄──►│ • SQLite DB     │
│ • Tailwind CSS │    │ • Controllers   │    │ • Models        │
│ • JavaScript    │    │ • Middleware    │    │ • Migrations    │
│ • Socket.IO     │    │ • Routes        │    │ • Seeders       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 📁 Project Structure

```
POS-kita/
├── 📁 config/                 # Database configuration and setup
│   ├── database.js            # SQLite connection and schema
│   ├── seeder.js              # Database seeding script
│   ├── database.sqlite        # SQLite database file
│   └── sessions.sqlite        # Session storage
├── 📁 controllers/            # Business logic controllers
│   ├── adminController.js     # Admin functionality (37KB)
│   ├── authController.js      # Authentication logic
│   ├── cashierController.js   # POS and transaction handling
│   ├── managerController.js   # Inventory and reporting
│   └── landingController.js   # Public pages
├── 📁 middleware/             # Custom middleware functions
│   └── auth.js               # Authentication & authorization
├── 📁 models/                # Data models and business logic
│   ├── Transaction.js        # Transaction processing
│   ├── Product.js           # Product management
│   ├── Ingredient.js        # Inventory management
│   └── User.js              # User management
├── 📁 routes/                # Express.js route definitions
│   ├── admin.js             # Admin routes (62 endpoints)
│   ├── auth.js              # Authentication routes
│   ├── cashier.js           # Cashier/POS routes
│   ├── manager.js           # Manager routes
│   └── landing.js           # Public routes
├── 📁 views/                 # Pug template files
│   ├── 📁 admin/            # Admin interface (22 templates)
│   ├── 📁 auth/             # Authentication pages (4 templates)
│   ├── 📁 cashier/          # Cashier interface (6 templates)
│   ├── 📁 manager/          # Manager interface (11 templates)
│   ├── layout.pug           # Main layout template
│   ├── index.pug            # Landing page
│   └── error.pug            # Error page template
├── 📁 public/               # Static assets
│   ├── 📁 css/             # Stylesheets
│   ├── 📁 js/              # Client-side JavaScript
│   ├── 📁 images/          # Image assets
│   └── 📁 uploads/         # User uploaded files
├── 📁 preview/             # Application screenshots
├── app.js                  # Main application entry point
├── package.json           # Dependencies and scripts
└── README.md             # This documentation
```

## 🔐 Security Features

### Authentication & Authorization
- **Session-based Authentication**: Secure server-side sessions with SQLite storage
- **Password Security**: bcrypt hashing with salt rounds
- **Role-based Access Control**: Granular permissions for different user types
- **Session Management**: Automatic session cleanup and timeout handling

### Security Middleware
- **CSRF Protection**: Custom CSRF token implementation for all forms
- **Input Validation**: Server-side validation for all user inputs
- **File Upload Security**: Secure file handling with type validation
- **SQL Injection Prevention**: Parameterized queries throughout the application

### Data Protection
- **Secure Headers**: HTTP security headers implementation
- **Session Security**: HttpOnly cookies with SameSite protection
- **Environment Variables**: Sensitive configuration via environment variables

## 👥 User Roles & Permissions

### 🔴 Admin Role
**Complete System Access**
- ✅ User Management (Create, Edit, Delete users)
- ✅ System Configuration
- ✅ Transaction Management (View, Delete transactions)
- ✅ Product Management (Full CRUD operations)
- ✅ Inventory Management (Full control)
- ✅ Recipe Management
- ✅ Landing Page Content Management
- ✅ All Reports and Analytics
- ✅ System Logs and Monitoring

### 🟡 Manager Role
**Operations Management**
- ✅ Inventory Management (Add, Edit ingredients)
- ✅ Product Management (Create, Edit products)
- ✅ Recipe Management (Create, Edit recipes)
- ✅ Reports and Analytics
- ✅ Stock Level Monitoring
- ✅ Cost Analysis
- ❌ User Management
- ❌ System Configuration
- ❌ Transaction Deletion

### 🟢 Cashier Role
**Point of Sale Operations**
- ✅ Process Transactions
- ✅ Print Receipts
- ✅ View Transaction History (Own transactions)
- ✅ Basic Product Lookup
- ✅ Customer Management
- ❌ Inventory Management
- ❌ Product Creation/Editing
- ❌ System Reports
- ❌ User Management

## 🗄️ Database Schema

### Core Tables

#### Users Table
```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  username TEXT NOT NULL UNIQUE,
  password TEXT NOT NULL,           -- bcrypt hashed
  fullname TEXT NOT NULL,
  role TEXT CHECK (role IN ('admin', 'cashier', 'manager')),
  email TEXT UNIQUE,
  reset_token TEXT,                 -- Password reset functionality
  reset_token_expires TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Products Table
```sql
CREATE TABLE products (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL UNIQUE,
  description TEXT,
  price REAL NOT NULL,
  category_id INTEGER,
  image_path TEXT,                  -- Product images
  is_active BOOLEAN DEFAULT 1,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (category_id) REFERENCES categories(id)
);
```

#### Ingredients Table
```sql
CREATE TABLE ingredients (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL UNIQUE,
  stock_qty REAL NOT NULL DEFAULT 0,
  unit TEXT NOT NULL,
  base_unit_conversion REAL NOT NULL DEFAULT 1,
  cost_per_unit REAL NOT NULL DEFAULT 0,
  min_stock_level REAL,            -- Low stock alerts
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Transactions Table
```sql
CREATE TABLE transactions (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  transaction_number TEXT UNIQUE NOT NULL,  -- Auto-generated: TRX24010100001
  cashier_id INTEGER NOT NULL,
  customer_name TEXT,
  total_amount REAL NOT NULL,
  payment_method TEXT NOT NULL,
  payment_amount REAL NOT NULL,
  change_amount REAL NOT NULL,
  status TEXT NOT NULL DEFAULT 'completed',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (cashier_id) REFERENCES users(id)
);
```

### Relationship Tables
- **product_recipes**: Links products to ingredients with quantities
- **transaction_items**: Individual items within transactions
- **ingredient_logs**: Audit trail for inventory changes
- **categories**: Product categorization
- **landing_content**: Dynamic landing page content

## 🛠️ API Endpoints

### Authentication Routes (`/auth`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/auth/login` | Login page | Guest only |
| POST | `/auth/login` | Process login | Guest only |
| GET | `/auth/register` | Registration page | Guest only |
| POST | `/auth/register` | Process registration | Guest only |
| GET | `/auth/logout` | Logout user | Authenticated |
| GET/POST | `/auth/forgot-password` | Password reset | Guest only |
| GET/POST | `/auth/reset-password/:token` | Reset password | Guest only |
| GET/POST | `/auth/change-password` | Change password | Authenticated |

### Admin Routes (`/admin`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/admin/dashboard` | Admin dashboard | Admin only |
| GET | `/admin/users` | User management | Admin only |
| GET/POST | `/admin/users/add` | Add new user | Admin only |
| GET/POST | `/admin/users/edit/:id` | Edit user | Admin only |
| GET | `/admin/users/delete/:id` | Delete user | Admin only |
| GET | `/admin/products` | Product listing | Admin only |
| GET/POST | `/admin/products/create` | Create product | Admin only |
| GET/POST | `/admin/products/edit/:id` | Edit product | Admin only |
| GET | `/admin/products/delete/:id` | Delete product | Admin only |
| GET | `/admin/products/:id/recipe` | Product recipe | Admin only |
| POST | `/admin/products/:id/recipe/add` | Add recipe item | Admin only |
| GET | `/admin/ingredients` | Ingredient listing | Admin only |
| GET/POST | `/admin/ingredients/create` | Create ingredient | Admin only |
| GET/POST | `/admin/ingredients/edit/:id` | Edit ingredient | Admin only |
| POST | `/admin/ingredients/:id/adjust` | Adjust stock | Admin only |
| GET | `/admin/transactions` | Transaction management | Admin only |
| GET | `/admin/transactions/:id` | Transaction detail | Admin only |
| GET | `/admin/transactions/delete/:id` | Delete transaction | Admin only |
| GET | `/admin/reports` | Reports dashboard | Admin only |
| GET | `/admin/reports/sales` | Sales reports | Admin only |
| GET | `/admin/reports/inventory` | Inventory reports | Admin only |
| GET | `/admin/reports/costs` | Cost analysis | Admin only |

### Cashier Routes (`/cashier`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/cashier/dashboard` | Cashier dashboard | Cashier only |
| GET | `/cashier/pos` | Point of sale interface | Cashier only |
| POST | `/cashier/add-item` | Add item to cart | Cashier only |
| POST | `/cashier/checkout` | Process transaction | Cashier only |
| GET | `/cashier/transactions` | Transaction history | Cashier only |
| GET | `/cashier/transactions/:id` | Transaction detail | Cashier only |
| POST | `/cashier/print/:id` | Print receipt | Cashier only |

### Manager Routes (`/manager`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/manager/dashboard` | Manager dashboard | Manager only |
| GET | `/manager/inventory` | Inventory management | Manager only |
| GET | `/manager/products` | Product management | Manager only |
| GET | `/manager/reports/sales` | Sales reports | Manager only |
| GET | `/manager/reports/inventory` | Inventory reports | Manager only |

## 🔧 Installation & Setup

### Prerequisites
- **Node.js**: Version 18.x or higher
- **npm**: Version 8.x or higher
- **Git**: For version control

### Quick Start

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Environment Configuration**
   ```bash
   cp .env.example .env
   # Edit .env file with your configuration
   ```

3. **Database Setup**
   ```bash
   npm run setup
   ```
   This command will:
   - Install all dependencies
   - Create database schema
   - Seed initial data (admin user, sample products)
   - Set up required directories

4. **Start the Application**
   ```bash
   # Production mode
   npm start
   
   # Development mode (with auto-restart)
   npm run dev
   ```

6. **Access the Application**
   - Open your browser to `http://localhost:3000`
   - Default admin credentials:
     - Username: `admin`
     - Password: `admin123`

### Available Scripts

| Script | Command | Description |
|--------|---------|-------------|
| **start** | `npm start` | Start production server |
| **dev** | `npm run dev` | Start development server with nodemon |
| **setup** | `npm run setup` | Complete setup (install + seed + assets) |
| **seed** | `npm run seed` | Seed database with sample data |
| **update-assets** | `npm run update-assets` | Update static assets |

### Environment Variables

```bash
# Server Configuration
PORT=3000
NODE_ENV=production

# Database Configuration
DATABASE_PATH=./config/database.sqlite

# Session Configuration
SESSION_SECRET=your-secret-key-here

# File Upload Configuration
UPLOAD_PATH=./public/uploads
MAX_FILE_SIZE=5242880  # 5MB

# Printer Configuration (Optional)
PRINTER_IP=192.168.1.100
PRINTER_PORT=9100
```

## 🖥️ User Interface

### Design System
- **Framework**: Tailwind CSS 3.x
- **Icons**: Boxicons
- **Animations**: AOS (Animate On Scroll)
- **Theme**: Dark/Light mode support
- **Responsive**: Mobile-first design approach

### Key UI Components
- **Dashboard Cards**: Real-time statistics and metrics
- **Data Tables**: Sortable, filterable, paginated tables
- **Forms**: CSRF-protected forms with validation
- **Modals**: Dynamic modal dialogs
- **Notifications**: Toast notifications for user feedback
- **Charts**: Sales and inventory visualization

### Accessibility Features
- **Keyboard Navigation**: Full keyboard accessibility
- **Screen Reader Support**: ARIA labels and descriptions
- **Color Contrast**: WCAG 2.1 AA compliant
- **Focus Management**: Clear focus indicators

## 📊 Reporting & Analytics

### Sales Reports
- **Daily Sales**: Transaction count, total revenue, average order value
- **Monthly Sales**: Month-over-month growth analysis
- **Product Performance**: Best-selling products and revenue contribution
- **Cashier Performance**: Individual cashier statistics
- **Payment Methods**: Cash vs. non-cash transaction analysis

### Inventory Reports
- **Stock Levels**: Current inventory status
- **Low Stock Alerts**: Items below minimum threshold
- **Usage Patterns**: Ingredient consumption analysis
- **Cost Analysis**: Product profitability and margin analysis
- **Waste Tracking**: Expired or damaged inventory

### Business Intelligence
- **Revenue Trends**: Historical sales performance
- **Customer Analytics**: Customer behavior patterns
- **Seasonal Analysis**: Peak hours and seasonal trends
- **Profit Margins**: Product and category profitability

## 🔌 Integration Capabilities
### Real-time Features
- **Socket.IO Integration**: Live updates across all connected clients
- **Inventory Sync**: Real-time stock level updates
- **Transaction Notifications**: Live transaction alerts
- **Multi-user Support**: Concurrent user session management

### External API Support
- **RESTful Architecture**: Clean API endpoints for integration
- **JSON Responses**: Standardized API response format
- **Authentication**: Token-based API authentication
- **Rate Limiting**: API request throttling

## 🧪 Testing & Quality Assurance

### Code Quality
- **ESLint**: JavaScript linting and code standards
- **Prettier**: Code formatting consistency
- **Security Auditing**: npm audit for vulnerability scanning
- **Performance Monitoring**: Application performance tracking

### Testing Strategy
- **Unit Tests**: Individual component testing
- **Integration Tests**: API endpoint testing
- **End-to-End Tests**: Complete user workflow testing
- **Load Testing**: Performance under high traffic

## 🚀 Deployment

### Production Deployment

1. **Server Requirements**
   - **OS**: Linux (Ubuntu 20.04+ recommended)
   - **RAM**: Minimum 1GB, Recommended 2GB+
   - **Storage**: Minimum 1GB free space
   - **Node.js**: Version 18.x LTS

2. **Deployment Steps**
   ```bash
   
   # Set environment variables
   export NODE_ENV=production
   export PORT=3000
   
   # Run setup
   npm run setup
   
   # Start application
   npm start
   ```

3. **Process Management**
   ```bash
   # Using PM2 (recommended)
   npm install -g pm2
   pm2 start app.js --name "pos-kita"
   pm2 startup
   pm2 save
   ```

4. **Reverse Proxy (Nginx)**
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;
       
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

### Docker Deployment

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --production

COPY . .

RUN npm run setup

EXPOSE 3000

CMD ["npm", "start"]
```

## 🔧 Maintenance & Monitoring

### Database Maintenance
- **Backup Strategy**: Regular SQLite database backups
- **Vacuum Operations**: Database optimization
- **Log Rotation**: Transaction and error log management
- **Data Archival**: Historical data management

### Performance Monitoring
- **Application Metrics**: Response times, error rates
- **Database Performance**: Query optimization
- **Memory Usage**: Node.js heap monitoring
- **Disk Space**: Storage utilization tracking

### Security Monitoring
- **Access Logs**: User authentication tracking
- **Failed Login Attempts**: Brute force detection
- **Session Monitoring**: Unusual session activity
- **Vulnerability Scanning**: Regular security audits

## 🤝 Contributing

### Development Guidelines
1. **Code Style**: Follow ESLint configuration
2. **Commit Messages**: Use conventional commit format
3. **Branch Naming**: `feature/`, `bugfix/`, `hotfix/` prefixes
4. **Pull Requests**: Include tests and documentation

### Development Setup
```bash
# Install development dependencies
npm install

# Run in development mode
npm run dev

# Run tests
npm test

# Check code quality
npm run lint
```

---

**Built with ❤️ for modern businesses**

*POS-kita - Empowering businesses with intelligent point-of-sale solutions*
