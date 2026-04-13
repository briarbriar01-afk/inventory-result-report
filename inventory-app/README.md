# Inventory Management System

A modern web-based inventory management application built with Flask, perfect for tracking organizational assets like computers, vehicles, warehouses, and buildings.

## Features

✅ **User Authentication** - Secure login and registration
✅ **Dashboard** - Real-time statistics and charts
✅ **Inventory Management** - Create, read, update, delete items
✅ **Categories** - Organize items by type
✅ **Reports & Analytics** - Visual insights with Chart.js
✅ **Export to Excel** - Generate reports in Excel format
✅ **Audit Logging** - Track all changes
✅ **Responsive Design** - Works on desktop and mobile

## Quick Start

### Prerequisites
- Python 3.8+
- pip

### Installation

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Initialize the app with demo data
python init_app.py

# 3. Run the app
python run.py
```

The app will start at `http://localhost:5000`

### Default Credentials

- **Admin**: `admin` / `admin123`
- **User**: `demo` / `demo123`

## Project Structure

```
inventory-app/
├── app/
│   ├── __init__.py          # Flask app factory
│   ├── models.py            # Database models
│   ├── routes.py            # All routes (auth, main, api)
│   ├── static/
│   │   ├── css/             # Stylesheets
│   │   └── js/              # JavaScript
│   └── templates/
│       ├── base.html        # Base template
│       ├── login.html       # Login page
│       ├── register.html    # Registration page
│       ├── dashboard.html   # Main dashboard
│       ├── inventory.html   # Inventory management
│       └── reports.html     # Reports page
├── run.py                   # Application entry point
├── init_app.py              # Database initialization
└── requirements.txt         # Python dependencies
```

## Database

The app uses SQLite. Database file: `inventory.db` (created on first run)

### Models

- **User** - System users with authentication
- **Category** - Asset categories (Computers, Vehicles, etc.)
- **InventoryItem** - Individual inventory items
- **AuditLog** - Change tracking

## API Endpoints

All API endpoints require authentication:

### Items
- `GET /api/items` - Get all items
- `POST /api/items` - Create new item
- `PUT /api/items/<id>` - Update item
- `DELETE /api/items/<id>` - Delete item

### Categories
- `GET /api/categories` - Get all categories

### Reports
- `GET /api/reports/data` - Get report data for charts
- `GET /api/export/excel` - Export to Excel

## Usage

1. **Login** with the provided credentials
2. **View Dashboard** to see summary statistics and charts
3. **Manage Inventory** - Add, edit, or delete items
4. **View Reports** - Analyze data with visual charts
5. **Export Data** - Download inventory as Excel

## Data Import

The app automatically imports data from the Excel file if available. To manually import:

```python
python init_app.py
```

## Development

### Debug Mode

The app runs in debug mode by default. Disable in production by setting `debug=False` in `run.py`.

### Database Reset

To reset the database:

```bash
rm inventory.db
python init_app.py
```

## Future Enhancements

- [ ] Multi-language support
- [ ] Advanced filtering and search
- [ ] CSV import/export
- [ ] Barcode scanning
- [ ] Email notifications
- [ ] User roles and permissions
- [ ] Data backup and restore
- [ ] API documentation (Swagger)

## License

MIT
