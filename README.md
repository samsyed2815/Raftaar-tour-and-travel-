from zipfile import ZipFile
import os

# Create the folder structure
os.makedirs("/mnt/data/raftaar-tour-travel/images", exist_ok=True)

# HTML content
html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raftaar Tour and Travel</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Raftaar Tour and Travel</h1>
        <p>Your journey begins with us</p>
    </header>

    <section id="services">
        <h2>Our Services</h2>
        <div class="service">Flight Booking</div>
        <div class="service">Hotel Reservation</div>
        <div class="service">Customized Packages</div>
        <div class="service">Car Rentals</div>
    </section>

    <section id="packages">
        <h2>Popular Packages</h2>
        <div class="package">Goa Beach Tour - ₹12,999</div>
        <div class="package">Himalayan Adventure - ₹18,499</div>
    </section>

    <section id="booking">
        <h2>Book Your Trip</h2>
        <form action="https://formsubmit.co/your-email@example.com" method="POST">
            <input type="text" name="name" placeholder="Your Name" required>
            <input type="email" name="email" placeholder="Your Email" required>
            <input type="tel" name="phone" placeholder="Your Phone Number" required>
            <input type="text" name="package" placeholder="Interested Package" required>
            <button type="submit">Book Now</button>
        </form>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <p>Email: contact@raftaartours.com</p>
        <p>Phone: +91 98765 43210</p>
        <div class="map-container">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18..." width="100%" height="300" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
        </div>
    </section>

    <a href="https://wa.me/919876543210" class="whatsapp-button" target="_blank">Chat with Us</a>
</body>
</html>
"""

# CSS content
css_content = """
body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    padding: 0;
    line-height: 1.6;
    background: #f9f9f9;
}
header {
    background: url('images/banner.jpg') no-repeat center center/cover;
    color: white;
    height: 90vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
}
section {
    padding: 40px 20px;
}
h2 {
    color: #007BFF;
    text-align: center;
    margin-bottom: 20px;
}
.service, .package {
    background: white;
    margin: 10px auto;
    padding: 15px;
    border-radius: 10px;
    max-width: 500px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
}
.service:hover, .package:hover {
    transform: scale(1.05);
}
form {
    max-width: 400px;
    margin: auto;
    display: flex;
    flex-direction: column;
}
input, button {
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ddd;
    border-radius: 5px;
}
button {
    background: #007BFF;
    color: white;
    border: none;
    cursor: pointer;
}
button:hover {
    background: #0056b3;
}
.map-container {
    margin-top: 20px;
}
.whatsapp-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #25D366;
    color: white;
    padding: 10px 20px;
    border-radius: 50px;
    text-decoration: none;
    font-weight: bold;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}
"""

# Sample image placeholder (empty file, normally it would be a real image)
open("/mnt/data/raftaar-tour-travel/images/banner.jpg", 'a').close()

# Write HTML
with open("/mnt/data/raftaar-tour-travel/index.html", "w", encoding="utf-8") as f:
    f.write(html_content)

# Write CSS
with open("/mnt/data/raftaar-tour-travel/style.css", "w", encoding="utf-8") as f:
    f.write(css_content)

# Create ZIP
zip_path = "/mnt/data/raftaar-tour-travel.zip"
with ZipFile(zip_path, 'w') as zipf:
    for root, dirs, files in os.walk("/mnt/data/raftaar-tour-travel"):
        for file in files:
            zipf.write(os.path.join(root, file), os.path.relpath(os.path.join(root, file), "/mnt/data/raftaar-tour-travel"))

zip_path
