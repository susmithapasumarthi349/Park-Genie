# 🅿️ ParkGenie - Your Smart Parking Companion

**Never waste time searching for parking again!**

ParkGenie is a modern, interactive web application that helps users find nearby parking spots using intelligent maps and an AI-powered chatbot assistant. Built with HTML, CSS, JavaScript, and Leaflet.js, it simulates real-world parking data and provides an intuitive interface to explore parking availability across locations worldwide.

---

## ✨ Features

### 🗺️ **Interactive Map Interface**
- Beautiful, responsive map powered by Leaflet.js and OpenStreetMap
- Real-time parking spot markers with availability status
- Color-coded indicators (Green: Available | Orange: Limited | Red: Full)
- Click markers to view detailed parking information
- Smooth zoom and pan controls

### 🤖 **Intelligent Chatbot Assistant**
- Natural language parking search
- Smart suggestions for popular cities
- Conversational interface for easy interaction
- Quick-action suggestion chips
- Context-aware responses

### 📍 **Location Services**
- **"Locate Me"** button for instant GPS-based parking search
- Search in 30+ major Indian cities
- Custom location search worldwide
- **"Search This Area"** for exploring different map regions

### 📋 **Detailed Parking Information**
- Parking spot name and type
- Full address with distance from your location
- Real-time availability status
- Hourly pricing in INR
- Special features (24/7, Security, EV Charging, Covered, Handicap)
- Direct navigation to Google Maps

### 🎨 **Modern UI/UX**
- Sleek gradient design with Poppins font
- Smooth animations and transitions
- Mobile-responsive layout
- Glassmorphism effects
- Professional color scheme

---

## 🚀 Quick Start

### **1. Clone or Download**
```bash
git clone https://github.com/susmithapasumarthi349/Park-Genie.git
cd Park-Genie
```

### **2. Open in Browser**
Simply open the `Code` file in any modern web browser:
```bash
# Double-click the file or use:
open Code  # macOS
start Code # Windows
xdg-open Code # Linux
```

### **3. Start Exploring!**
- Click **"Locate Me"** to find parking near you
- Or chat: *"Find parking in Mumbai"*
- Click any parking card to view on map
- Click **"Directions"** to navigate

---

## 💻 Technology Stack

| Technology | Purpose |
|---|---|
| **HTML5** | Structure and semantic markup |
| **CSS3** | Styling, animations, gradients |
| **JavaScript (ES6+)** | Core functionality and logic |
| **Leaflet.js** | Interactive mapping library |
| **OpenStreetMap** | Map tiles and geodata |
| **Geolocation API** | User location detection |
| **Google Fonts (Poppins)** | Modern typography |

---

## 🛠️ How It Works

### **Architecture Flow**
```
User Input (Chat/Map) → Location Processing → Parking Data Generation 
                          ↓
       Display on Map ← Filter & Sort ← Calculate Distances
```

### **Key Components**

1. **Chatbot Engine**
   - Natural language processing for city names
   - Query matching with 30+ Indian cities
   - Contextual responses with suggestions

2. **Map Controller**
   - Leaflet.js map initialization
   - Dynamic marker management
   - Popup information display

3. **Data Generator**
   - Mock parking data simulation
   - Random availability and pricing
   - Distance calculations

4. **UI Manager**
   - Chat message rendering
   - Parking card creation
   - Loading states and animations

---

## 🎯 Use Cases

### 🛍️ **Shopping**
*"Find parking near Phoenix Mall Mumbai"*
- Locate parking before reaching the mall
- Compare prices and availability
- Save time and fuel

### 🏟️ **Tourism**
*"Parking near India Gate Delhi"*
- Plan your sightseeing efficiently
- Know pricing upfront
- Navigate directly to spots

### 🏢 **Business**
*"Parking in Whitefield Bangalore"*
- Find parking for meetings
- Book ahead mentally
- Arrive stress-free

### 🎉 **Events**
*"24/7 parking near Bandra"*
- Late-night event parking
- Secure, covered options
- Handicap accessibility

---

## 🌍 Supported Cities

ParkGenie currently supports **30+ major Indian cities** including:

**Metro Cities:** Mumbai, Delhi, Bangalore, Chennai, Hyderabad, Kolkata  
**Tier 1:** Pune, Ahmedabad, Jaipur, Surat, Lucknow, Kanpur  
**Tier 2:** Nagpur, Indore, Thane, Bhopal, Visakhapatnam, Vadodara  
**Tourist:** Agra, Varanasi, Srinagar, Amritsar, Jodhpur, Kochi  
**And More:** Ludhiana, Nashik, Faridabad, Meerut, Rajkot, Ghaziabad

*Global cities can be searched using the map interface!*

---

## 💡 Usage Examples

### **Example 1: Voice-like Natural Search**
```
User: "I need parking near Connaught Place"
ParkGenie: "I found 7 parking spots near Delhi. Here are the best options:"
```

### **Example 2: Current Location**
```
User: Clicks "Locate Me" button
ParkGenie: Finds GPS coordinates
ParkGenie: "I found 5 parking spots near your current location."
```

### **Example 3: Specific Requirements**
```
User: "Cheapest parking in Bangalore"
ParkGenie: Shows results sorted by price
```

### **Example 4: Map Exploration**
```
User: Pans map to new area
User: Clicks "Search This Area"
ParkGenie: Shows parking in visible map bounds
```

---

## 🎮 Interactive Demo

### **Try These Commands:**
- 📍 "Parking near me"
- 🏭 "Find parking in Mumbai"
- 💰 "Cheapest parking in Delhi"
- 🔒 "24/7 parking in Bangalore"
- 🚗 "EV charging parking in Pune"
- ♿ "Handicap parking in Chennai"

---

## 📈 Future Enhancements

### **Planned Features**
- [ ] Real-time parking availability API integration
- [ ] User authentication and booking system
- [ ] Payment gateway integration
- [ ] Reviews and ratings
- [ ] Parking history and favorites
- [ ] Push notifications for booking reminders
- [ ] Multi-language support
- [ ] Dark mode
- [ ] PWA (Progressive Web App) support
- [ ] Voice search integration

---

## 👥 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### **Ideas for Contributions:**
- Add more cities to the database
- Improve chatbot intelligence
- Add new parking features
- Enhance mobile responsiveness
- Create unit tests
- Improve documentation

---

## 🐛 Known Issues

- Parking data is currently simulated (not real-time)
- Geolocation requires HTTPS in production
- Some browsers may block location access
- Mobile keyboard may hide chat input (scroll down)

---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

---

## 📧 Contact

**Susmitha Pasumarthi**  
👤 GitHub: [@susmithapasumarthi349](https://github.com/susmithapasumarthi349)  
💾 Repository: [Park-Genie](https://github.com/susmithapasumarthi349/Park-Genie)

---

## 🌟 Star This Repository!

If you find ParkGenie useful, please consider starring this repository!  
⭐ Stars help others discover the project and motivate continued development.

---

## 📸 Screenshots

### **Main Interface**
- Split-screen design with chatbot on left, map on right
- Gradient background with modern UI elements
- Real-time parking cards with status indicators

### **Chat Interface**
- Conversational bot with helpful suggestions
- Smooth message animations
- Quick-action buttons for common queries

### **Map View**
- Interactive markers with popup details
- Zoom/pan controls
- Current location indicator

---

<div align="center">

**Built with ❤️ by Susmitha Pasumarthi**

**Making parking hassle-free, one spot at a time!**

[Report Bug](https://github.com/susmithapasumarthi349/Park-Genie/issues) • [Request Feature](https://github.com/susmithapasumarthi349/Park-Genie/issues)

</div>
