# CarZone Project - Model Architecture & Functionality

This document explains the data models and their roles in the CarZone car dealership application.

## Django Apps Overview

The project is organized into 4 main Django apps, each handling specific functionality:

### 1. Cars App (`cars/`)
**Purpose**: Core functionality for car listings and inventory management

#### Car Model
The main model that stores all car information:

**Key Fields:**
- `car_title`: Display name of the car
- `state`, `city`: Location information
- `model`, `year`, `color`: Basic car specifications
- `price`: Car pricing
- `description`: Rich text description using CKEditor
- `car_photo` + 4 additional photos: Image gallery
- `features`: Multi-select field for car features (Cruise Control, Airbags, etc.)
- `body_style`, `engine`, `transmission`: Technical specifications
- `miles`, `milage`, `fuel_type`: Performance metrics
- `doors`, `passengers`: Capacity information
- `vin_no`: Vehicle identification
- `is_featured`: Boolean flag for homepage promotion
- `created_date`: Timestamp for sorting

**What it does:**
- Stores complete car inventory with photos and specifications
- Supports advanced filtering and search functionality
- Manages featured cars for homepage display
- Tracks car condition, ownership history, and technical details

### 2. Pages App (`pages/`)
**Purpose**: Static content and team information

#### Team Model
Stores information about dealership staff:

**Key Fields:**
- `first_name`, `last_name`: Staff member names
- `designation`: Job title/role
- `photo`: Staff member photo
- `facebook_link`, `twitter_link`, `google_plus_link`: Social media profiles
- `created_date`: Record creation timestamp

**What it does:**
- Manages "About Us" team member profiles
- Displays staff information on the about page
- Handles social media integration for team members
- Supports dynamic team roster updates

### 3. Contacts App (`contacts/`)
**Purpose**: Customer inquiries and lead management

#### Contact Model
Stores customer inquiries about specific cars:

**Key Fields:**
- `first_name`, `last_name`: Customer information
- `car_id`: Reference to the car of interest
- `customer_need`: Type of inquiry (purchase, test drive, etc.)
- `car_title`: Car name for reference
- `city`, `state`: Customer location
- `email`, `phone`: Contact information
- `message`: Custom inquiry message
- `user_id`: Links to registered user (if applicable)
- `create_date`: Inquiry timestamp

**What it does:**
- Captures customer interest in specific vehicles
- Stores lead information for sales follow-up
- Links inquiries to both cars and registered users
- Enables customer relationship management

### 4. Accounts App (`accounts/`)
**Purpose**: User authentication and account management

**Key Features:**
- Uses Django's built-in User model
- No custom models defined (relies on Django auth)
- Integrates with Django Allauth for social login
- Supports Facebook and Google authentication
- Provides user dashboard functionality

**What it does:**
- Handles user registration and login
- Manages user sessions and authentication
- Provides social media login options
- Creates user dashboards for account management

## Model Relationships

### Data Flow:
1. **Car Model** → Central inventory system
2. **Contact Model** → References cars via `car_id`
3. **Team Model** → Independent staff information
4. **User Model** → Links to contacts via `user_id`

### Key Integrations:
- Cars can have multiple contact inquiries
- Users can make multiple inquiries
- Featured cars appear on homepage
- Team members display on about page

## Business Logic

### Search & Filtering:
The Car model supports complex queries:
- **Text Search**: Description keyword matching
- **Categorical Filters**: Model, city, year, body style
- **Price Range**: Min/max price filtering
- **Feature Matching**: Multi-select feature filtering

### User Experience:
- **Guest Users**: Can browse and inquire about cars
- **Registered Users**: Get personalized dashboard and inquiry tracking
- **Admin Users**: Full CRUD operations on all models

### Content Management:
- **Rich Text**: Car descriptions support formatted content
- **Image Gallery**: Multiple photos per car with organized storage
- **Dynamic Choices**: Year choices auto-update, state choices predefined
- **Feature Flags**: Cars can be marked as featured for promotion

## Technical Implementation

### Database Design:
- **PostgreSQL**: Production database with full-text search capabilities
- **SQLite**: Development database for local testing
- **Migrations**: Proper Django migration system for schema changes

### File Management:
- **Media Files**: Organized by date (`photos/%Y/%m/%d/`)
- **Static Files**: Separate handling for CSS, JS, and images
- **WhiteNoise**: Production static file serving

### Performance Considerations:
- **Pagination**: Car listings paginated (4 per page)
- **Indexing**: Created date ordering for recent cars first
- **Caching**: Static file compression and caching
- **Optimization**: Distinct queries for search dropdowns

This architecture provides a scalable foundation for a car dealership website with room for future enhancements like inventory tracking, financing integration, and advanced CRM features.