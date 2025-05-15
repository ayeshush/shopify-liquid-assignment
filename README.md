# Shopify Liquid Assignment

## ✅ Tasks Completed with Logic

---

### Task 1: Dynamic Product Badge

- **File modified:** `snippets/card-product.liquid`
- **What it does:**  
  Adds badges to product cards on collection pages.

- **Logic Used:**  
  - If `product.price < 500`, show “Budget Pick”
  - If `product.quantity <= 5`, show “Limited Stock”
  - If product is **sold out**, do not show “Limited Stock”
  - Used `product.price` and `product.selected_or_first_available_variant.inventory_quantity`
  - Placed the badge code inside the card badge container, and used conditional checks with `{% if %}` statements

---

### Task 2: Custom Collection Filter

- **File modified:** `sections/main-collection-product-grid.liquid`
- **What it does:**  
  Adds a dropdown to filter collection page products by tags like Best Seller, New Arrival, or Discounted.

- **Logic Used:**  
  - Uses a `<select>` dropdown and a JavaScript `onchange` listener
  - On selection, it reloads the page and appends the tag to the URL path (e.g., `/collections/all/best-seller`)
  - Inside the product loop, used `{% if current_tags == blank or product.tags contains current_tags %}` to filter what gets shown
  - Keeps the selected option persistent using `{% if current_tags contains 'tag' %}selected{% endif %}`

---

### Task 3: Personalized Greeting on Homepage

- **Files modified:**  
  - `sections/greeting.liquid`  
  - `templates/index.json`

- **What it does:**  
  Adds a greeting at the top of the homepage based on the current time.

- **Logic Used:**  
  - Used Liquid's `date` filter to get the current hour with `{% assign current_hour = 'now' | date: '%H' | plus: 0 %}`
  - Used `{% if current_hour < 12 %}`, `{% elsif current_hour < 18 %}`, and `{% else %}` to show:
    - “Good Morning” before 12 PM
    - “Good Afternoon” between 12–6 PM
    - “Good Evening” after 6 PM
  - Registered the new section in `index.json` and placed it at the top of the `"order"` array

---

### Task 4: Cart Upsell Section

- **File modified:** `sections/main-cart-items.liquid`
- **What it does:**  
  Displays an upsell product on the cart page depending on cart total.

- **Logic Used:**  
  - First assigned cart total using:  
    `{% assign cart_total = cart.total_price | divided_by: 100 %}` (Shopify stores price in paise)
  - If cart_total < 1000 → show product from `collections['accessories'].products.first`
  - Else → show product from `collections['premium'].products.first`
  - Displayed image, title, and price of the upsell product
  - Added fallback image using a conditional check if `featured_image` is not present

---

### Bonus Task: Dynamic Free Shipping Message

- **File modified:** `sections/main-cart-items.liquid`
- **What it does:**  
  Shows a message based on the cart total about free shipping eligibility.

- **Logic Used:**  
  - If cart_total < 500:  
    Show → “Spend ₹{{ 500 | minus: cart_total }} more to get free shipping!”
  - Else:  
    Show → “You've unlocked free shipping!”
  - Placed this message below the upsell section using simple `{% if %}` conditions

---

## 🔗 Preview Link

[Shopify Development Store Preview](https://henq03-vr.myshopify.com/)

🔐 **Password:** reiglo
