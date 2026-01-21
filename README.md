# Kurnool ENT Centers Website

A modern, professional website for ENT care services with real-time Google Maps reviews integration.

## Features

- 🏥 **Medical Website**: Professional ENT care services website
- 🎨 **Clean Design**: Modern, green-themed design with excellent readability
- ⭐ **Google Maps Reviews**: Dynamic integration with real Google reviews
- 🌙 **Dark Mode**: Toggle between light and dark themes
- 📱 **Responsive**: Mobile-first design that works on all devices
- ✨ **Animations**: Smooth scroll animations and hover effects

## Setup Instructions

### 1. Install Dependencies

```bash
cd git/kurnoolentcenters
pip install flask flask-cors requests
```

### 2. Configure Google Places API (Optional - for Real Reviews)

To display real Google Maps reviews, you need to set up Google Places API:

#### Get API Key:
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable "Places API" and "Places API (New)"
4. Create an API key in "Credentials"
5. Restrict the API key to your domain for security

#### Get Place ID:
1. Go to [Google Places API Place ID Finder](https://developers.google.com/maps/documentation/places/web-service/place-id)
2. Search for your business: "Kurnool ENT Center Dr. S Reena Tanaz"
3. Copy the Place ID (starts with "ChIJ...")

#### Set Environment Variables:
```bash
# Windows
set GOOGLE_PLACES_API_KEY=your_api_key_here
set PLACE_ID=your_place_id_here

# Linux/Mac
export GOOGLE_PLACES_API_KEY=your_api_key_here
export PLACE_ID=your_place_id_here
```

Or create a `.env` file:
```
GOOGLE_PLACES_API_KEY=your_api_key_here
PLACE_ID=your_place_id_here
```

### 3. Run the Application

```bash
python app.py
```

The website will be available at:
- **Local:** http://127.0.0.1:5000
- **Network:** http://192.168.29.201:5000 (if accessible)

## API Endpoints

### GET `/api/google-reviews`
Returns Google Maps reviews for the business.

**Response:**
```json
{
  "success": true,
  "reviews": [
    {
      "author_name": "John Doe",
      "rating": 5,
      "text": "Great service!",
      "time": "2 weeks ago",
      "profile_photo_url": "https://..."
    }
  ],
  "message": "Real Google reviews fetched successfully"
}
```

## Color Scheme

- **Background:** `#E4F0E4` (Light green)
- **Text:** `#333333` (Dark gray)
- **Primary:** `#2d5a27` (Deep green)
- **Borders:** `#c8d9c8` (Light green borders)

## Technologies Used

- **Backend:** Flask (Python)
- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **APIs:** Google Places API (optional)
- **Libraries:** ScrollReveal.js, Font Awesome
- **Fonts:** Inter, Poppins (Google Fonts)

## File Structure

```
kurnool-ent-centers/
├── app.py                 # Flask backend with Google API integration
├── templates/
│   └── index.html        # Main website template
├── static/
│   ├── styles.css        # All styling
│   ├── ear-cartoon.png   # Service icons
│   ├── nose-cartoon.png
│   └── throat-cartoon.png
└── README.md             # This file
```

## Development Notes

- **Mock Data:** If no Google API key is configured, the site shows mock reviews
- **CORS:** Enabled for frontend API calls
- **Error Handling:** Graceful fallbacks for API failures
- **Responsive:** Works on all screen sizes
- **Accessibility:** Proper ARIA labels and focus management

## Deployment

For production deployment:

1. Set environment variables securely
2. Use a production WSGI server (Gunicorn)
3. Configure HTTPS
4. Set up monitoring and logging

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Built with ❤️ for Kurnool ENT Centers**
