# PMCLTrial
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Location Tracker</title>
</head>
<body>
    <h1>Location Tracker</h1>
    <button id="getLocation">Get Location</button>

    <script>
        document.getElementById('getLocation').addEventListener('click', getLocation);

        function getLocation() {
            if ('geolocation' in navigator) {
                navigator.geolocation.getCurrentPosition(handleSuccess, handleError);
            } else {
                alert('Geolocation is not supported by your browser.');
            }
        }

        function handleSuccess(position) {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;
            const timestamp = new Date().toLocaleString();

            // Now, you can send the location and timestamp to a server.
            sendLocationData(latitude, longitude, timestamp);
        }

        function handleError(error) {
            console.error('Error getting location:', error.message);
        }

        function sendLocationData(latitude, longitude, timestamp) {
            // You would send this data to your server using a method like AJAX or fetch.
            // For simplicity, this example does not include the server interaction.
            console.log('Location:', latitude, longitude);
            console.log('Timestamp:', timestamp);
        }
