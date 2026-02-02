# ChargeMaster - Optimal EV Charging Location Finder

An optimization and visualization tool for municipal planners to identify the best placement for electric vehicle (EV) charging stations in Bangalore. **ChargeMaster** helps minimize total social costs by combining charging demand analysis with proximity to essential services.

Addressing the critical question: **Where should charging stations be placed to minimize total social cost?**

## Overview

With India's government targeting 30% electric vehicle adoption by 2030, the challenge of optimal charging station placement becomes increasingly important. "Range anxiety" remains a significant barrier to EV adoption, especially for apartment dwellers without access to home charging. ChargeMaster solves this by combining optimization algorithms with interactive visualization to guide infrastructure planning decisions.

## Key Features

- **Optimization Engine**: Solves the facility location problem using advanced algorithms
- **Interactive Maps**: Visualize optimal locations using Folium heatmaps and markers
- **Multiple Scenarios**: Test various EV penetration ratios
- **Proximity Analysis**: Considers nearby amenities (food courts, shopping malls, apartments, etc.)
- **Web Interface**: User-friendly Flask web application for exploration and analysis

## Packages

Install required dependencies with:

```bash
pip install -r requirements.txt
```

This project uses:
- **Optimization**: Python optimization libraries for solving the facility location problem
- **Visualization**: Folium for interactive maps
- **Web Framework**: Flask for the web application
- **Data Processing**: Pandas and NumPy for data analysis

## Data Sources

- **Demand for Charging**: Trip data from Bangalore (2016-2018) from [Uber Movement Dataset](https://github.com/syedmisbah/Uber-movement-bangalore-dataset)
- **Supply Points**: Existing charging stations and potential locations (parking lots) from Google Maps API
- **Proximity Data**: Locations of apartments, food courts, shopping malls, gas stations, and universities

## Optimization Model

### Decision Variable
Choose a subset of parking lots to install EV chargers.

### Objective Function
Minimize: (Cost of installing chargers) + (Total travel distance from stations to destinations)

### Constraints
1. Each destination zone must have adequate charging capacity
2. Each charging station's capacity cannot exceed its limit

### Distance Calculation
Uses the Haversine formula to calculate great-circle distances between coordinates:

```
d = 2R × arcsin(√[sin²((lat₂-lat₁)/2) + cos(lat₁) × cos(lat₂) × sin²((lon₂-lon₁)/2)])
```

## Web Application

### User Interface
The web app guides users through an intuitive workflow:

1. **Input Stage**: Specify the EV penetration ratio (% of vehicles to convert to electric)
2. **Processing**: Run optimization algorithm
3. **Results**: View optimal parking locations as a table
4. **Exploration**: Visualize results on an interactive map with:
   - Heatmaps showing demand density
   - Markers for recommended charging locations
   - Existing charging station information
   - Nearby places overlays

### Map Features
- Color-coded density visualization
- Cluster markers for charging stations
- Popup information for each location
- Layer controls for different amenity types

## Quick Start

### Clone the Repository
```bash
git clone https://github.com/weeiiiiiii/ChargeMaster.git
cd ChargeMaster
```

### Setup Environment
```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

### Run the Application
```bash
python app.py
```

Navigate to `http://127.0.0.1:5000` and start exploring optimal charging locations!

## Project Structure

```
ChargeMaster/
├── app.py                    # Flask application
├── requirements.txt          # Python dependencies
├── templates/                # HTML templates for web interface
│   ├── index.html           # Landing page
│   ├── charging_map.html    # Map visualization
│   └── ...
├── static/                   # CSS, JavaScript, images
│   ├── css/
│   ├── js/
│   └── img/
├── csv/                      # Data files
│   ├── charging_station.csv
│   ├── parking.csv
│   ├── apartment.csv
│   └── ...
└── scripts/                  # Jupyter notebooks for analysis
    ├── ChargingAlgoAndGrading.ipynb
    ├── AnalyseUberTrips&NearbyPlaces.ipynb
    └── ...
```

## Methodology

### Step 1: Demand Analysis
Analyze Uber trip data to identify high-demand zones for charging in Bangalore.

### Step 2: Supply Mapping
Identify potential charging locations (parking lots, parking complexes) using Google Maps API data.

### Step 3: Proximity Scoring
Evaluate each location's proximity to:
- Apartments and residential areas
- Food courts and restaurants
- Shopping malls
- Gas stations
- Universities and educational institutions

### Step 4: Optimization
Solve the mixed-integer linear programming problem to find optimal locations that:
- Minimize installation costs
- Reduce average travel distance for EV users
- Meet capacity constraints

### Step 5: Visualization
Display results interactively on maps for decision-making and planning.

## Technical Stack

| Component | Technology |
|-----------|-----------|
| Backend | Python, Flask |
| Optimization | Linear Programming Solver |
| Data Processing | Pandas, NumPy |
| Visualization | Folium, Leaflet.js |
| Frontend | HTML5, CSS3, JavaScript |
| Deployment | Heroku (optional) |

## Usage Examples

### Scenario 1: Low EV Penetration (5%)
Identify critical charging stations for early adopters in high-density areas.

### Scenario 2: Medium EV Penetration (15%)
Plan moderate expansion of charging infrastructure.

### Scenario 3: High EV Penetration (30%)
Comprehensive charging network to support government's 2030 target.

## Results Interpretation

- **Green zones**: High demand areas needing more charging stations
- **Recommended markers**: Optimal parking lots for charger installation
- **Blue zones**: Existing charging infrastructure
- **Tables**: Ranked list of locations with metrics

## Future Enhancements

- Multi-city support
- Real-time traffic data integration
- Cost-benefit analysis reporting
- Phased implementation planning
- Dynamic pricing scenarios
- Battery degradation modeling

## License

This project is open source and available under the MIT License.

## Contributors

ChargeMaster was developed to address the critical infrastructure gaps in India's EV charging network.

## Contact & Support

For questions, suggestions, or collaboration:
- GitHub: [https://github.com/weeiiiiiii/ChargeMaster](https://github.com/weeiiiiiii/ChargeMaster)
- Issues: Report bugs and request features via GitHub Issues
 Linear Programming - Optimization Techniques

---

**Mission**: Making electric vehicle infrastructure planning data-driven and optimal for sustainable urban mobility.
