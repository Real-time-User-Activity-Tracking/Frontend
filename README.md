# Real-time User Activity Tracking - Frontend

A modern, responsive web application that demonstrates real-time user activity tracking and analytics. This frontend application simulates an e-commerce mobile phone store while capturing and sending user interaction data to a backend analytics service.

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

### 🔧 Technical Features
- **Static HTML**: Single-page application with embedded JavaScript
- **Backend Integration**: RESTful API communication with analytics backend
- **Error Handling**: Graceful error handling for network issues
- **CORS Support**: Configured for cross-origin requests

## 📋 Prerequisites
- Modern web browser with JavaScript enabled
- Backend analytics service running on `http://localhost:9094`
- CORS properly configured on the backend

## 📊 Tracked Events

The application tracks the following user interactions:

### 1. Page View Events
- **Trigger**: Page load
- **Data**: Page title, type, total products count
- **Endpoint**: `POST /track/event`

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


### Event Payload Structure
```json
{
  "timestamp": "2024-01-01T12:00:00.000Z",
  "user_id": "user-abc123",
  "session_id": "session-xyz789",
  "event_type": "page_view|search|image_click|button_click",
  "page_url": "http://localhost:8000",
  "additional_data": {}
}
```


### Event Tracking
- Add new event types in the JavaScript section
- Modify the `sendEvent` function for different payload structures
- Update event logging format and styling

## 🐛 Troubleshooting

### Common Issues

1. **Events not sending**
   - Check if backend is running on port 9094
   - Verify CORS configuration on backend
   - Check browser console for network errors

2. **Event log not updating**
   - Ensure JavaScript is enabled
   - Check for JavaScript errors in console
   - Verify DOM elements exist

3. **Styling issues**
   - Ensure Tailwind CSS CDN is accessible
   - Check if Google Fonts are loading
   - Verify CSS custom properties


**Note**: This is a demo application for educational purposes. In production, ensure proper security measures, data privacy compliance, and robust error handling.
