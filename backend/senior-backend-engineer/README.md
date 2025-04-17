# Senvo Senior Backend Challenge

## Overview

Welcome to the Senvo Senior Backend Challenge! At Senvo we are big supporters of our public infrastructure network, 
and even offer a discounted subscription with the BVG Job Ticket! 

In light of this, you'll build a backend API service that models Berlin's public transportation network and provides 
route-overlap analysis capabilities.

The challenge involves storing Berlin's transit network (S-Bahn, U-Bahn, Tram, and Regional trains) in a relational 
database and implementing an API to query overlapping segments between different trips.

## Objective

Create a Python-based API service that can:

1. Import and store Berlin's transit network data in a relational database
2. Provide endpoints to query routes and find overlapping segments
3. Calculate and return overlapping segments between different trips
4. Handle efficient querying of complex route data

## Technical Requirements

- Python 3.12+ 
- Database: PostgreSQL (preferred) or alternative relational database
- Web framework: FastAPI (preferred) or Flask
- Proper data modeling with SQLAlchemy ORM
- RESTful API design
- Comprehensive test coverage
- Docker containerization

## Data Provided

We provide comprehensive data for Berlin's public transit network:
- S-Bahn lines and stations
- U-Bahn lines and stations
- Tram lines and stations
- Regional train lines and stations

Each dataset contains line identifiers and ordered lists of stations.

## Core Features to Implement

### 1. Data Modeling & Storage

Design an efficient database schema to represent:
- Transit lines (S-Bahn, U-Bahn, etc.)
- Stations
- Routes (ordered sequences of stations)
- Connections between stations

Consider the design patterns on how to retrieve and store this data.

### 2. API Endpoints

Implement the following API endpoints:

- `GET /api/lines` - Return all transit lines
- `GET /api/lines/{line_id}` - Return details of a specific line
- `GET /api/stations` - Return all stations (with pagination)
- `GET /api/stations/{station_id}` - Return details of a specific station
- `GET /api/routes/{line_id}` - Return the route (ordered stations) for a specific line
- `POST /api/overlaps` - Find overlapping segments between provided routes

### 3. Overlap Analysis

The core of this challenge is the overlap analysis. When given two or more routes, your API should identify all 
segments where these routes overlap. A segment is defined as two or more consecutive stations that are shared 
between routes.

Example request to the overlap endpoint:
```json
{
  "routes": ["U2", "U1", "S5"]
}
```

Example response (feel free to change this!):
```json
{
  "overlaps": [
    {
      "routes": ["U1", "U2"],
      "segments": [
        {
          "stations": ["Wittenbergplatz", "Nollendorfplatz"],
          "segment_length": 2
        },
        {
          "stations": ["Gleisdreieck", "Möckernbrücke"],
          "segment_length": 2
        }
      ]
    },
    {
      "routes": ["U2", "S5"],
      "segments": [
        {
          "stations": ["Alexanderplatz", "Hauptbahnhof"],
          "segment_length": 2
        }
      ]
    }
  ]
}
```

## Advanced Requirements (Bonus Points) - Do not feel pressured to implement these!

- Implement route search with transfer suggestions
- Some stations have multiple names eg. Berlin-Lichtenberg and Lichtenberg - handle this in your data model!
- Add geographic coordinates to stations and calculate actual distances
- Implement caching for frequently requested routes 
- Build a simple monitoring dashboard for API performance (HTMX, Streamlit, basic NextJS or similar..) Remember, 
  this is a backend challenge!

## Evaluation Criteria

Your submission will be evaluated on:

1. **Code quality and organization**: Clean, readable code following Python best practices
2. **Database design**: Efficient schema design and query optimization
3. **API design**: RESTful principles, clear documentation, error handling
4. **Algorithm efficiency**: Optimized approach to finding route overlaps
5. **Testing**: Comprehensive test coverage including edge cases
6. **Documentation**: Clear explanation of your solution and setup instructions

## Submission Guidelines

1. Create a private GitHub repository with your solution
2. Include a comprehensive README with:
   - Explanation of your data model
   - Setup instructions
   - API documentation
   - Any assumptions or design decisions you made
   - If you had more time, what would you improve or add?
3. Include a Docker Compose configuration for easy setup

## Time Expectation

We expect this challenge to take approximately 4-6 hours. Focus on building a clean, working solution rather than 
implementing all possible features.

Good luck, and we look forward to reviewing your solution!
