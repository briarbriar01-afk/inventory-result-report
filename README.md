# Inventory Result Report System

A professional web-based inventory audit reporting system for PDK (Kurdish Democratic Party). This application enables staff to conduct and submit detailed inventory audits through an intuitive A4-formatted form, with centralized superadmin dashboard for monitoring and reviewing all submitted reports.

## Features

✅ **Professional Report Form**
- Beautiful A4-sized single-page form with Kurdish (Sorani) interface
- Auto-calculated discrepancies for each asset category
- Real-time field validation and calculations
- Save as draft or submit to superadmin
- Print-optimized layout

✅ **Four Asset Categories**
- 🖥️ Computers (کۆمپیوتەر)
- 🚗 Vehicles (مۆبیلیات)
- 🏠 Warehouses (بارەگا)
- 🏢 Buildings (بینا)

✅ **Interactive Charts**
- Beautiful animated bar charts showing expected vs. counted items
- Charts for each asset category
- Color-coded data visualization
- System count vs. actual count comparison

✅ **Superadmin Dashboard**
- View all submitted reports in clean table format
- Quick statistics showing total discrepancies
- Expandable report details with all information
- Print individual reports
- Color-coded discrepancy indicators

✅ **Role-Based Access Control**
- SuperAdmin: Access dashboard, view all reports
- Admin: Can view reports
- Employee: Create and submit reports

## Technology Stack

- **Backend**: Flask 3.1.3 (Python)
- **Frontend**: Bootstrap 5.3, Chart.js 4.4
- **Data Storage**: JSON files (no database required)
- **Authentication**: Flask-Login + Werkzeug
- **Language**: 100% Kurdish (Sorani) interface

## Installation

### Requirements
- Python 3.7+
- Unix/Windows shell environment

### Setup

```bash
# Clone the repository
git clone https://github.com/briarbriar01-afk/inventory-result-report.git
cd inventory-result-report/inventory-app

# Install dependencies
pip install -r requirements.txt

# Initialize the application
python init.py

# Start the development server
python app.py
```

The app will be available at: `http://localhost:5000`

## Demo Users

| Role | Username | Password |
|---|---|---|
| SuperAdmin | superadmin | superadmin123 |
| Admin | admin | admin123 |
| Employee | employee | employee123 |

## Usage

### For Staff (Creating Reports)

1. Login with employee credentials
2. Click "جەردی نوێ درست بکە" (Create New Report)
3. Fill in the form:
   - Organization info
   - Responsible people
   - Asset counts (system vs. counted)
4. Click "💾 پاشکۆکی" to save draft
5. Click "📤 ناردن بۆ سوپەر ئاداین" to submit to superadmin

### For Superadmin (Reviewing Reports)

1. Login with superadmin credentials
2. Go to dashboard
3. View all submitted reports in table
4. Click "🔍 نیشاندان" to view full details
5. Click "🖨️ چاپ" to print report

## Form Layout

The form includes:
- **Header**: Organization logo and title
- **Section 1**: General information (org name, date, auditor)
- **Section 2**: Responsible people (3 officers with IDs)
- **Section 3**: Summary totals
- **Section 4**: Category-wise audit results with charts
- **Section 5**: Signature lines

## Color Scheme

- Primary Blue: #2C5AA0
- Light Blue: #5B9FD9
- Dark Blue: #1a3f6e
- Red (discrepancies): #d32f2f
- Green (positive): #2E7D32

## File Structure

```
inventory-app/
├── app.py                 # Main Flask application
├── init.py               # Data initialization
├── requirements.txt      # Python dependencies
├── data/                 # JSON data files
│   ├── users.json       # User accounts
│   ├── categories.json  # Asset categories
│   ├── items.json       # Inventory items
│   └── reports.json     # Submitted reports
├── templates/           # HTML templates
│   ├── base.html       # Base template
│   ├── new_report_form.html  # Staff report form
│   ├── superadmin_dashboard.html
│   ├── login.html
│   └── ...
└── static/             # Static assets
    └── images/         # Logos and images
```

## Key Features Explained

### Auto-Calculated Discrepancies
- System automatically calculates: `Counted - System Count = Discrepancy`
- Color coding: Red for negative, Green for positive, Blue for zero
- Real-time updates as staff enters data

### Beautiful Charts
- Interactive bar charts for each category
- Animated transitions
- Tooltips showing exact values
- Responsive design

### One-Page A4 Format
- Fixed 210mm × 297mm container
- Optimized spacing for all content on single page
- Print-ready styling

## Development

### Modifying Colors
All colors use blue (#2C5AA0, #5B9FD9) instead of green for a professional look.

### Adding New Categories
1. Edit `init.py` categories
2. Add corresponding HTML form sections
3. Update JavaScript calculations
4. Add to charts

### Styling Charts
Charts are configured in `new_report_form.html` using Chart.js:
```javascript
canvas.chart = new Chart(ctx, {
    type: 'bar',
    data: { ... },
    options: { ... }
});
```

## Troubleshooting

**Reports not showing in superadmin dashboard:**
- Ensure you're logged in as superadmin
- Reports must have status "submitted" (not draft)
- Check `data/reports.json` file exists

**Charts not displaying:**
- Click "📊 نیشاندانی چارت" button
- Ensure Chart.js is loaded from CDN
- Check browser console for errors

**Form won't save:**
- Check network connection
- Verify Flask server is running
- Check browser console for JavaScript errors

## License

This project is developed for PDK (Kurdish Democratic Party).

## Author

Developed for inventory audit management and reporting.

---

**Version**: 1.0  
**Language**: Kurdish (Sorani) - 100%  
**Status**: Production Ready ✅
