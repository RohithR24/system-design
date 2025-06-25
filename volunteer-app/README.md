# Volunteer App – System Design Documentation

## 📌 Functional Requirements

### 👤 User

1. Create an account using Google and update their profile.
2. View all events (filterable by location and date).
3. Register for events.
4. Receive notifications for newly posted events.
5. View history of attended events.

### 👨‍💼 Admin

1. Create new events.
2. Approve registered volunteers.
3. Check-in and check-out volunteers during events.
4. Take action on volunteers (e.g., Approve, Reject, etc.)

---

## ⚙️ Non-Functional Requirements

- Support for up to **100 simultaneous users**.
- No high scalability needs as this application is intended for a specific group of users.

---

## 🔌 API Endpoints

### 👤 Volunteer

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/user/events?location=&date_from=&date_to=` | View and filter events by location and date. Defaults to the next 30 calendar days. |
| POST   | `/user/{eventId}/register` | Register for an event. |
| PUT    | `/user/profile/update` | Update user profile. |
| GET    | `/user/{userId}/points?range=date` | View earned points within a selected date range. Defaults to all-time. |

---

### 🛠️ Admin / Lead

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/admin/volunteers` | View list of all volunteers. |

#### 📅 Event Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/admin/event` | Create a new event. |
| PUT    | `/admin/event/{eventId}` | Update event details. |
| DELETE | `/admin/event/{eventId}` | Delete an event. |
| GET    | `/admin/events` | List all events. |

#### 🏛️ Venue Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/admin/venue` | Create a new venue. |
| PUT    | `/admin/venue/{venueId}` | Update venue details. |
| DELETE | `/admin/venue/{venueId}` | Delete a venue. |
| GET    | `/admin/venues` | List all venues. |

#### ⏱️ Attendance Management

| Method | Endpoint | Description |
|--------|----------|-------------|
| PUT    | `/admin/attendance/{userId}/checkin` | Update check-in time (set status to `CheckedIn`). |
| PUT    | `/admin/attendance/{userId}/checkout` | Update check-out time (set status to `Attended`). |

#### 🛡️ Volunteer Action

| Method | Endpoint | Description |
|--------|----------|-------------|
| PUT    | `/admin/action/{userId}` | Take action (approve or reject) for a volunteer based on `eventId` and action in request body. |

---



---

> Feel free to expand with authentication flow, notification service architecture, or hosting plans if needed.
