# Real-time User Activity Tracking - Frontend

A modern, responsive web application that demonstrates real-time user activity tracking. This frontend application simulates an e-commerce mobile phone store while capturing and sending user interaction data to a clean, simplified backend ingestion service.

## 🚀 Features

### 📊 Real-time Analytics Tracking
- **User Identification**: Persistent user IDs stored in localStorage
- **Session Management**: Unique session IDs for each page visit
- **Event Tracking**: Comprehensive tracking of user interactions:
  - Page views
  - Search queries
  - Product image clicks
  - Button interactions (Add to Cart, Buy Now)
- **Real-time Event Log**: Live display of tracked events with timestamps
- **CORS Integration**: Proper cross-origin communication with backend


## 🏗️ Architecture

```
Frontend (localhost:3000) → Backend (localhost:9094)
     |                            |
     | 1. OPTIONS (Preflight)     |
     | 2. POST /api/v1/events/track |
     | 3. Receive JSON Response   |
```

## 📊 Tracked Events

The application tracks the following user interactions:

### 1. Page View Events
- **Trigger**: Page load
- **Data**: Page title, type, total products count
- **Endpoint**: `POST /api/v1/events/track`

### 2. Search Events
- **Trigger**: Search button click or Enter key press
- **Data**: Search query, search box ID, context
- **Validation**: Empty queries are logged as warnings

### 3. Image Click Events
- **Trigger**: Product image clicks
- **Data**: Product ID, name, price, element ID

### 4. Button Click Events
- **Trigger**: Add to Cart or Buy Now button clicks
- **Data**: Action type, product details, price

## 📡 API Integration

### Event Payload Structure
```json
{
  "event_type": "button_click|search|page_view|image_click",
  "timestamp": "2024-01-01T12:00:00.000Z",
  "user_id": "user-abc123",
  "session_id": "session-xyz789",
  "page_url": "http://localhost:3000",
  "event_data": {
    "action": "add_to_cart",
    "product_id": "phone-001",
    "product_name": "iPhone 15 Pro"
  },
  "client_info": {
    "user_agent": "Mozilla/5.0...",
    "screen_resolution": "1920x1080",
    "language": "en-US"
  }
}
```

### Backend Response
```json
{
  "status": "success",
  "message": "Event received and processed successfully",
  "event_id": "uuid-generated",
  "request_id": "uuid-generated",
  "timestamp": "2024-01-01T12:00:00.000Z"
}
```

### CORS Flow
1. **Preflight Request**: Browser sends OPTIONS request
2. **Backend Response**: Returns CORS headers allowing the request
3. **Actual Request**: Browser sends POST with event data
4. **Success Response**: Backend processes and responds with confirmation

## 🛠️ Backend Service

The frontend communicates with a clean, simplified Go backend service:

### Backend Endpoints
- `POST /api/v1/events/track` - Event tracking


### Start the Frontend
```bash
cd Frontend
python3 -m http.server 3000
# or
npx serve -s . -l 3000
```

### Open in Browser
Navigate to `http://localhost:3000`
