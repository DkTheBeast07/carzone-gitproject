# CarZone - Car Dealership Website

A comprehensive Django-based car dealership website that allows users to browse, search, and inquire about cars for sale.

## Features

- **Car Listings**: Browse through available cars with detailed information
- **Advanced Search**: Filter cars by model, city, year, body style, price range, and more
- **User Authentication**: Register, login, and manage user accounts with social login support
- **Car Details**: View comprehensive car information including photos, specifications, and features
- **Contact System**: Inquire about specific cars or contact the dealership
- **Admin Panel**: Manage cars, users, and inquiries through Django admin
- **Responsive Design**: Mobile-friendly interface
- **Featured Cars**: Highlight special or promoted vehicles

## Technology Stack

- **Backend**: Django 3.0.7
- **Database**: PostgreSQL (with SQLite for development)
- **Frontend**: HTML, CSS, JavaScript, Bootstrap
- **Authentication**: Django Allauth (supports Facebook and Google login)
- **Rich Text Editor**: CKEditor
- **Image Handling**: Pillow
- **Deployment**: Heroku with WhiteNoise for static files

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd carzone-gitproject-master
   ```

2. **Create virtual environment**
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Database setup**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create superuser**
   ```bash
   python manage.py createsuperuser
   ```

6. **Run the development server**
   ```bash
   python manage.py runserver
   ```

## Configuration

### Environment Variables
Set up the following environment variables for production:
- `SECRET_KEY`: Django secret key
- `DATABASE_URL`: PostgreSQL database URL
- `EMAIL_HOST_USER`: SMTP email username
- `EMAIL_HOST_PASSWORD`: SMTP email password

### Social Authentication
Configure Facebook and Google OAuth credentials in Django admin under Social Applications.

## Project Structure

```
carzone/
├── accounts/          # User authentication and dashboard
├── cars/             # Car listings and search functionality
├── contacts/         # Contact forms and inquiries
├── pages/            # Static pages (home, about, services)
├── carzone/          # Main project settings
├── templates/        # HTML templates
├── static/           # CSS, JS, and image files
├── media/            # User uploaded files
└── requirements.txt  # Python dependencies
```

## Usage

1. **Admin Panel**: Access `/admin/` to manage cars, users, and content
2. **Browse Cars**: Visit the cars page to view all available vehicles
3. **Search**: Use the search functionality to filter cars by various criteria
4. **Car Details**: Click on any car to view detailed information
5. **Contact**: Use contact forms to inquire about specific cars
6. **User Account**: Register/login to access dashboard features

## Deployment

The project is configured for Heroku deployment:
- `Procfile` for Heroku process configuration
- `runtime.txt` specifies Python version
- WhiteNoise for static file serving
- PostgreSQL database configuration

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License
This project is open source and available under the MIT License.