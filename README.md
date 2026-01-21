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

## Docker Deployment

### Build Docker Image

```bash
# Navigate to project directory
cd "C:\Work\git\kurnoolentcenters"

# Build the Docker image
docker build -t kurnoolentcenters:v3.0 .

# Alternative: Build with no cache (if you encounter issues)
docker build --no-cache -t kurnoolentcenters:v3.0 .
```

### Run Docker Container

```bash
# Run the container
docker run -p 5000:5000 kurnoolentcenters:v3.0

# Run in detached mode
docker run -d -p 5000:5000 --name kurnool-ent-center kurnoolentcenters:v3.0

# View container logs
docker logs kurnool-ent-center

# Stop the container
docker stop kurnool-ent-center

# Remove the container
docker rm kurnool-ent-center
```

### Docker Image Management

```bash
# List all images
docker images

# Remove an image
docker rmi kurnoolentcenters:v3.0

# Clean up unused images and containers
docker system prune
```

## Kubernetes Deployment with Helm

### Prerequisites

- Kubernetes cluster
- Helm 3.x installed
- kubectl configured

### Install Helm Chart

```bash
# Navigate to the project directory
cd "C:\Work\git\kurnoolentcenters"

# Install the Helm chart
helm install kurnoolentcenters ./helm/kurnoolentcenters

# Install with custom values
helm install kurnoolentcenters ./helm/kurnoolentcenters --set image.tag=v3.0

# Install with custom name
helm install my-kurnool-ent ./helm/kurnoolentcenters
```

### Helm Chart Management

```bash
# List all releases
helm list

# View release status
helm status kurnoolentcenters

# Upgrade the release
helm upgrade kurnoolentcenters ./helm/kurnoolentcenters

# Rollback to previous version
helm rollback kurnoolentcenters 1

# Uninstall the release
helm uninstall kurnoolentcenters
```

### Custom Configuration

Edit `helm/kurnoolentcenters/values.yaml` to customize:

```yaml
# Image configuration
image:
  repository: kurnoolentcenters
  tag: "v3.0"
  pullPolicy: IfNotPresent

# Resource limits
deployment:
  resources:
    limits:
      cpu: 500m
      memory: 512Mi
    requests:
      cpu: 100m
      memory: 128Mi

# Environment variables
env:
  FLASK_ENV: production
  FLASK_DEBUG: "false"

# Health checks
healthCheck:
  enabled: true
  path: /health
  port: 5000
```

### Access the Application

After deployment:

```bash
# Get service information
kubectl get services

# Get pod information
kubectl get pods

# Port forward to access locally
kubectl port-forward service/kurnoolentcenters 8080:80

# Access at http://localhost:8080
```

## Production Deployment

### Environment Variables

Set these environment variables for production:

```bash
# Flask configuration
export FLASK_ENV=production
export FLASK_DEBUG=false

# Google Places API (optional)
export GOOGLE_PLACES_API_KEY=your_api_key_here
export PLACE_ID=your_place_id_here
```

### Security Considerations

1. **API Keys**: Store Google API keys securely using Kubernetes secrets
2. **HTTPS**: Configure SSL/TLS certificates
3. **Resource Limits**: Set appropriate CPU and memory limits
4. **Health Checks**: Monitor application health
5. **Logging**: Implement proper logging and monitoring

### Monitoring and Maintenance

```bash
# Monitor pod resources
kubectl top pods

# View application logs
kubectl logs -f deployment/kurnoolentcenters

# Scale the application
kubectl scale deployment kurnoolentcenters --replicas=3
```

## Troubleshooting

### Docker Issues

**Permission Denied:**
```bash
# Add user to docker group (Linux)
sudo usermod -aG docker $USER
# Then logout and login again
```

**Port Already in Use:**
```bash
# Find and kill process using port 5000
lsof -i :5000
kill -9 <PID>
```

### Kubernetes Issues

**Image Pull Errors:**
```bash
# Check image pull policy
kubectl describe pod <pod-name>

# Use IfNotPresent or Always for development
```

**Resource Limits:**
```bash
# Check resource usage
kubectl top nodes
kubectl top pods
```

**Health Check Failures:**
```bash
# Check pod status
kubectl describe pod <pod-name>

# Check application logs
kubectl logs <pod-name>
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Built with ❤️ for Kurnool ENT Centers**
