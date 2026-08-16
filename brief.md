# CampusEats - System Architecture & Domain Brief

## 1. What CampusEats Does (System Overview)
CampusEats is an on-campus digital food ordering and pickup management platform tailored for university environments. The system eliminates long physical queues at campus food courts, cafeterias, and canteens during rush hours. 

Students and faculty can browse live digitized menus, check real-time item availability, customize dishes, place pre-orders, and make cashless payments. For canteen vendors, the platform provides an order management dashboard to streamline kitchen workflows, control live inventory, manage preparation queues, and notify customers when their food is ready for pickup.

---

## 2. Who Uses It (Actors / Stakeholders)

- **Students & Faculty (Customers / End-Users):**
  - Search campus food outlets, view item pricing and nutritional/dietary tags.
  - Place scheduled or instant pickup orders and track live order progress.
  - Execute digital payments and submit feedback/reviews.

- **Canteen Staff / Vendors (Merchants):**
  - Manage daily menu items (pricing, active/inactive status, stock).
  - Accept, queue, and transition order states (e.g., *Received* -> *Preparing* -> *Ready for Pickup*).
  - Review daily sales summaries and order throughput.

- **Campus Administrator:**
  - Onboard and verify campus vendor stalls.
  - Manage user role permissions, handle disputes, monitor hygiene/service compliance, and analyze campus-wide operational metrics.

---

## 3. Nouns (Entities / Core Domain Models)
The nouns define the core data objects, resources, and database entities of CampusEats:

1. **User:** Represents system actors (`user_id`, `name`, `email`, `role`, `phone`, `campus_id`).
2. **Vendor / Canteen:** An outlet operating within campus (`vendor_id`, `name`, `stall_location`, `operating_hours`, `is_open`).
3. **MenuItem:** Individual food or beverage offering (`item_id`, `vendor_id`, `name`, `category`, `price`, `is_available`, `prep_time_estimate`).
4. **Order:** A transactional record binding a user to specific food items (`order_id`, `user_id`, `vendor_id`, `total_amount`, `order_status`, `placed_at`, `pickup_time`).
5. **OrderItem:** Relational line-item representing quantity and customizations within an order (`order_item_id`, `order_id`, `item_id`, `quantity`, `unit_price`, `special_instructions`).
6. **Payment:** Financial transaction record (`payment_id`, `order_id`, `payment_gateway_ref`, `amount`, `payment_method`, `payment_status`, `timestamp`).
7. **Notification:** Real-time event alert dispatched to user devices (`notification_id`, `user_id`, `message_text`, `notification_type`, `is_read`).
8. **Review:** User rating and feedback on food quality/service (`review_id`, `order_id`, `user_id`, `rating_score`, `comment_text`).

---

## 4. Verbs (Actions / System Contracts / Operations)
The verbs represent functional actions, state transitions, and API contracts executed across the system:

1. **AuthenticateUser:** Verify campus credentials and issue secure session tokens.
2. **BrowseMenu:** Query and filter available food items by vendor, category, dietary preference, or price range.
3. **AddToCart:** Aggregate selected `MenuItem` records with desired quantities and customization flags.
4. **PlaceOrder:** Validate inventory, generate a new `Order` record, and set initial state to `Pending`.
5. **ProcessPayment:** Execute transaction via digital gateway and record `Payment` confirmation.
6. **AcceptOrder / RejectOrder:** Vendor reviews incoming order against kitchen bandwidth and accepts or cancels it.
7. **UpdatePreparationStatus:** Advance order lifecycle (`Pending` -> `Preparing` -> `Ready for Pickup` -> `Completed`).
8. **NotifyCustomer:** Push live status notifications to the customer when the kitchen marks food ready for collection.
9. **CollectOrder:** Verify order token/OTP at the vendor counter and mark order as `Completed`.
10. **CancelOrder:** Abort an active order prior to kitchen preparation and trigger automated payment refund.