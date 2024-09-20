<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CloToGo - Clothing Delivery Service</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            margin: 0;
            padding: 0;
            color: #333;
        }

        header {
            background-color: #1e90ff;
            color: #fff;
            text-align: center;
            padding: 20px;
            position: relative;
        }

        header img {
            position: absolute;
            left: 20px;
            top: 15px;
            width: 80px;
            height: auto;
        }

        h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        p.description {
            font-size: 1.2rem;
            margin: 10px 0 20px;
            font-style: italic;
        }

        .company-description {
            font-size: 1rem;
            margin: 20px auto;
            padding: 0 20px;
            max-width: 800px;
            color: #444;
        }

        section {
            margin: 20px auto;
            padding: 20px;
            width: 90%;
            max-width: 600px;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }

        h2 {
            color: #1e90ff;
        }

        label {
            display: block;
            margin-top: 10px;
        }

        input, select, textarea {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border-radius: 4px;
            border: 1px solid #ccc;
        }

        button {
            background-color: #1e90ff;
            color: #fff;
            padding: 10px 20px;
            margin-top: 10px;
            border: none;
            cursor: pointer;
            border-radius: 4px;
        }

        button:hover {
            background-color: #4682b4;
        }

        #reviews-container {
            margin-top: 20px;
        }

        #reviews-list {
            list-style-type: none;
            padding: 0;
        }

        #reviews-list li {
            background-color: #f1f1f1;
            padding: 10px;
            margin-top: 10px;
            border-radius: 4px;
        }

        .pay-now {
            background-color: #32cd32;
            margin-top: 20px;
        }

        .pay-now:hover {
            background-color: #228b22;
        }

        .deposit-info {
            font-size: 0.9rem;
            margin-top: 5px;
            color: #333;
        }
    </style>
</head>
<body>
    <header>
        <h1>CloToGo</h1>
        <p class="description">Welcome to CloToGo - Your personal clothing delivery service!</p>
    </header>

    <div class="company-description">
        <p>CloToGo is a premier clothing delivery service exclusively designed for the Syracuse Community, bringing your favorite fashion brands directly to your doorstep. We partner with popular stores like H&M, Old Navy, and American Eagle to provide a seamless shopping experience that combines the convenience of online ordering with the speed of local delivery.</p>
    </div>

    <section id="order-section">
        <h2>Place Your Order</h2>
        <form id="order-form">
            <div id="item-container">
                <label for="item-number">Item Number:</label>
                <input type="text" class="item-number" name="item-number[]" required>

                <label for="quantity">Quantity:</label>
                <input type="number" class="quantity" name="quantity[]" required>

                <label for="size">Size:</label>
                <select class="size" name="size[]" required>
                    <option value="" disabled selected>Select Size</option>
                    <option value="small">Small</option>
                    <option value="medium">Medium</option>
                    <option value="large">Large</option>
                    <option value="xl">XL</option>
                </select>
            </div>

            <button type="button" id="add-item">Add Another Item</button>

            <label for="contact-info">Contact Information:</label>
            <input type="email" id="contact-info" name="contact-info" placeholder="Enter your email" required>

            <label for="store-location">Store Location (Where is the item?):</label>
            <input type="text" id="store-location" name="store-location" placeholder="Enter the store where the item is located" required>

            <button type="submit">Submit Order</button>
        </form>

        <button class="pay-now">Pay Now</button>
        <p class="deposit-info">A $5 deposit is required at this time, remainder of payment due at the time of delivery!</p>
    </section>

    <section id="reviews-section">
        <h2>Leave a Review</h2>
        <form id="review-form">
            <label for="review">Your Review:</label>
            <textarea id="review" name="review" rows="4" required></textarea>

            <button type="submit">Submit Review</button>
        </form>
        <div id="reviews-container">
            <h3>Customer Reviews</h3>
            <ul id="reviews-list">
                <!-- Reviews will be added here -->
            </ul>
        </div>
    </section>

    <script>
        // Add more item fields
        document.getElementById('add-item').addEventListener('click', function() {
            let itemContainer = document.getElementById('item-container');
            let newItem = `
                <label for="item-number">Item Number:</label>
                <input type="text" class="item-number" name="item-number[]" required>

                <label for="quantity">Quantity:</label>
                <input type="number" class="quantity" name="quantity[]" required>

                <label for="size">Size:</label>
                <select class="size" name="size[]" required>
                    <option value="" disabled selected>Select Size</option>
                    <option value="small">Small</option>
                    <option value="medium">Medium</option>
                    <option value="large">Large</option>
                    <option value="xl">XL</option>
                </select>
            `;
            itemContainer.insertAdjacentHTML('beforeend', newItem);
        });

        document.getElementById('order-form').addEventListener('submit', function(event) {
            event.preventDefault();
            alert('Thank you for your order! We will contact you soon.');
        });

        document.querySelector('.pay-now').addEventListener('click', function() {
            alert('Redirecting to payment page...');
            // Add your payment integration logic here
        });

        document.getElementById('review-form').addEventListener('submit', function(event) {
            event.preventDefault();
            let review = document.getElementById('review').value;
            if (review) {
                let reviewList = document.getElementById('reviews-list');
                let newReview = document.createElement('li');
                newReview.textContent = review;
                reviewList.appendChild(newReview);
                document.getElementById('review').value = ''; // clear review text area
                alert('Thank you for your review!');
            }
        });
    </script>
</body>
</html>
