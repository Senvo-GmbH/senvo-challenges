# Senvo Junior Backend Engineer Coding Challenge

## Context
Welcome to the Senvo Junior Backend Engineer Challenge! Imagine you're building the backbone of a package tracking 
system that will help e-commerce businesses track their shipments across the globe. Your mission is to create a 
"Shipment Tracker" API that can store, retrieve, and analyze shipment data.

## Shipment Definition
A shipment is defined by the following attributes:
- Shipment number (tracking number)
- Shipment date: When the package was picked up by the carrier
- Destination address consisting of fields: address line 1, address line 2, postal code, city and country code
- Physical dimensions of the package in cm (length, width, height)
- Weight of the package in grams
- Price of the shipment service (amount and currency)
- Name of carrier: Possible values are `dhl-express`, `ups`, and `fedex`
- Current status: One of `processing`, `in-transit`, `delivered`, or `exception`
- Delivery estimate: Expected delivery date

## API Requirements
Your application should provide a JSON API with the following endpoints:

### Core Endpoints
1. **POST /shipments**
   - Accept a list of shipments to be stored in a PostgreSQL database
   - Validate all input data and return appropriate error messages
   - Return status code 201 on success

2. **GET /shipments**
   - Return a list of shipments with pagination (default: 10 per page)
   - Implement filtering by:
     - Date range (shipment date)
     - Carrier
     - Price range
     - Current status
     - Country code
   - Filters should work additively (can be combined)
   - Support sorting by date, price, or weight

### Bonus Endpoints (choose at least one)
3. **GET /shipments/{tracking_number}**
   - Return detailed information about a specific shipment
   - Include a calculation of delivery progress (% complete based on shipment date and delivery estimate)

4. **GET /analytics/carrier-statistics**
   - Return statistics about each carrier:
     - Average price
     - Average delivery time (estimate vs. shipment date)
     - Total number of packages
     - Percentage of packages by status

5. **POST /shipments/{tracking_number}/update-status**
   - Allow updating the status of a shipment
   - Implement a simple state machine (e.g., cannot go from `delivered` back to `in-transit`)
   - Log status changes with timestamps

## Technical Requirements
- Python 3.12+ with a web framework of your choice (FastAPI or Flask recommended)
- PostgreSQL database with appropriate schema design
- Data validation for all inputs
- Basic error handling with informative error messages
- Simple documentation for your API endpoints

## Testing Requirements
- Unit tests for your validation logic
- API tests for your endpoints
- Optional: Include a simple load test script that demonstrates how your API performs with many shipments

## Evaluation Criteria
- **Functionality**: Does the API work as expected?
- **Code Quality**: Is the code clean, well-organized, and following Python best practices?
- **Error Handling**: Are errors handled gracefully with informative messages?
- **Database Design**: Is the database schema well-designed for the data being stored?
- **Creativity**: How did you approach the fun elements of the challenge?

## Submission Guidelines
- Create a private GitHub repository with your solution
- Include a README with:
  - Setup instructions
  - Brief explanation of your approach
  - Which bonus endpoints and fun elements you implemented
  - Any additional features you added
- Add a simple diagram of your database schema

We expect this challenge to take approximately 2-4 hours. Focus on building a clean, working solution rather than 
implementing all possible features. Have fun with it, and we look forward to seeing your creative approach!
