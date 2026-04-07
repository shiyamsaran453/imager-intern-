========================================================================
SMART CANTEEN DEMAND PREDICTION SYSTEM
========================================================================

TECHNOLOGY STACK
================
Backend:        Python 3.8+ with Flask web framework
Database:       SQLite (canteen.db)
Frontend:       HTML5, CSS3, JavaScript (Vanilla)
Server:         Flask development server
Environment:    Python Virtual Environment

KEY FEATURES
============
1. Rule-Based AI Prediction Engine
   - Analyzes day type (weekday, weekend, exam, holiday)
   - Considers time slot (breakfast, lunch, dinner)
   - Factors in expected student count
   - Provides demand level and food preparation suggestions

2. Data Entry Form
   - Easy-to-use interface for canteen staff
   - Date, day type, time slot, and student count inputs
   - Real-time client-side validation
   - Server-side validation for data integrity

3. Prediction Results Display
   - Clear visual representation of demand levels
   - Color-coded indicators (High=Red, Medium=Orange, Low=Green)
   - Confidence score for each prediction
   - Food preparation recommendations

4. History & Analytics
   - View past 10 predictions with details
   - Demand level distribution summary
   - Dashboard with key metrics
   - Quick access to recent predictions

5. Database Management
   - SQLite database with proper schema
   - Historical data storage
   - Relationship between entries and predictions

PROJECT STRUCTURE
=================
SmartCanteen/
├── app.py                  # Main Flask application
├── database.py             # Database initialization and management
├── predict.py              # Rule-based prediction engine
├── canteen.db              # SQLite database (auto-generated)
├── templates/              # HTML templates
│   ├── base.html          # Base template with navbar and footer
│   ├── entry.html         # Data entry form page
│   ├── result.html        # Prediction result page
│   ├── history.html       # Past predictions history page
│   ├── dashboard.html     # System dashboard page
│   ├── 404.html           # 404 error page
│   └── 500.html           # 500 error page
├── static/                 # Static files
│   ├── style.css          # CSS styling
│   └── script.js          # JavaScript functionality
└── README.txt             # This file

INSTALLATION & SETUP
====================
1. Navigate to the SmartCanteen directory:
   cd "c:\Users\shiya\OneDrive\Desktop\imagger intern\SmartCanteen"

2. The virtual environment should already be configured at:
   c:\Users\shiya\OneDrive\Desktop\imagger intern\.venv

3. Install required packages (if not already installed):
   pip install Flask

HOW TO RUN
==========
1. Open terminal/PowerShell and navigate to the project:
   cd "c:\Users\shiya\OneDrive\Desktop\imagger intern\SmartCanteen"

On Windows REQUIREMENT INSTALLATION Command:
Open PowerShell or Command Prompt
Navigate to the SmartCanteen folder
Run: .\setup.bat

2. Run the Flask application:
   python app.py

3. Open your web browser and visit:
   http://127.0.0.1:5000

4. The application will display the Dashboard page

USAGE INSTRUCTIONS
==================
For Canteen Staff:

1. Dashboard (Home Page)
   - View total number of entries
   - See demand level distribution
   - Check most recent prediction
   - Quick access to other pages

2. New Entry Page
   - Select date for prediction
   - Choose day type (Weekday, Weekend, Exam, Holiday)
   - Select time slot (Breakfast, Lunch, Dinner)
   - Enter expected number of students
   - Click "Get Prediction"

3. Result Page
   - View predicted demand level
   - See preparation suggestion
   - View confidence score
   - Option to add another entry

4. History Page
   - View past 10 predictions
   - See all prediction details
   - Understand demand patterns
   - Export data if needed

PREDICTION RULES
================
The system uses the following rules to predict demand:

HIGH DEMAND (📈):
- Exam day + Lunch → Confidence: 95%
- Weekday + Lunch with 300+ students → Confidence: 90%
- Weekend + Lunch with 200+ students → Confidence: 80%

MEDIUM DEMAND (📊):
- Exam day + Breakfast/Dinner → Confidence: 85%
- Weekday + Breakfast/Dinner → Confidence: 75%
- Holiday + Lunch → Confidence: 70%

LOW DEMAND (📉):
- Weekend + Breakfast/Dinner → Confidence: 70%
- Holiday + Breakfast/Dinner → Confidence: 60%

DATABASE SCHEMA
===============
Table: canteen_data
- id: INTEGER PRIMARY KEY (auto-increment)
- date: TEXT (YYYY-MM-DD format)
- day_type: TEXT (weekday, weekend, exam, holiday)
- time_slot: TEXT (breakfast, lunch, dinner)
- student_count: INTEGER (expected students)
- created_at: TIMESTAMP (auto-generated)

Table: predictions
- id: INTEGER PRIMARY KEY (auto-increment)
- canteen_data_id: INTEGER FOREIGN KEY
- demand_level: TEXT (High, Medium, Low)
- food_suggestion: TEXT (preparation recommendation)
- confidence_score: REAL (0-100)
- created_at: TIMESTAMP (auto-generated)

API ENDPOINTS
=============
For advanced usage:

GET /                          → Dashboard
GET /entry                     → Data entry form
POST /entry                    → Submit entry data
GET /result                    → Show prediction result
GET /history                   → View past predictions
GET /dashboard                 → Dashboard (alias)
POST /api/predict              → JSON prediction endpoint
GET /api/history               → JSON history endpoint

VALIDATION
==========
Client-Side Validation:
- All form fields required
- Date must be valid (YYYY-MM-DD)
- Student count: 1-5000 range
- Day type and time slot from predefined options

Server-Side Validation:
- Confirms all client-side rules
- Validates data before database insertion
- Prevents invalid entries
- Returns error messages

FILE DESCRIPTIONS
=================
app.py
- Main Flask application
- All route handlers (/entry, /predict, /history, /dashboard)
- Form validation and prediction logic
- Database queries
- Error handlers

database.py
- Database initialization
- Table creation (canteen_data, predictions)
- Connection management
- Helper functions

predict.py
- Rule-based prediction engine
- DemandPredictor class
- Prediction logic and rules
- Confidence score calculation

test_system.py
- Test suite for the system
- Sample data generation
- Database verification
- Prediction rule testing

HTML Templates (templates/)
- base.html: Navigation and footer
- entry.html: Data entry form
- result.html: Prediction results
- history.html: Past predictions
- dashboard.html: System dashboard
- 404.html: Page not found
- 500.html: Server error

CSS (static/style.css)
- Complete styling for all pages
- Responsive design
- Dark/light themes
- Animation and transitions

JavaScript (static/script.js)
- Form validation
- User interactions
- DOM manipulation
- Utility functions

DEPLOYMENT
==========
For production deployment:
1. Set debug=False in app.py
2. Use production WSGI server (Gunicorn)
3. Add SSL/TLS certificates
4. Configure proper database backups
5. Set up logging and monitoring
6. Use environment variables for config




