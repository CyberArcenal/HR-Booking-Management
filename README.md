# HR Booking Management System

[![Electron](https://img.shields.io/badge/Electron-191970?style=for-the-badge&logo=Electron&logoColor=white)](https://www.electronjs.org/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)

A professional desktop application for managing HR bookings, appointments, employee scheduling, and resource management. Built with Electron, React, and SQLite for cross-platform desktop deployment.

## ✨ Features

### 📅 Appointment Management
- **Smart Calendar** - Visual calendar with drag-and-drop scheduling
- **Recurring Appointments** - Set up weekly, monthly, or custom recurring bookings
- **Resource Allocation** - Book rooms, equipment, and personnel
- **Conflict Detection** - Automatic conflict checking for overlapping bookings

### 👥 Employee Management
- **Role-based Access** - Administrator, Manager, Employee, and Viewer roles
- **Availability Blocks** - Set working hours and unavailable periods
- **Leave Management** - Track vacation, sick leave, and time-off requests
- **Performance Reports** - Generate and review employee performance metrics

### 🔔 Smart Notifications
- **Email & SMS Reminders** - Automated reminders for upcoming appointments
- **Cancellation Alerts** - Notify stakeholders of booking changes
- **Real-time Updates** - Live updates for calendar changes
- **Audit Trail** - Complete history of all system activities

### 📊 Reporting & Analytics
- **Dashboard** - Real-time overview of bookings, utilization, and trends
- **Export Options** - Export data to PDF, Excel, and CSV formats
- **Custom Reports** - Generate reports by department, date range, or resource
- **Data Visualization** - Charts and graphs for quick insights

### 🔧 Advanced Features
- **Calendar Synchronization** - Sync with external calendars (Google, Outlook)
- **Auto-cancellation** - Automated cleanup of no-show appointments
- **Backup & Recovery** - Automated database backups and restoration
- **Migration Manager** - Safe database schema updates without data loss

## 📸 Screenshots
Here are sample displays of the system (replace the links with your own):

![Screenshot 3](https://github.com/CyberArcenal/HR-Booking-Management/blob/main/images/img3.png?raw=true)
![Screenshot 2](https://github.com/CyberArcenal/HR-Booking-Management/blob/main/images/img2.png?raw=true)
![Screenshot 1](https://github.com/CyberArcenal/HR-Booking-Management/blob/main/images/img1.png?raw=true)

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ and npm
- Git
- For development: Visual Studio Code recommended

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/CyberArcenal/HR-Booking-Management.git
   cd HR-Booking-Management
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment**
   - Copy `.env.example` to `.env`
   - Update configuration as needed (optional for basic setup)

4. **Run in development mode**
   ```bash
   npm run dev
   ```

5. **Build for production**
   ```bash
   npm run build
   ```

## 📁 Project Structure

```
hrbooking-management/
├── src/
│   ├── main/                  # Electron main process
│   │   ├── index.js          # Main entry point
│   │   ├── preload.js        # Preload script
│   │   └── reg.handler.js    # IPC handlers
│   ├── renderer/             # React frontend
│   │   ├── pages/            # Application pages
│   │   ├── components/       # Reusable components
│   │   ├── api/              # API communication layer
│   │   └── lib/              # Utilities and stores
│   ├── entities/             # TypeORM entities
│   ├── migrations/           # Database migrations
│   ├── seeders/              # Database seed data
│   ├── config/               # Configuration files
│   ├── scheduler/            # Background job schedulers
│   └── utils/                # Utility functions
├── build/                    # Build assets (icons, etc.)
├── dist/                     # Production build output
└── release/                  # Installer packages
```

## 🛠️ Development

### Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build for production |
| `npm run electron:dev` | Run Electron in development mode |
| `npm run migration:generate` | Generate new database migration |
| `npm run migration:run` | Run pending migrations |
| `npm run seed` | Seed database with sample data |
| `npm run lint` | Run ESLint for code quality |

### Database Management

The application uses SQLite with TypeORM. Key commands:

```bash
# Generate migration after entity changes
npm run migration:generate

# Apply migrations
npm run migration:run

# Revert last migration
npm run migration:revert

# Seed database with default data
npm run seed
```

### Adding New Features

1. **New Entity/Table:**
   - Create entity in `src/entities/`
   - Generate migration: `npm run migration:generate`
   - Run migration: `npm run migration:run`

2. **New API Endpoint:**
   - Add handler in `src/main/reg.handler.js`
   - Create API client in `src/renderer/api/`
   - Add validation as needed

3. **New Page:**
   - Create component in `src/renderer/pages/`
   - Add route in App.tsx
   - Update navigation if needed


### Database Configuration

The application automatically handles database paths:
- **Development**: `easybook_hr.db` in project root
- **Production**: `userData/data/easybook_hr.db` in app directory

## 📦 Build & Distribution

### Building for Windows

```bash
npm run build
```

The installer will be available in `release/` directory.

### Build Configuration

Key settings in `package.json`:

```json
{
  "build": {
    "appId": "com.CyberArcenal.hrbooking.app",
    "productName": "HR Booking Management",
    "directories": {
      "output": "release"
    },
    "win": {
      "target": "nsis",
      "icon": "build/icon.ico"
    },
    "mac": {
      "target": "dmg",
      "icon": "build/icon.icns"
    }
  }
}
```

## 🔐 Security Features

- **Password Hashing**: Bcrypt for secure password storage
- **JWT Tokens**: Stateless authentication with refresh tokens
- **Role-based Permissions**: Granular access control
- **Input Validation**: Protection against SQL injection and XSS
- **Audit Trail**: Complete logging of all user actions
- **Data Encryption**: Sensitive data encryption at rest

## 📈 Performance Optimizations

- **SQLite WAL Mode**: Write-Ahead Logging for better concurrency
- **React Lazy Loading**: Code splitting for faster initial load
- **Image Optimization**: Compressed and optimized assets
- **Database Indexing**: Optimized queries with proper indexing
- **Memory Management**: Efficient garbage collection in Electron

## 🐛 Troubleshooting

### Common Issues

1. **"Database not found" error**
   - Run: `npm run migration:run`
   - Or delete database file and restart

2. **"Cannot open database" error**
   - Check file permissions
   - Ensure disk space is available

3. **Build failures**
   - Clear node_modules: `rm -rf node_modules`
   - Reinstall: `npm install`
   - Clear cache: `npm cache clean --force`

4. **App crashes on startup**
   - Check logs in: `%APPDATA%\HR Booking Management\logs\`
   - Reset settings if needed

### Logs Location

- **Windows**: `%APPDATA%\HR Booking Management\logs\`
- **macOS**: `~/Library/Logs/HR Booking Management/`
- **Linux**: `~/.config/HR Booking Management/logs/`

## 📞 Support

For support, bug reports, or feature requests:
- Create an issue on GitHub
- Email: support@cyberarcenal.com
- Documentation: [View Wiki](https://github.com/CyberArcenal/hrbooking-management/wiki)

## 🏆 Acknowledgements

- [Electron](https://www.electronjs.org/) - Cross-platform desktop apps
- [React](https://reactjs.org/) - Frontend library
- [TypeORM](https://typeorm.io/) - Database ORM
- [SQLite](https://sqlite.org/) - Embedded database
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- [Lucide Icons](https://lucide.dev/) - Beautiful icons

---

<div align="center">
  Made with ❤️ by <a href="https://github.com/CyberArcenal">CyberArcenal</a>
</div>