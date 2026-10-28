# Fast Orders — customer reviews integrated

## What changed
- Customer feedback stays on the customer order-tracking page (`index.html` / `customer.html`).
- When a customer submits feedback, the review includes the order number, ordered items, quantities, item prices, order total, star rating, comment, and submission time.
- The manager dashboard now has a **Customer Reviews** tab showing those details.
- Each review is published to a separate retained MQTT topic so multiple reviews can be restored when the manager reconnects.
- `reviews.html` is no longer needed for the integrated flow.

## Upload to the existing GitHub Pages repository
1. Keep a backup of your current files first.
2. Upload/replace `index.html`, `customer.html`, `manager.html`, and `cashier.html` in the repository root.
3. Commit the changes and wait for GitHub Pages to publish.
4. Open the customer page through the cashier's QR code and test with a sample order.
5. Mark the sample order as picked up, submit a rating/comment, then open Manager → Customer Reviews.

## Important limitations of this version
- This is still the existing MQTT/localStorage prototype, not a secured production backend. The MQTT broker/topic is public, so someone who knows the topic could publish fake reviews or order updates.
- The manager login in this supplied code is a browser-side demo login, not secure authentication.
- Old reviews created before this update only contain their order number/rating/comment; their item details cannot be reconstructed from the old review record. New reviews include order details.
- The pages currently display prices using `$`, as in your original code. Change the currency display separately if you want ETB.
