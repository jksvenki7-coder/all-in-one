# all-in-one/index.html (main home page with navigation)
/food/index.html (food category with gallery and form)
/pharmacy/index.html (pharmacy category with gallery and form)
/images/food1.jpg to food10.jpg (sample images for food)
/images/pharmacy1.jpg to pharmacy10.jpg (sample images for pharmacy)<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>All-in-One Delivery Service</title>
    <style>
        body { font-family: Arial,sans-serif; margin:0; background: #f9fbfd; color:#333;}
        header { background: #2196f3; color:#fff; padding: 15px 0; text-align:center;}
        nav { display:flex; justify-content:center; gap: 20px; margin-top:14px; }
        nav button { background:#87ceeb; border:none; padding: 10px 25px; border-radius: 6px; color:#fff; font-weight:bold; cursor:pointer;}
        nav button:hover { background:#588fc7;}
        main { max-width: 1100px; margin: 30px auto; text-align:center; }
    </style>
    <script>
        function goToPage(page) {
            window.location.href = page;
        }
        function openCamera() {
            alert("Camera opening - mobile only feature.");
        }
        function openGoogleMaps() {
            window.open("https://maps.google.com", "_blank");
        }
    </script>
</head>
<body>
    <header>
        <h1>All-in-One Delivery Service</h1>
        <nav>
            <button onclick="goToPage('food/index.html')">Food</button>
            <button onclick="goToPage('pharmacy/index.html')">Pharmacy</button>
            <button onclick="openCamera()">Camera</button>
            <button onclick="openGoogleMaps()">Google Maps</button>
        </nav>
    </header>
    <main>
        <h2>Welcome! Select a category to order products</h2>
        <p>Fast and reliable delivery at your door step.</p>
    </main>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Food Delivery</title>
    <style>
        body { font-family: Arial, sans-serif; background:#f0fbff; margin:0; padding:0;}
        header { background:#2196f3; color:#fff; padding: 15px; text-align:center;}
        nav { margin: 12px; text-align:center;}
        nav button { background:#87ceeb; border:none; padding: 10px 20px; margin:2px; border-radius:6px; color:#fff; font-weight:bold; cursor:pointer;}
        nav button:hover { background:#4444aa;}
        .gallery {
            display:grid;
            grid-template-columns: repeat(auto-fit, minmax(150px,1fr));
            gap: 14px;
            max-width: 900px;
            margin: 24px auto 38px auto;
        }
        .gallery img {
            width: 100%;
            height: 140px;
            object-fit: cover;
            border-radius: 10px;
            box-shadow: 0 1px 5px #a2d4f7;
        }
        form {
            max-width: 450px;
            background:#fff;
            margin: 0 auto 40px auto;
            padding: 24px 20px;
            border-radius: 14px;
            box-shadow: 0 2px 8px #d8ecff;
        }
        label {
            display: block;
            margin-bottom: 6px;
            color: #222;
            font-weight: bold;
        }
        input, textarea {
            width: 100%;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #99bbdd;
            margin-bottom: 18px;
            font-size: 16px;
            font-family: Arial, sans-serif;
        }
        button {
            width: 100%;
            background: #2196f3;
            color: white;
            font-weight: bold;
            padding: 14px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 18px;
            transition: background 0.2s;
        }
        button:hover {
            background: #0b7dda;
        }
        .hint {
            font-size: 12px;
            color: #555;
            margin-top: -12px;
            margin-bottom: 14px;
            padding-left: 4px;
        }
    </style>
    <script>
        function goBack() {
            window.location.href = '../index.html';
        }
        function validatePhone(input) {
            const val = input.value.trim();
            const pattern1 = /^[6-9]\d{9}$/;
            const pattern2 = /^\+91[6-9]\d{9}$/;
            if (pattern1.test(val) || pattern2.test(val)) {
                input.setCustomValidity('');
            } else {
                input.setCustomValidity('Enter valid 10 digit or +91 number');
            }
        }
        function sendOrder(event) {
            event.preventDefault();
            const name = document.getElementById('name').value.trim();
            const phone = document.getElementById('phone').value.trim();
            const item = document.getElementById('item').value.trim();
            const addr = document.getElementById('address').value.trim();

            const pattern1 = /^[6-9]\d{9}$/;
            const pattern2 = /^\+91[6-9]\d{9}$/;
            if (!(pattern1.test(phone) || pattern2.test(phone))) {
                alert('Enter valid phone number (10 digit or +91 format)');
                return;
            }

            if (!name || !item || !addr) {
                alert('Please fill all the fields');
                return;
            }

            const message = encodeURIComponent(
                `Order from Food category:\nName: ${name}\nPhone: ${phone}\nItem: ${item}\nAddress: ${addr}`
            );
            window.open(`https://wa.me/918977143043?text=${message}`, '_blank');
        }
    </script>
</head>
<body>
    <header>
        <h1>Food Delivery</h1>
        <nav><button onclick="goBack()">Back to Home</button></nav>
    </header>

    <div class="gallery">
        <img src="../images/food1.jpg" alt="Food 1" />
        <img src="../images/food2.jpg" alt="Food 2" />
        <img src="../images/food3.jpg" alt="Food 3" />
        <img src="../images/food4.jpg" alt="Food 4" />
        <img src="../images/food5.jpg" alt="Food 5" />
        <img src="../images/food6.jpg" alt="Food 6" />
        <img src="../images/food7.jpg" alt="Food 7" />
        <img src="../images/food8.jpg" alt="Food 8" />
        <img src="../images/food9.jpg" alt="Food 9" />
        <img src="../images/food10.jpg" alt="Food 10" />
    </div>

    <form onsubmit="sendOrder(event)">
        <label for="name">Name:</label>
        <input type="text" id="name" required placeholder="Your Name" />

        <label for="phone">Mobile Number:</label>
        <input type="tel" id="phone" 
               pattern="(\+91)?[6-9]\d{9}" 
               placeholder="10 digit or +91 number" required
               oninput="validatePhone(this)" />

        <label for="item">Order Item:</label>
        <input type="text" id="item" required placeholder="What do you want to order?" />

        <label for="address">Delivery Address:</label>
        <textarea id="address" rows="3" placeholder="Your delivery address" required></textarea>

        <button type="submit">Place Order via WhatsApp</button>
    </form>
</body><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Pharmacy Delivery</title>
    <style>
        body { font-family: Arial, sans-serif; background:#f0fbff; margin:0; padding:0;}
        header { background:#2196f3; color:#fff; padding: 15px; text-align:center;}
        nav { margin: 12px; text-align:center;}
        nav button { background:#87ceeb; border:none; padding: 10px 20px; margin:2px; border-radius:6px; color:#fff; font-weight:bold; cursor:pointer;}
        nav button:hover { background:#4444aa;}
        .gallery {
            display:grid;
            grid-template-columns: repeat(auto-fit, minmax(150px,1fr));
            gap: 14px;
            max-width: 900px;
            margin: 24px auto 38px auto;
        }
        .gallery img {
            width: 100%;
            height: 140px;
            object-fit: cover;
            border-radius: 10px;
            box-shadow: 0 1px 5px #a2d4f7;
        }
        form {
            max-width: 450px;
            background:#fff;
            margin: 0 auto 40px auto;
            padding: 24px 20px;
            border-radius: 14px;
            box-shadow: 0 2px 8px #d8ecff;
        }
        label {
            display: block;
            margin-bottom: 6px;
            color: #222;
            font-weight: bold;
        }
        input, textarea {
            width: 100%;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #99bbdd;
            margin-bottom: 18px;
            font-size: 16px;
            font-family: Arial, sans-serif;
        }
        button {
            width: 100%;
            background: #2196f3;
            color: white;
            font-weight: bold;
            padding: 14px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 18px;
            transition: background 0.2s;
        }
        button:hover {
            background: #0b7dda;
        }
        .hint {
            font-size: 12px;
            color: #555;
            margin-top: -12px;
            margin-bottom: 14px;
            padding-left: 4px;
        }
    </style>
    <script>
        function goBack() {
            window.location.href = '../index.html';
        }
        function validatePhone(input) {
            const val = input.value.trim();
            const pattern1 = /^[6-9]\d{9}$/;
            const pattern2 = /^\+91[6-9]\d{9}$/;
            if (pattern1.test(val) || pattern2.test(val)) {
                input.setCustomValidity('');
            } else {
                input.setCustomValidity('Enter valid 10 digit or +91 number');
            }
        }
        function sendOrder(event) {
            event.preventDefault();
            const name = document.getElementById('name').value.trim();
            const phone = document.getElementById('phone').value.trim();
            const item = document.getElementById('item').value.trim();
            const addr = document.getElementById('address').value.trim();

            const pattern1 = /^[6-9]\d{9}$/;
            const pattern2 = /^\+91[6-9]\d{9}$/;
            if (!(pattern1.test(phone) || pattern2.test(phone))) {
                alert('Enter valid phone number (10 digit or +91 format)');
                return;
            }

            if (!name || !item || !addr) {
                alert('Please fill all the fields');
                return;
            }

            const message = encodeURIComponent(
                `Order from Pharmacy category:\nName: ${name}\nPhone: ${phone}\nItem: ${item}\nAddress: ${addr}`
            );
            window.open(`https://wa.me/918977143043?text=${message}`, '_blank');
        }
    </script>
</head>
<body>
    <header>
        <h1>Pharmacy Delivery</h1>
        <nav><button onclick="goBack()">Back to Home</button></nav>
    </header>

    <div class="gallery">
        <img src="../images/pharmacy1.jpg" alt="Pharmacy 1" />
        <img src="../images/pharmacy2.jpg" alt="Pharmacy 2" />
        <img src="../images/pharmacy3.jpg" alt="Pharmacy 3" />
        <img src="../images/pharmacy4.jpg" alt="Pharmacy 4" />
        <img src="../images/pharmacy5.jpg" alt="Pharmacy 5" />
        <img src="../images/pharmacy6.jpg" alt="Pharmacy 6" />
        <img src="../images/pharmacy7.jpg" alt="Pharmacy 7" />
        <img src="../images/pharmacy8.jpg" alt="Pharmacy 8" />
        <img src="../images/pharmacy9.jpg" alt="Pharmacy 9" />
        <img src="../images/pharmacy10.jpg" alt="Pharmacy 10" />
    </div>

    <form onsubmit="sendOrder(event)">
        <label for="name">Name:</label>
        <input type="text" id="name" required placeholder="Your Name" />

        <label for="phone">Mobile Number:</label>
        <input type="tel" id="phone" 
               pattern="(\+91)?[6-9]\d{9}" 
               placeholder="10 digit or +91 number" required
               oninput="validatePhone(this)" />

        <label for="item">Order Item:</label>
        <input type="text" id="item" required placeholder="What do you want to order?" />

        <label for="address">Delivery Address:</label>
        <textarea id="address" rows="3" placeholder="Your delivery address" required></textarea>

        <button type="submit">Place Order via WhatsApp</button>
    </form>
</body>
</html>
</html>
