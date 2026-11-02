# Datix – Cloud AI-Powered Data Analytics Studio

## 1. Project Description

Datix is a browser-based data analytics platform designed to simplify data cleaning, visualization, statistical analysis, and AI-powered data exploration.

Users can upload datasets in CSV, Excel, JSON, Parquet, and TSV formats, clean and transform their data, explore patterns through interactive visualizations, perform statistical analysis, and ask natural-language questions using an integrated AI assistant.

The AI assistant is powered by **Llama 3 through the Groq Cloud API**, eliminating the need to install local AI models or use a dedicated GPU.

## 2. Key Features

### 2.1 Data Cleaning and Preprocessing

- Drag-and-drop dataset upload.
- Supports CSV, Excel (`.xls`, `.xlsx`), JSON, Parquet, and TSV.
- Dataset overview:
  - Total rows and columns.
  - Missing cells.
  - Duplicate rows.
  - Total cells.
  - Memory usage.
- Column-level diagnostics:
  - Data types.
  - Missing-value percentages.
  - Unique values.
  - Detected data issues.
- Missing-value heatmap.
- Data-type breakdown.

**Cleaning Operations**

- Standardize and fix column names.
- Remove duplicate rows and columns.
- Remove empty rows.
- Remove constant columns.
- Remove columns with excessive missing values.
- Strip unnecessary whitespace.
- Standardize text case.
- Remove HTML tags and special characters.
- Convert columns to numeric values.
- Remove currency and percentage symbols.
- Parse and format dates.
- Convert Yes/No and True/False values into Boolean values.

**Missing Value Handling**

- Mean imputation.
- Median imputation.
- Zero replacement.
- Forward fill.
- Backward fill.
- Mode imputation.
- Unknown-value replacement.

**Outlier Handling**

- IQR-based capping.
- Z-score-based removal.
- Numeric normalization.

Additional capabilities include before-and-after comparisons, transformation logs, advanced filtering, and cleaned dataset exports.

### 2.2 Data Visualization

Datix provides multiple visualization options for exploring datasets.

**Supported Chart Types**

- Bar Chart.
- Horizontal Bar Chart.
- Grouped Bar Chart.
- Stacked Bar Chart.
- 100% Stacked Bar Chart.
- Line Chart.
- Area Chart.
- Scatter Plot.
- Pie Chart.
- Donut Chart.
- Box Plot.

**Advanced Visualization**

- Chart Guide for selecting appropriate chart types.
- Distribution Explorer with histograms, KDE, violin plots, box plots, and summary statistics.
- Correlation analysis using Pearson, Spearman, and Kendall methods.
- Correlation heatmaps and strongest correlation pairs.
- Multi-variable scatter plots with X-axis, Y-axis, hue, bubble size, and trend lines.
- Time-series analysis with automatic date-column detection and rolling averages.

### 2.3 Statistical Analysis

Datix includes a dedicated analysis section for exploring dataset characteristics and identifying meaningful patterns.

**Statistical Overview**

- Numeric statistics.
- Categorical statistics.
- Data profiling.

**Group-by Analysis**

Supported aggregations:

- Mean.
- Sum.
- Count.
- Median.
- Standard deviation.
- Minimum.
- Maximum.

Additional features include group comparison heatmaps.

**Outlier Detection**

- IQR method.
- Z-score method.
- Modified Z-score method.

**Additional Analysis Tools**

- Data profiling table.
- Value-count explorer.
- KPI dashboard.
- Optional KPI filters.

### 2.4 AI Data Assistant

Datix includes an AI-powered data assistant using **Llama 3 through the Groq Cloud API**.

Users can ask questions about their uploaded datasets using natural language.

Example questions:

- Summarize the sales trends.
- Which columns have the most missing values?
- Which category has the highest sales?
- What are the most important patterns in this dataset?

The AI assistant receives contextual information about:

- Dataset dimensions.
- Column names.
- Column data types.
- Sample data.

**Quick Actions**

- Auto Insights.
- Statistical Summary.
- Data Quality Report.
- Analysis Suggestions.
- Generate Pandas Code.

**Additional AI Features**

- Streaming responses.
- Typing indicator.
- Input locking while generating.
- Rule-based static insights.
- Export chat transcripts as `.txt` files.

No local AI model installation or GPU is required.

### 2.5 Advanced Filtering

Datix provides advanced filtering options for exploring specific portions of a dataset.

**Numeric Filters**

- Equal to (`=`).
- Greater than (`>`).
- Less than (`<`).
- Greater than or equal to (`>=`).
- Less than or equal to (`<=`).

**Text Filters**

- Equals.
- Contains.

Filtered datasets can be exported in supported formats.

### 2.6 Dataset Export

Users can export processed datasets in:

- CSV.
- Excel.
- JSON.
- Parquet.

### 2.7 Responsive Interface

Datix is designed to work across desktop, tablet, and mobile devices.

Interface features include:

- Responsive layouts.
- Collapsible sidebar.
- Mobile hamburger menu.
- Fluid chart and metric layouts.
- Responsive breakpoints.

## 3. Technology Stack

| Layer | Technology |
|---|---|
| Backend | Python, Flask, Gunicorn |
| Data Processing | pandas, NumPy, SciPy |
| Visualization | Matplotlib, Seaborn |
| AI Integration | Groq Cloud API, Llama 3 |
| Frontend | HTML, CSS, JavaScript |
| Deployment | Render, Railway, and other Python-compatible platforms |

The frontend uses Vanilla HTML, CSS, and JavaScript. No frontend build process is required.

## 4. System Architecture

Datix follows a Flask-based backend architecture with a static frontend.

**Frontend**

- HTML provides the application structure.
- CSS handles styling and responsive layouts.
- JavaScript manages user interactions, API communication, and dynamic updates.

**Backend**

- Flask handles application routing and REST API requests.
- pandas and NumPy process and transform datasets.
- SciPy supports statistical operations.
- Matplotlib and Seaborn generate visualizations.
- The Groq API connects the application to the Llama 3 model.

**AI Processing**

The backend sends relevant dataset context and user questions to the Groq Cloud API. The AI-generated response is returned to the frontend for display.

**Data Storage**

Uploaded datasets are maintained in server memory per browser session. The application does not persist uploaded datasets to a database or write them to disk during normal processing. Data may be lost when the server restarts or the session is cleared.

## 5. Installation and Setup

### Prerequisites

Make sure the following are installed:

- Python 3.10 or later.
- pip.
- Git.
- A Groq API key.

Get a Groq API key from:

https://console.groq.com/keys

### Step 1: Clone the Repository

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

### Step 2: Create a Virtual Environment

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux**

```bash
python -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

Copy the example environment file:

```bash
cp .env.example .env
```

On Windows, create the `.env` file manually if necessary.

Add your Groq API key:

```env
GROQ_API_KEY=gsk_your_real_key_here
```

Optional configuration:

```env
GROQ_MODEL=llama-3.3-70b-versatile
FLASK_DEBUG=true
```

Never commit your `.env` file or expose API keys in your source code.

### Step 5: Run the Application

```bash
python app.py
```

Open the application in your browser:

```text
http://127.0.0.1:5000
```

## 6. Environment Variables

| Variable | Description | Required |
|---|---|---|
| `GROQ_API_KEY` | API key used to access Groq Cloud | Yes |
| `GROQ_MODEL` | Groq model identifier | No |
| `SECRET_KEY` | Flask session security key | Yes for production |
| `FLASK_DEBUG` | Enables Flask debug mode | No |
| `ALLOWED_ORIGINS` | Allowed frontend origins for CORS | Required for split deployment |
| `MAX_UPLOAD_MB` | Maximum upload size in MB; defaults to 50 MB | No |

Keep all sensitive configuration in environment variables.

## 7. API Endpoints

All API endpoints are prefixed with `/api`.

| Endpoint | Method | Description |
|---|---|---|
| `/api/upload` | POST | Upload and parse a dataset |
| `/api/clean` | POST | Execute the data-cleaning pipeline |
| `/api/filter` | POST / DELETE | Apply or clear advanced filters |
| `/api/download` | GET | Export the active dataset |
| `/api/chart/basic` | GET | Generate basic, grouped, and stacked charts |
| `/api/chart/guide` | GET | Retrieve the chart-type guide |
| `/api/analysis/*` | GET | Perform statistical analysis, outlier detection, profiling, and KPI operations |
| `/api/chat` | GET / POST / DELETE | Manage AI conversations about the dataset |
| `/api/chat/quick-action` | POST | Execute predefined AI analysis actions |
| `/api/chat/status` | GET | Check Groq configuration and availability |

## 8. Project Structure

```text
datix/
│
├── app.py                  # Flask application and REST API routes
├── cleaning.py             # Data cleaning and preprocessing pipeline
├── chart_utils.py          # Chart generation utilities
├── analysis_utils.py       # Statistical analysis helpers
├── chat_service.py         # Groq and Llama 3 integration
│
├── requirements.txt        # Python dependencies
├── Procfile                # Gunicorn start command
├── render.yaml             # Render deployment configuration
├── .env.example            # Environment variable template
├── .gitignore              # Git ignore rules
│
├── templates/
│   └── index.html          # Main application page
│
├── static/
│   ├── css/
│   │   └── style.css       # Application styling
│   │
│   └── js/
│       └── app.js          # Frontend application logic
│
└── frontend/               # Static frontend for Vercel deployment
    ├── index.html
    ├── vercel.json
    └── static/
        ├── css/
        │   └── style.css
        └── js/
            └── app.js
```

## 9. Deployment

Datix can be deployed as a single Flask application or as two separate services.

### Recommended Deployment

- Backend: Render.
- Frontend: Vercel.
- AI service: Groq Cloud API.

### Backend Deployment on Render

1. Push the repository to GitHub.
2. Open Render and select **New → Blueprint**.
3. Connect the GitHub repository.
4. Allow Render to detect the root-level `render.yaml`.
5. Configure the required environment variables:
   - `GROQ_API_KEY`.
   - `ALLOWED_ORIGINS`.
   - `SECRET_KEY` (automatically generated by the supplied blueprint, if configured).
6. Deploy the backend.
7. Copy the generated backend URL.

Example:

```text
https://datix-backend.onrender.com
```

### Frontend Deployment on Vercel

1. Open Vercel and create a new project.
2. Import the same GitHub repository.
3. Set the root directory to `frontend`.
4. Select **Other** as the framework preset.
5. Configure the backend URL in `frontend/index.html`:

```html
<script>
  window.API_BASE_URL = "https://datix-backend.onrender.com";
</script>
```

6. Replace the example URL with your actual Render backend URL.
7. Deploy the frontend.

### Configure CORS

After deploying the frontend:

1. Copy the Vercel deployment URL.
2. Open the Render backend environment settings.
3. Set `ALLOWED_ORIGINS` to the frontend URL.
4. Redeploy or restart the backend.

The frontend communicates with the backend through `/api/...` requests. Session cookies are sent with cross-origin requests to maintain each visitor's session.

**Deployment Notes**

- Render free-tier services may sleep after inactivity.
- The first request after a service sleeps may take approximately 30–60 seconds.
- Uploaded datasets are stored in server memory and may be lost when the service restarts or sleeps.
- The application does not use a persistent database by design.

### Alternative Hosting Platforms

Datix can also be deployed to:

- Railway.
- Fly.io.
- Heroku.
- PythonAnywhere.
- AWS EC2 or other virtual machines.
- Other Python-compatible hosting platforms.

For Gunicorn-based deployment, use:

```bash
gunicorn app:app --bind 0.0.0.0:$PORT --workers 2 --threads 4 --timeout 120
```

## 10. Application Usage

### 10.1 Clean Your Data

1. Upload a dataset.
2. Review the dataset overview.
3. Inspect missing values and column diagnostics.
4. Select the required cleaning operations.
5. Execute the cleaning process.
6. Apply advanced filters if necessary.
7. Export the cleaned dataset.

### 10.2 Visualize Your Data

1. Open the Visualize section.
2. Select a chart type.
3. Choose the required columns.
4. Configure grouping options if necessary.
5. Generate the visualization.
6. Use the Chart Guide to select suitable chart types.

### 10.3 Perform Statistical Analysis

Use the Analyze section to explore:

- Numeric and categorical statistics.
- Group comparisons.
- Outlier detection.
- Data profiles.
- Value counts.
- KPI metrics.

### 10.4 Use the AI Data Assistant

1. Upload a dataset.
2. Open the AI Chat section.
3. Enter a question about your dataset.
4. Review the generated response.
5. Use Quick Actions for predefined analysis tasks.

The Clean, Visualize, Analyze, and AI Chat sections become available after a dataset has been uploaded.

## 11. Data Storage and Privacy

Datix uses an in-memory session-based approach for uploaded datasets.

- Each browser session maintains its own active dataset.
- Uploaded datasets are stored in server memory.
- The application does not persist datasets to a database.
- Dataset files are not written to disk during normal processing.
- Uploaded data may be lost when the server restarts or the session expires.
- Users can explicitly download processed datasets through the export functionality.

Avoid uploading confidential or sensitive datasets to publicly deployed instances unless appropriate security controls have been implemented.

## 12. Troubleshooting

### GROQ_API_KEY Is Not Set

Check that:

1. The `.env` file exists.
2. `GROQ_API_KEY` is configured correctly.
3. The API key is valid.
4. The application has been restarted after changing environment variables.

For production deployments, configure the key through the hosting platform's environment settings.

### Invalid GROQ_API_KEY

Verify that:

- The key was copied completely.
- There are no additional spaces or newlines.
- The key has not been revoked.
- The correct key is configured in the environment.

### Groq Rate Limit Reached

Groq applies API usage limits.

If a rate limit is reached:

1. Wait briefly before retrying.
2. Check your Groq API usage.
3. Reduce repeated requests if necessary.

### Chart or Analysis Errors

Some visualizations require specific column types.

For example:

- Y-axis values may need to be numeric.
- Group-by columns may need to be categorical.
- Time-series analysis requires a date or time column.

Select compatible columns based on the chart or analysis operation.

### Large Files Are Slow

- Table previews are limited to 100 rows.
- Cleaning and filtering operate on the full dataset in memory.
- Chart and analysis operations process the dataset in memory.
- The default upload limit is 50 MB and can be configured through `MAX_UPLOAD_MB`.

Large datasets may require additional server memory and processing capacity.

### Application Is Slow After Deployment

Free hosting services may sleep after periods of inactivity. The first request after a service starts again can take longer than usual.

## 13. Security Considerations

- Never commit API keys or secrets to GitHub.
- Store sensitive configuration in environment variables.
- Keep `.env` excluded through `.gitignore`.
- Use a strong, randomly generated `SECRET_KEY` in production.
- Configure CORS to allow only trusted frontend origins.
- Be careful when uploading sensitive datasets.
- Secure publicly deployed instances before using them with confidential information.

## Application Screenshots

### Dashboard
![](screenshots/dashboard.png)

### Data Cleaning
![](screenshots/data-cleaning.png)

### Data Visualization
![](screenshots/visualization.png)

### Statistical Analysis
![](screenshots/statistical-analysis.png)

### AI Data Assistant
![](screenshots/ai-assistant.png)

### Advanced Filtering
![](screenshots/advanced-filtering.png)

## 14. Future Improvements

Potential enhancements for future versions include:

- User authentication and account management.
- Persistent dataset storage.
- Database integration.
- Larger dataset processing and optimization.
- Additional visualization types.
- Advanced statistical and predictive analysis.
- Automated machine learning workflows.
- AI-generated dashboards and reports.
- Scheduled data-processing workflows.
- More export formats.
- Improved data privacy and access controls.

## 15. License

This project is licensed under the MIT License.

See the `LICENSE` file for more information.

*Ensure that an MIT License file is included in the repository before describing the project as MIT-licensed.*

## 16. Acknowledgements

Datix is built using the following technologies and services:

- [Python](https://www.python.org/)
- [Flask](https://flask.palletsprojects.com/)
- [pandas](https://pandas.pydata.org/)
- [NumPy](https://numpy.org/)
- [SciPy](https://scipy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [Groq Cloud](https://console.groq.com/)
- Llama 3

## 17. Author

**Abeesh**

---

If you find Datix useful, consider giving the repository a star on GitHub.
