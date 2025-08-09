# E-commerce Marketing Analytics Toolkit

This comprehensive marketing analytics toolkit provides advanced capabilities for data-driven marketing decisions across the entire marketing lifecycle. It enables marketers to analyze historical performance, disaggregate temporal data, measure channel effectiveness, optimize budget allocation, and extract customer insights through integrated Python-based modules.

## 📁 Project Structure

```
Compiled_Notebooks/
├── dataset_maker.ipynb           # Data preparation and cleaning
├── eda.ipynb                     # Exploratory data analysis
├── hypothesis_testing.ipynb      # Statistical hypothesis testing
├── temporal_disaggregation.ipynb # Temporal data disaggregation
├── hill_function.ipynb           # Hill function modeling and optimization
├── optimisation(experimental).ipynb # Experimental optimization models
├── requirements.txt              # Python dependencies
└── README.txt                    # file
```

## 🎯 Core Marketing Channels

The toolkit analyzes and optimizes these standard marketing channels:

- **TV**: Television advertising
- **Digital**: Digital display and video advertising  
- **Sponsorship**: Brand sponsorships and partnerships
- **Content Marketing**: Blogs, videos, infographics, etc.
- **Online Marketing**: General online campaigns
- **Affiliates**: Affiliate marketing programs
- **SEM**: Search engine marketing/PPC
- **Radio**: Radio advertising
- **Other**: Additional marketing channels

## 📊 Detailed Components

### 1. Data Preparation (`dataset_maker.ipynb`)
Central data processing module that supports all other components.

**Key Features:**
- Manages date transformations and feature creation
- Integrates marketing, sales, and event data
- Creates derived features for modeling
- Identifies sale periods and special events
- Handles data cleaning and validation

**Technical Details:**
- Date handling and period calculations
- Feature engineering pipeline
- Data cleaning and validation
- Outlier detection and handling

### 2. Exploratory Data Analysis (`eda.ipynb`)
Comprehensive exploratory data analysis of e-commerce data.

**Key Features:**
- Data cleaning and preprocessing
- Customer order analysis
- Product performance analysis
- Marketing channel analysis
- Temporal patterns and seasonality
- Payment and delivery analysis

**Technical Details:**
- Statistical analysis and visualization
- Time series analysis
- Customer segmentation
- Revenue pattern analysis

### 3. Hypothesis Testing (`hypothesis_testing.ipynb`)
Statistical hypothesis testing for marketing insights.

**Key Features:**
- Impact of media spending on revenue
- Effect of promotions on sales performance
- Relationship between NPS scores and revenue
- Impact of discounts on sales
- Time series analysis for seasonality

**Technical Details:**
- T-tests and ANOVA analysis
- Linear regression modeling
- Correlation analysis
- Seasonal decomposition

### 4. Temporal Disaggregation (`temporal_disaggregation.ipynb`)
Converts monthly marketing channel investments into daily values using advanced statistical methods.

**Key Features:**
- Implements Litterman-MaxLog temporal disaggregation algorithm
- Uses XGBoost regression to model relationship between daily GMV and marketing spend
- Creates rolling metrics (3-day, 7-day) to capture temporal patterns
- Preserves monthly totals through precise rebalancing
- Validates results with comparison metrics

**Technical Details:**
- Uses timedisagg library's TempDisagg class
- Applies non-negativity constraints for realistic daily values
- Includes MinMaxScaler normalization for model features
- Produces validation tables comparing original vs. disaggregated amounts

### 5. Hill Function Modeling (`hill_function.ipynb`)
Advanced modeling using Hill functions for marketing response curves.

**Key Features:**
- Individual channel response modeling using Hill functions
- Non-negative least squares (NNLS) for coefficient estimation
- Saturation level calculation for each channel
- Response curve visualization
- Channel effectiveness analysis

**Technical Details:**
- Hill function parameters (Hill coefficient, EC50)
- Saturation levels based on channel performance
- Non-negative least squares optimization
- Response curve fitting and visualization

### 6. Experimental Optimization (`optimisation(experimental).ipynb`)
Experimental optimization models for marketing budget allocation.

**Key Features:**
- Adstock modeling for marketing carryover effects
- Advanced optimization algorithms
- Budget allocation strategies
- Performance forecasting
- Experimental modeling approaches

**Technical Details:**
- Adstock feature creation with decay rates
- Variance Inflation Factor (VIF) analysis
- Multiple optimization approaches
- Experimental model validation

## 🛠 Technical Architecture

The toolkit employs a modular design with these components:

### Data Layer:
- Input processing for daily GMV/sales data
- Monthly marketing channel data management
- Event calendar integration

### Modeling Layer:
- XGBoost for daily pattern prediction
- Hill functions for response modeling
- Non-negative least squares (NNLS)
- Temporal disaggregation algorithms

### Optimization Layer:
- Budget allocation optimization
- Constraint handling
- Multi-period optimization

### Analytics Layer:
- ROI and efficiency calculations
- Channel importance rankings
- Visualization and reporting

## 📋 Data Requirements

### Required Datasets

**Daily Sales Data** (`datewise_vertical_data.csv`):
- Columns: `order_date`, `gmv`, `units`, `holiday`, `sale`, `sla`, `pay_day`
- Format: CSV with date in YYYY-MM-DD format
- Time Period: Minimum 12 months recommended

**Monthly Marketing Data** (`Media data-Sale Calendar-NPS Scores_Data.xlsx`):
- Columns: `Year-Month`, `Total_Investment`, `TV`, `Digital`, `Sponsorship`, `Content_Marketing`, `Online_marketing`, `Affiliates`, `SEM`, `Radio`, `Other`
- Format: Excel with Year-Month in YYYY-MM format
- Time Period: Matching daily sales data period

**Event Calendar** (included in marketing data file):
- Columns: `date`, `event_name`, `event_type`
- Events: holidays, promotional sales, pay days

### Data Format Requirements
- Date formats consistent (YYYY-MM-DD for daily, YYYY-MM for monthly)
- No missing values in key fields (can be zero but not NULL)
- Consistent channel naming across files
- Numeric values for all metrics

## 🚀 Installation and Dependencies

### Required Libraries
```bash
# Core data processing and analysis
pandas>=1.3.5
numpy>=1.20.0
scipy>=1.7.0

# Machine learning libraries
scikit-learn>=1.0.2
xgboost>=1.5.0
statsmodels>=0.13.0

# Optimization
gurobipy>=9.5.0

# Time series analysis and disaggregation
timedisagg>=0.9.0

# Visualization
matplotlib>=3.5.0

# Progress bars
tqdm>=4.62.0

# Optional: Jupyter environment for interactive development
jupyter>=1.0.0
notebook>=6.4.0
```

### Recommended System Requirements
- Python 3.7+
- 8GB+ RAM
- 4+ CPU cores
- 10GB+ free disk space

## 📈 Performance Metrics

The toolkit provides these key marketing performance metrics:

- **Channel ROI**: Revenue generated per unit spend for each channel
- **Channel Elasticity**: Percentage change in revenue for percentage change in channel spend
- **Saturation Levels**: Point at which additional spend yields diminishing returns
- **Optimal Lag Time**: Time period between marketing activity and maximum impact
- **Channel Effectiveness**: Relative contribution of each channel to total revenue
- **Marketing Efficiency**: Revenue generated per unit of marketing at optimal lag time

## 🔄 Workflow Integration

### Recommended Workflow
1. **Data Preparation** (`dataset_maker.ipynb`)
2. **Exploratory Analysis** (`eda.ipynb`)
3. **Hypothesis Testing** (`hypothesis_testing.ipynb`)
4. **Temporal Disaggregation** (`temporal_disaggregation.ipynb`)
5. **Hill Function Modeling** (`hill_function.ipynb`)
6. **Experimental Optimization** (`optimisation(experimental).ipynb`)

### Data Flow
- `dataset_maker` creates cleaned data for all modules
- `eda` provides insights and patterns
- `hypothesis_testing` validates assumptions
- `temporal_disaggregation` creates daily marketing values
- `hill_function` models channel response curves
- `optimisation` produces allocation recommendations

## 🔧 Troubleshooting

### Common Issues
- **Missing Channel Data**: Ensure all channels exist in marketing data file
- **Column Name Variations**: Check for consistency between 'Content_Marketing' and 'Content Marketing'
- **Convergence Issues**: Adjust parameters for optimization models
- **Negative Values**: Check rebalancing procedure in disaggregation
- **Memory Errors**: Process data in chunks or reduce time period

### Performance Optimization
- Use smaller data samples for initial testing
- Adjust XGBoost parameters for faster training
- Simplify constraints in optimization models
- Run modules independently for specific analyses

## 👥 Developer Information

- Original development by Marketing Analytics Team
- Temporal disaggregation using timedisagg package with Litterman method
- Hill function parameters estimated from historical channel performance
- Experimental optimization using advanced algorithms

## 📝 Example Use Cases

- **Annual Marketing Planning**: Optimize next year's marketing budget
- **Mid-year Reallocation**: Adjust channel mix based on performance
- **Campaign Effectiveness**: Measure impact of specific campaigns
- **Channel Saturation Analysis**: Identify diminishing returns thresholds
- **Customer Feedback Integration**: Align marketing with sentiment insights

## 📄 License

This project is for internal use and analysis purposes.
