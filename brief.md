# CampusEats — System Brief

## 1. What CampusEats Does
CampusEats is an online food ordering and pickup management web application built for our college campus. 

During lunch and tea breaks, students and faculty face long queues at campus canteens and food stalls, which wastes a lot of break time. CampusEats solves this problem by allowing students to view live canteen menus, check item availability, place orders in advance, and pay online. 

Instead of waiting in line, students receive a digital pickup token and an alert when their food is prepared. For canteen staff, the application acts as an order dashboard to accept incoming orders, update item availability when stock runs out, and organize kitchen preparation smoothly.

---

## 2. Who Uses It (System Actors)

1. **Students & Faculty (Customers):**
   - Browse canteen menus and check available items.
   - Add items to cart, place orders, and pay digitally.
   - Track live order status and show token at the counter to collect food.

2. **Canteen Staff / Vendors:**
   - Manage daily food menus and toggle item availability (in-stock / out-of-stock).
   - View incoming orders, accept or reject them based on rush.
   - Update order preparation status (*Preparing* -> *Ready for Pickup*).

3. **Campus Admin:**
   - Onboard new canteen vendors and manage stall locations.
   - Manage user accounts and handle order/payment disputes.

---

## 3. Nouns (System Entities & Data Objects)
The core things (data entities) managed by CampusEats are:

- **User:** Stores profile information of students, faculty, and vendors (`user_id`, `name`, `email`, `role`, `phone`).
- **Canteen:** Represents a food outlet on campus (`canteen_id`, `name`, `location`, `opening_hours`, `is_active`).
- **MenuItem:** Represents a food dish or beverage (`item_id`, `canteen_id`, `name`, `price`, `category`, `is_available`).
- **Order:** Represents a food order placed by a user (`order_id`, `user_id`, `canteen_id`, `total_amount`, `order_status`, `pickup_token`, `created_at`).
- **OrderItem:** Line items inside an order with quantity and item snapshot (`order_item_id`, `order_id`, `item_id`, `quantity`, `price_at_order`).
- **Payment:** Financial record of the transaction (`payment_id`, `order_id`, `amount`, `payment_method`, `payment_status`, `txn_reference`).
- **Notification:** Status alert sent to the user (`notification_id`, `user_id`, `message`, `sent_at`).

---

## 4. Verbs (Actions & System Operations)
The primary operations and actions executed across the system are:

- **BrowseMenu:** User fetches the current list of active items for a canteen.
- **PlaceOrder:** User validates cart items and creates a new order in `Pending` state.
- **ProcessPayment:** User pays for the order via online payment methods.
- **AcceptOrder:** Canteen staff reviews the incoming order and confirms preparation.
- **UpdateOrderStatus:** Canteen staff advances the state (`Pending` -> `Preparing` -> `Ready` -> `Completed`).
- **CollectOrder:** User verifies their pickup token at the counter and receives the meal.
- **CancelOrder:** User or vendor cancels an order before cooking starts and initiates a refund.
- **UpdateItemStock:** Vendor marks an item as available or out-of-stock in real time.