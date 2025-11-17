# Parking_Finder
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ParkGenie - Global Parking Finder</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
    <style>
        :root {
            --primary: #3a86ff;
            --secondary: #2667cc;
            --accent: #8338ec;
            --light: #f8f9fa;
            --dark: #212529;
            --success: #4cc9f0;
            --warning: #f8961e;
            --danger: #f94144;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--light);
            color: var(--dark);
        }
        
        .container {
            display: grid;
            grid-template-columns: 1fr 1.5fr;
            height: 100vh;
        }
        
        .left-panel {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2rem;
            display: flex;
            flex-direction: column;
            position: relative;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
        }
        
        .logo-icon {
            margin-right: 0.5rem;
        }
        
        .logo span {
            color: var(--accent);
        }
        
        .chat-container {
            flex-grow: 1;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            backdrop-filter: blur(5px);
        }
        
        .chat-header {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
        }
        
        .chat-header-icon {
            margin-right: 0.5rem;
        }
        
        .chat-messages {
            flex-grow: 1;
            overflow-y: auto;
            margin-bottom: 1rem;
        }
        
        .message {
            margin-bottom: 1rem;
            padding: 0.8rem 1rem;
            border-radius: 12px;
            max-width: 80%;
            line-height: 1.4;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .bot-message {
            background: rgba(255, 255, 255, 0.2);
            border-top-left-radius: 5px;
            align-self: flex-start;
        }
        
        .user-message {
            background: var(--accent);
            border-top-right-radius: 5px;
            align-self: flex-end;
        }
        
        .chat-input {
            display: flex;
        }
        
        .chat-input input {
            flex-grow: 1;
            padding: 0.8rem 1rem;
            border: none;
            border-radius: 25px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            outline: none;
            font-family: 'Poppins', sans-serif;
        }
        
        .chat-input input::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }
        
        .chat-input button {
            background: var(--accent);
            color: white;
            border: none;
            border-radius: 50%;
            width: 45px;
            height: 45px;
            margin-left: 0.5rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 0.2s;
        }
        
        .chat-input button:hover {
            transform: scale(1.05);
        }
        
        .right-panel {
            display: flex;
            flex-direction: column;
        }
        
        .map-container {
            flex-grow: 1;
            height: 60%;
            position: relative;
        }
        
        #parking-map {
            height: 100%;
            width: 100%;
        }
        
        .map-controls {
            position: absolute;
            top: 10px;
            right: 10px;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: 5px;
        }
        
        .map-control {
            background: white;
            border: none;
            border-radius: 5px;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        
        .parking-list {
            height: 40%;
            padding: 1.5rem;
            overflow-y: auto;
            background: white;
        }
        
        .parking-card {
            background: white;
            border-radius: 10px;
            padding: 1rem;
            margin-bottom: 1rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: center;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
        }
        
        .parking-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .parking-icon {
            background: var(--primary);
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 1rem;
            flex-shrink: 0;
        }
        
        .parking-info {
            flex-grow: 1;
        }
        
        .parking-name {
            font-weight: 600;
            margin-bottom: 0.3rem;
        }
        
        .parking-address {
            font-size: 0.8rem;
            color: #666;
            margin-bottom: 0.3rem;
        }
        
        .parking-availability {
            display: flex;
            align-items: center;
            font-size: 0.9rem;
        }
        
        .availability-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin-right: 0.5rem;
        }
        
        .available {
            background: var(--success);
        }
        
        .limited {
            background: var(--warning);
        }
        
        .full {
            background: var(--danger);
        }
        
        .parking-distance {
            font-size: 0.8rem;
            color: var(--accent);
        }
        
        .parking-action {
            margin-left: 1rem;
        }
        
        .parking-action button {
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 5px;
            padding: 0.5rem 1rem;
            cursor: pointer;
            font-size: 0.8rem;
            transition: background 0.2s;
        }
        
        .parking-action button:hover {
            background: var(--secondary);
        }
        
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: white;
            animation: spin 1s ease-in-out infinite;
            margin-left: 10px;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .suggestions {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }
        
        .suggestion {
            background: rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            padding: 5px 12px;
            font-size: 0.8rem;
            cursor: pointer;
            transition: background 0.2s;
        }
        
        .suggestion:hover {
            background: rgba(255, 255, 255, 0.3);
        }
        
        .parking-marker {
            background: var(--primary);
            color: white;
            padding: 3px 6px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
            border: 2px solid white;
        }
        
        .current-location-marker {
            background: var(--accent);
            color: white;
            padding: 3px 6px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
            border: 2px solid white;
        }
        
        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
                height: auto;
            }
            
            .left-panel {
                height: 50vh;
            }
            
            .right-panel {
                height: 50vh;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left-panel">
            <div class="logo">
                <svg class="logo-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21V5a2 2 0 0 0-2-2H7a2 2 0 0 0-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 8v-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v4"></path></svg>
                Park<span>Genie</span>
            </div>
            <div class="chat-container">
                <div class="chat-header">
                    <svg class="chat-header-icon" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></svg>
                    Parking Assistant
                </div>
                <div class="chat-messages" id="chat-messages">
                    <div class="message bot-message">
                        Hello! I'm ParkGenie, your smart parking assistant. I can help you find available parking spots anywhere in the world, with special focus on India. Where would you like to park today?
                        <div class="suggestions">
                            <div class="suggestion" onclick="sendSuggestion('Show parking in Mumbai')">Mumbai</div>
                            <div class="suggestion" onclick="sendSuggestion('Find parking in Delhi')">Delhi</div>
                            <div class="suggestion" onclick="sendSuggestion('Parking near me')">Near Me</div>
                            <div class="suggestion" onclick="sendSuggestion('Cheapest parking in Bangalore')">Bangalore</div>
                        </div>
                    </div>
                </div>
                <div class="chat-input">
                    <input type="text" id="user-input" placeholder="Ask about parking in any location..." autocomplete="off" onkeypress="handleKeyPress(event)">
                    <button id="send-button" onclick="handleUserInput()">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
                    </button>
                </div>
            </div>
        </div>
        <div class="right-panel">
            <div class="map-container">
                <div id="parking-map"></div>
                <div class="map-controls">
                    <button class="map-control" id="locate-me" title="Locate Me" onclick="locateUser()">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path><circle cx="12" cy="10" r="3"></circle></svg>
                    </button>
                    <button class="map-control" id="search-area" title="Search This Area" onclick="searchCurrentArea()">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
                    </button>
                </div>
            </div>
            <div class="parking-list" id="parking-list">
                <div style="text-align: center; padding: 2rem; color: #666;">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21V5a2 2 0 0 0-2-2H7a2 2 0 0 0-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 8v-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v4"></path></svg>
                    <p>Search for parking locations using the chat or map</p>
                </div>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    <script>
        // Initialize the map with a view centered on India
        const map = L.map('parking-map').setView([20.5937, 78.9629], 5);
        
        // Add OpenStreetMap tiles
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);
        
        // Parking data storage
        let parkingData = [];
        let markers = [];
        let currentLocationMarker = null;
        let currentLocation = null;
        
        // Chatbot functionality
        const chatMessages = document.getElementById('chat-messages');
        const userInput = document.getElementById('user-input');
        const sendButton = document.getElementById('send-button');
        const parkingList = document.getElementById('parking-list');
        const locateMeBtn = document.getElementById('locate-me');
        const searchAreaBtn = document.getElementById('search-area');
        
        // Add message to chat
        function addMessage(message, isUser, suggestions = []) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${isUser ? 'user-message' : 'bot-message'}`;
            messageDiv.textContent = message;
            
            if (suggestions.length > 0 && !isUser) {
                const suggestionsDiv = document.createElement('div');
                suggestionsDiv.className = 'suggestions';
                
                suggestions.forEach(suggestion => {
                    const suggestionDiv = document.createElement('div');
                    suggestionDiv.className = 'suggestion';
                    suggestionDiv.textContent = suggestion;
                    suggestionDiv.onclick = () => sendSuggestion(suggestion);
                    suggestionsDiv.appendChild(suggestionDiv);
                });
                
                messageDiv.appendChild(suggestionsDiv);
            }
            
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        // Send suggestion as user message
        function sendSuggestion(suggestion) {
            userInput.value = suggestion;
            handleUserInput();
        }
        
        // Show loading indicator in chat
        function showLoading() {
            const loadingDiv = document.createElement('div');
            loadingDiv.className = 'message bot-message';
            loadingDiv.id = 'loading-message';
            loadingDiv.innerHTML = 'Searching for parking... <span class="loading"></span>';
            chatMessages.appendChild(loadingDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        // Hide loading indicator
        function hideLoading() {
            const loadingDiv = document.getElementById('loading-message');
            if (loadingDiv) {
                loadingDiv.remove();
            }
        }
        
        // Handle user input
        function handleUserInput() {
            const input = userInput.value.trim();
            if (!input) return;
            
            addMessage(input, true);
            userInput.value = '';
            
            // Process the input
            processUserQuery(input);
        }
        
        // Handle Enter key press
        function handleKeyPress(event) {
            if (event.key === 'Enter') {
                handleUserInput();
            }
        }
        
        // Process user query
        function processUserQuery(query) {
            showLoading();
            
            // Check for common queries
            if (query.toLowerCase().includes('near me') || query.toLowerCase().includes('current location')) {
                if (currentLocation) {
                    findParkingNearLocation(currentLocation, 'your current location');
                } else {
                    setTimeout(() => {
                        hideLoading();
                        addMessage("I don't have your location yet. Please click the 'Locate Me' button or tell me a specific location to search.", false, 
                            ['Locate Me', 'Parking in Mumbai', 'Parking in Delhi']);
                    }, 1000);
                }
            } 
            else if (query.toLowerCase().includes('mumbai')) {
                setTimeout(() => {
                    const mumbaiCoords = { lat: 19.0760, lng: 72.8777 };
                    findParkingNearLocation(mumbaiCoords, 'Mumbai');
                }, 1000);
            }
            else if (query.toLowerCase().includes('delhi')) {
                setTimeout(() => {
                    const delhiCoords = { lat: 28.7041, lng: 77.1025 };
                    findParkingNearLocation(delhiCoords, 'Delhi');
                }, 1000);
            }
            else if (query.toLowerCase().includes('bangalore') || query.toLowerCase().includes('bengaluru')) {
                setTimeout(() => {
                    const bangaloreCoords = { lat: 12.9716, lng: 77.5946 };
                    findParkingNearLocation(bangaloreCoords, 'Bangalore');
                }, 1000);
            }
            else if (query.toLowerCase().includes('chennai')) {
                setTimeout(() => {
                    const chennaiCoords = { lat: 13.0827, lng: 80.2707 };
                    findParkingNearLocation(chennaiCoords, 'Chennai');
                }, 1000);
            }
            else if (query.toLowerCase().includes('hyderabad')) {
                setTimeout(() => {
                    const hyderabadCoords = { lat: 17.3850, lng: 78.4867 };
                    findParkingNearLocation(hyderabadCoords, 'Hyderabad');
                }, 1000);
            }
            else if (query.toLowerCase().includes('kolkata')) {
                setTimeout(() => {
                    const kolkataCoords = { lat: 22.5726, lng: 88.3639 };
                    findParkingNearLocation(kolkataCoords, 'Kolkata');
                }, 1000);
            }
            else {
                // For other queries, try to geocode the location
                geocodeLocation(query);
            }
        }
        
        // Find parking near a specific location
        function findParkingNearLocation(coords, locationName) {
            // Clear previous markers
            clearMarkers();
            
            // Center map on the location
            map.setView([coords.lat, coords.lng], 14);
            
            // Add current location marker if it's the user's location
            if (locationName === 'your current location') {
                if (currentLocationMarker) {
                    map.removeLayer(currentLocationMarker);
                }
                currentLocationMarker = L.marker([coords.lat, coords.lng], {
                    icon: L.divIcon({
                        className: 'current-location-marker',
                        html: '📍',
                        iconSize: [30, 30]
                    })
                }).addTo(map);
            }
            
            // Generate mock parking data
            const mockData = generateMockParkingData(coords);
            parkingData = mockData;
            
            // Display results
            setTimeout(() => {
                hideLoading();
                addMessage(`I found ${mockData.length} parking spots near ${locationName}. Here are the best options:`, false);
                displayParkingResults(mockData);
                
                // Add suggestions based on location
                if (locationName === 'your current location') {
                    addMessage("What would you like to do next?", false, 
                        ['Show cheapest parking', 'Show nearest parking', 'Search another area']);
                } else {
                    addMessage(`Looking for parking in other cities?`, false, 
                        ['Parking in Mumbai', 'Parking in Delhi', 'Parking in Bangalore', 'Parking near me']);
                }
            }, 1500);
        }
        
        // Generate mock parking data based on location
        function generateMockParkingData(coords) {
            const baseLat = coords.lat;
            const baseLng = coords.lng;
            const count = Math.floor(Math.random() * 8) + 3; // 3-10 parking spots
            
            const data = [];
            const parkingTypes = ['Multi-level', 'Street', 'Mall', 'Underground', 'Open Lot', 'Valet'];
            const availabilityStatus = ['available', 'limited', 'full'];
            const statusText = {
                'available': 'Available',
                'limited': 'Limited',
                'full': 'Full'
            };
            
            for (let i = 0; i < count; i++) {
                // Generate random offset from base location (0.01 to 0.05 degrees)
                const latOffset = (Math.random() * 0.04 - 0.02);
                const lngOffset = (Math.random() * 0.04 - 0.02);
                
                const status = availabilityStatus[Math.floor(Math.random() * availabilityStatus.length)];
                const price = (Math.random() * 100 + 20).toFixed(2);
                const distance = (Math.random() * 2 + 0.1).toFixed(1);
                
                data.push({
                    id: i + 1,
                    name: `${parkingTypes[i % parkingTypes.length]} Parking ${i + 1}`,
                    address: `${Math.floor(Math.random() * 100) + 1} ${['Main', 'Park', 'Market', 'MG', 'Church'][i % 5]} ${['St', 'Rd', 'Ave', 'Lane'][i % 4]}`,
                    location: {
                        lat: baseLat + latOffset,
                        lng: baseLng + lngOffset
                    },
                    status: status,
                    statusText: statusText[status],
                    price: price,
                    distance: distance,
                    features: ['24/7', 'Security', 'EV Charging', 'Covered', 'Handicap'][i % 5]
                });
            }
            
            // Sort by distance
            data.sort((a, b) => parseFloat(a.distance) - parseFloat(b.distance));
            
            return data;
        }
        
        // Display parking results on map and list
        function displayParkingResults(data) {
            // Clear previous results
            parkingList.innerHTML = '';
            
            if (data.length === 0) {
                parkingList.innerHTML = '<div style="text-align: center; padding: 2rem; color: #666;">No parking spots found in this area. Try another location.</div>';
                return;
            }
            
            // Add markers to map and create list items
            data.forEach((parking, index) => {
                // Add marker
                const marker = L.marker([parking.location.lat, parking.location.lng], {
                    icon: L.divIcon({
                        className: 'parking-marker',
                        html: '🅿️',
                        iconSize: [30, 30]
                    })
                }).addTo(map);
                
                marker.bindPopup(`
                    <b>${parking.name}</b><br>
                    ${parking.address}<br>
                    Status: ${parking.statusText}<br>
                    Price: ₹${parking.price}/hr<br>
                    Distance: ${parking.distance} km<br>
                    Features: ${parking.features}
                `);
                
                markers.push(marker);
                
                // Create parking card
                const card = document.createElement('div');
                card.className = 'parking-card';
                card.onclick = () => {
                    map.setView([parking.location.lat, parking.location.lng], 16);
                    marker.openPopup();
                };
                
                card.innerHTML = `
                    <div class="parking-icon">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21V5a2 2 0 0 0-2-2H7a2 2 0 0 0-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 8v-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v4"></path></svg>
                    </div>
                    <div class="parking-info">
                        <div class="parking-name">${parking.name}</div>
                        <div class="parking-address">${parking.address}</div>
                        <div class="parking-availability">
                            <span class="availability-dot ${parking.status}"></span>
                            ${parking.statusText} • ₹${parking.price}/hr
                        </div>
                        <div class="parking-distance">${parking.distance} km away</div>
                    </div>
                    <div class="parking-action">
                        <button onclick="event.stopPropagation();navigateToParking(${parking.location.lat},${parking.location.lng})">Directions</button>
                    </div>
                `;
                
                parkingList.appendChild(card);
            });
        }
        
        // Clear all markers from map
        function clearMarkers() {
            markers.forEach(marker => map.removeLayer(marker));
            markers = [];
        }
        
        // Geocode location from text query
        function geocodeLocation(query) {
            // In a real app, you would use a geocoding service like Nominatim or Google Maps Geocoding API
            // For this demo, we'll use a simple mock with major Indian cities
            
            const cityMapping = {
                'mumbai': { lat: 19.0760, lng: 72.8777, name: 'Mumbai' },
                'delhi': { lat: 28.7041, lng: 77.1025, name: 'Delhi' },
                'bangalore': { lat: 12.9716, lng: 77.5946, name: 'Bangalore' },
                'bengaluru': { lat: 12.9716, lng: 77.5946, name: 'Bangalore' },
                'chennai': { lat: 13.0827, lng: 80.2707, name: 'Chennai' },
                'hyderabad': { lat: 17.3850, lng: 78.4867, name: 'Hyderabad' },
                'kolkata': { lat: 22.5726, lng: 88.3639, name: 'Kolkata' },
                'pune': { lat: 18.5204, lng: 73.8567, name: 'Pune' },
                'ahmedabad': { lat: 23.0225, lng: 72.5714, name: 'Ahmedabad' },
                'jaipur': { lat: 26.9124, lng: 75.7873, name: 'Jaipur' },
                'surat': { lat: 21.1702, lng: 72.8311, name: 'Surat' },
                'lucknow': { lat: 26.8467, lng: 80.9462, name: 'Lucknow' },
                'kanpur': { lat: 26.4499, lng: 80.3319, name: 'Kanpur' },
                'nagpur': { lat: 21.1458, lng: 79.0882, name: 'Nagpur' },
                'indore': { lat: 22.7196, lng: 75.8577, name: 'Indore' },
                'thane': { lat: 19.2183, lng: 72.9781, name: 'Thane' },
                'bhopal': { lat: 23.2599, lng: 77.4126, name: 'Bhopal' },
                'visakhapatnam': { lat: 17.6868, lng: 83.2185, name: 'Visakhapatnam' },
                'patna': { lat: 25.5941, lng: 85.1376, name: 'Patna' },
                'vadodara': { lat: 22.3072, lng: 73.1812, name: 'Vadodara' },
                'ghaziabad': { lat: 28.6692, lng: 77.4538, name: 'Ghaziabad' },
                'ludhiana': { lat: 30.9010, lng: 75.8573, name: 'Ludhiana' },
                'agra': { lat: 27.1767, lng: 78.0081, name: 'Agra' },
                'nashik': { lat: 20.0059, lng: 73.7910, name: 'Nashik' },
                'faridabad': { lat: 28.4089, lng: 77.3178, name: 'Faridabad' },
                'meerut': { lat: 28.6139, lng: 77.2090, name: 'Meerut' },
                'rajkot': { lat: 22.3039, lng: 70.8022, name: 'Rajkot' },
                'varanasi': { lat: 25.3176, lng: 82.9739, name: 'Varanasi' },
                'srinagar': { lat: 34.0837, lng: 74.7973, name: 'Srinagar' },
                'amritsar': { lat: 31.6340, lng: 74.8723, name: 'Amritsar' },
                'jodhpur': { lat: 26.2389, lng: 73.0243, name: 'Jodhpur' },
                'kochi': { lat: 9.9312, lng: 76.2673, name: 'Kochi' }
            };
            
            const normalizedQuery = query.toLowerCase().trim();
            let found = false;
            
            // Check if query matches any known city
            for (const [city, coords] of Object.entries(cityMapping)) {
                if (normalizedQuery.includes(city)) {
                    setTimeout(() => {
                        hideLoading();
                        findParkingNearLocation(coords, coords.name);
                    }, 1000);
                    found = true;
                    break;
                }
            }
            
            if (!found) {
                setTimeout(() => {
                    hideLoading();
                    addMessage(`I couldn't find parking information for "${query}". Try specifying a city name or use "near me" for your current location.`, false, 
                        ['Parking near me', 'Parking in Mumbai', 'Parking in Delhi', 'Parking in Bangalore']);
                }, 1000);
            }
        }
        
        // Locate user
        function locateUser() {
            showLoading();
            
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        currentLocation = {
                            lat: position.coords.latitude,
                            lng: position.coords.longitude
                        };
                        
                        setTimeout(() => {
                            hideLoading();
                            findParkingNearLocation(currentLocation, 'your current location');
                        }, 1000);
                    },
                    (error) => {
                        setTimeout(() => {
                            hideLoading();
                            addMessage("I couldn't access your location. Please make sure location services are enabled or specify a location.", false, 
                                ['Parking in Mumbai', 'Parking in Delhi', 'Parking in Bangalore']);
                        }, 1000);
                    }
                );
            } else {
                setTimeout(() => {
                    hideLoading();
                    addMessage("Geolocation is not supported by your browser. Please specify a location.", false, 
                        ['Parking in Mumbai', 'Parking in Delhi', 'Parking in Bangalore']);
                }, 1000);
            }
        }
        
        // Search current map area
        function searchCurrentArea() {
            const center = map.getCenter();
            findParkingNearLocation({ lat: center.lat, lng: center.lng }, 'this area');
        }
        
        // Navigate to parking (opens in Google Maps)
        function navigateToParking(lat, lng) {
            window.open(`https://www.google.com/maps/dir/?api=1&destination=${lat},${lng}&travelmode=driving`);
        }
        
                // Initialize the app
        document.addEventListener('DOMContentLoaded', () => {
            // Focus the input field when page loads
            userInput.focus();
            
            // Add event listeners for better UX
            sendButton.addEventListener('click', handleUserInput);
            userInput.addEventListener('keypress', handleKeyPress);
            
            // Set up map controls
            locateMeBtn.addEventListener('click', locateUser);
            searchAreaBtn.addEventListener('click', searchCurrentArea);
            
            // Welcome message with slight delay for better feel
            setTimeout(() => {
                addMessage("You can ask me about parking in any city or click 'Locate Me' to find parking near your current location.", false, [
                    'Parking near me',
                    'Cheapest parking in Mumbai',
                    'Parking in Delhi near metro',
                    '24/7 parking in Bangalore'
                ]);
            }, 1500);
        });
    </script>
</body>
</html>
