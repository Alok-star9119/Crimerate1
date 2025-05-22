<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Crime Sensitive Zone Notifier</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
  body {
    font-family: 'Roboto', sans-serif;
    background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 99%, #fad0c4 100%);
    margin: 0;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #5a1a01;
    min-height: 100vh;
    justify-content: center;
    text-align: center;
  }
  h1 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: #b00020;
    text-shadow: 0 0 5px #ff6f91;
  }
  #status {
    font-weight: 500;
    font-size: 1.25rem;
    margin-bottom: 1.5rem;
  }
  #zoneStatus {
    font-size: 1.5rem;
    font-weight: 700;
    margin: 1rem 0;
    color: #b00020;
  }
  #map {
    margin-top: 1rem;
    max-width: 400px;
    max-height: 300px;
    border-radius: 15px;
    border: 3px solid #b00020;
  }
  #instructions {
    margin-top: 2rem;
    font-size: 1rem;
    color: #660000;
    max-width: 400px;
    line-height: 1.4;
  }
</style>
</head>
<body>
  <h1>Crime Sensitive Zone Notifier</h1>
  <div id="status">Requesting location and notification permissions...</div>
  <div id="zoneStatus"></div>
  <canvas id="map" width="400" height="300" style="display:none;"></canvas>
  <div id="instructions">
    <p>Allow location and notification permissions to receive alerts if you enter a crime-sensitive zone.</p>
    <p>This is a demo app simulating zones.</p>
  </div>

<script>
  // Define actual crime-sensitive zones (latitude, longitude, radius in meters)
  const crimeZones = [
    {name: 'Delhi Crime Zone', lat: 28.6139, lon: 77.2090, radius: 1000}, // Example: Central Delhi
    {name: 'Bokaro Crime Zone', lat: 23.7648, lon: 86.1519, radius: 800}, // Example: Bokaro Steel City
    // Add more zones as needed
  ];

  let insideZone = false;

  function toRadians(deg) {
    return deg * Math.PI / 180;
  }

  // Haversine formula to calculate distance between two lat/lon points in meters
  function distanceMeters(lat1, lon1, lat2, lon2) {
    const earthRadius = 6371000; // meters
    const dLat = toRadians(lat2 - lat1);
    const dLon = toRadians(lon2 - lon1);
    const a = Math.sin(dLat/2) * Math.sin(dLat/2) +
              Math.cos(toRadians(lat1)) * Math.cos(toRadians(lat2)) *
              Math.sin(dLon/2) * Math.sin(dLon/2);
    const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
    return earthRadius * c;
  }

  function checkZones(position) {
    const lat = position.coords.latitude;
    const lon = position.coords.longitude;

    // Check each zone
    for (const zone of crimeZones) {
      const dist = distanceMeters(lat, lon, zone.lat, zone.lon);
      if (dist <= zone.radius) {
        return zone.name;
      }
    }
    return null;
  }

  function sendNotification(zoneName) {
    if (!("Notification" in window)) {
      alert("This browser does not support desktop notifications.");
      return;
    }
    if (Notification.permission === "granted") {
      const notification = new Notification("Crime Sensitive Zone Alert", {
        body: `You are in ${zoneName}. Be careful!`,
        icon: "https://cdn-icons-png.flaticon.com/512/616/616490.png"
      });
    }
  }

  function updateStatus(msg) {
    document.getElementById('status').textContent = msg;
  }

  function updateZoneStatus(msg, isWarning) {
    const zoneStatus = document.getElementById('zoneStatus');
    zoneStatus.textContent = msg;
    zoneStatus.style.color = isWarning ? '#b00020' : '#006400';
  }

  function locationSuccess(position) {
    updateStatus(`Your current location: Lat ${position.coords.latitude.toFixed(5)}, Lon ${position.coords.longitude.toFixed(5)}`);
    const zoneName = checkZones(position);

    if (zoneName) {
      if (!insideZone) {
        // Only notify when newly entered zone
        insideZone = true;
        updateZoneStatus(`⚠️ You are in a crime-sensitive zone: ${zoneName}`, true);
        sendNotification(zoneName);
      }
    } else {
      if (insideZone) {
        insideZone = false;
      }
      updateZoneStatus(`You are in a safe zone.`, false);
    }
  }

  function locationError(err) {
    updateStatus(`Error getting location: ${err.message}`);
  }

  function requestPermissions() {
    if (!("Notification" in window)) {
      updateStatus("Your browser does not support notifications.");
      return;
    }

    Notification.requestPermission().then(function(permission) {
      if (permission !== "granted") {
        updateStatus("Please allow notifications to receive alerts!");
      } else {
        updateStatus("Waiting for location updates...");
      }
    });

    if ("geolocation" in navigator) {
      navigator.geolocation.watchPosition(locationSuccess, locationError, {
        enableHighAccuracy: true,
        maximumAge: 10000,
        timeout: 5000
      });
    } else {
      updateStatus("Geolocation is not supported by your browser.");
    }
  }

  // Start tracking after page loads
  window.onload = function() {
    requestPermissions();
  };
</script>
</body>
</html>
