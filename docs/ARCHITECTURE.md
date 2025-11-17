# OctoFit Tracker Architecture

This document describes the technical architecture of the OctoFit Tracker application that you'll build during the workshop.

## 🏗️ System Overview

OctoFit Tracker is a full-stack web application built with a modern three-tier architecture:

```
┌─────────────────┐
│  React Frontend │  (Port 3000)
│   (Tier 1)      │
└────────┬────────┘
         │ HTTP/REST API
         │
┌────────▼────────┐
│ Django Backend  │  (Port 8000)
│   (Tier 2)      │
└────────┬────────┘
         │ Djongo ORM
         │
┌────────▼────────┐
│    MongoDB      │  (Port 27017)
│   (Tier 3)      │
└─────────────────┘
```

## 🎨 Frontend Architecture (React)

### Technology Stack

- **Framework**: React.js (Create React App)
- **Styling**: Bootstrap 5
- **Routing**: React Router DOM
- **HTTP Client**: Fetch API / Axios
- **State Management**: React Hooks (useState, useEffect)

### Directory Structure

```
frontend/
├── public/
│   ├── index.html           # HTML template
│   └── favicon.ico          # App icon
├── src/
│   ├── components/          # React components
│   │   ├── Dashboard.js     # Main dashboard
│   │   ├── ActivityLog.js   # Activity logging form
│   │   ├── Leaderboard.js   # Competition rankings
│   │   ├── TeamManager.js   # Team creation/management
│   │   └── Profile.js       # User profile
│   ├── services/            # API service layer
│   │   └── api.js           # Backend API calls
│   ├── App.js               # Main app component
│   ├── App.css              # Global styles
│   └── index.js             # Entry point
├── package.json             # Dependencies
└── package-lock.json        # Dependency lock file
```

### Key Components

#### Dashboard Component
- Displays user statistics and recent activities
- Shows team information and rankings
- Provides quick access to main features

#### ActivityLog Component
- Form for logging workouts
- Activity type selection (running, walking, strength)
- Duration and intensity inputs
- Automatic point calculation

#### Leaderboard Component
- Displays individual and team rankings
- Filters by time period (daily, weekly, monthly)
- Real-time updates from backend

#### TeamManager Component
- Create new teams
- Invite members
- View team activities
- Manage team settings

#### Profile Component
- User information display/edit
- Activity history
- Achievement badges
- Personal statistics

### Data Flow

```
User Interaction
      ↓
React Component
      ↓
Event Handler
      ↓
API Service Call
      ↓
Backend API (Django)
      ↓
Database (MongoDB)
      ↓
Response to Frontend
      ↓
State Update
      ↓
Component Re-render
```

## ⚙️ Backend Architecture (Django)

### Technology Stack

- **Framework**: Django 4.1.7
- **API**: Django REST Framework 3.14.0
- **Authentication**: Django Allauth & dj-rest-auth
- **Database Connector**: Djongo 1.3.6
- **CORS**: django-cors-headers

### Project Structure

```
backend/
├── venv/                    # Python virtual environment
├── octofit_tracker/         # Django project root
│   ├── octofit_tracker/     # Project configuration
│   │   ├── __init__.py
│   │   ├── settings.py      # Project settings
│   │   ├── urls.py          # URL routing
│   │   └── wsgi.py          # WSGI config
│   ├── users/               # User management app
│   │   ├── models.py        # User model
│   │   ├── serializers.py   # API serializers
│   │   ├── views.py         # API views
│   │   └── urls.py          # App URLs
│   ├── activities/          # Activity tracking app
│   │   ├── models.py        # Activity model
│   │   ├── serializers.py   # Activity serializers
│   │   ├── views.py         # Activity views
│   │   └── urls.py          # Activity URLs
│   ├── teams/               # Team management app
│   │   ├── models.py        # Team model
│   │   ├── serializers.py   # Team serializers
│   │   ├── views.py         # Team views
│   │   └── urls.py          # Team URLs
│   ├── leaderboard/         # Ranking system app
│   │   ├── models.py        # Ranking model
│   │   ├── serializers.py   # Ranking serializers
│   │   ├── views.py         # Ranking views
│   │   └── urls.py          # Ranking URLs
│   └── manage.py            # Django CLI
└── requirements.txt         # Python dependencies
```

### Django Apps

#### Users App
**Purpose**: User authentication and profile management

**Models**:
- `User`: Extended Django user with fitness profile
  - Fields: username, email, password, age, fitness_level, points

**Endpoints**:
- `POST /api/users/register/` - User registration
- `POST /api/users/login/` - User login
- `GET /api/users/profile/` - Get user profile
- `PUT /api/users/profile/` - Update profile
- `POST /api/users/logout/` - User logout

#### Activities App
**Purpose**: Log and track fitness activities

**Models**:
- `Activity`: Individual workout records
  - Fields: user, activity_type, duration, distance, calories, points, date

**Endpoints**:
- `POST /api/activities/` - Log new activity
- `GET /api/activities/` - List user activities
- `GET /api/activities/{id}/` - Get specific activity
- `PUT /api/activities/{id}/` - Update activity
- `DELETE /api/activities/{id}/` - Delete activity

#### Teams App
**Purpose**: Team creation and management

**Models**:
- `Team`: Team information
  - Fields: name, description, created_by, members, total_points
- `TeamMembership`: User-team relationships
  - Fields: team, user, joined_date, role

**Endpoints**:
- `POST /api/teams/` - Create team
- `GET /api/teams/` - List all teams
- `GET /api/teams/{id}/` - Get team details
- `POST /api/teams/{id}/join/` - Join team
- `POST /api/teams/{id}/leave/` - Leave team

#### Leaderboard App
**Purpose**: Rankings and competitions

**Models**:
- `Ranking`: Cached ranking data
  - Fields: user/team, rank, points, period

**Endpoints**:
- `GET /api/leaderboard/individual/` - Individual rankings
- `GET /api/leaderboard/team/` - Team rankings
- `GET /api/leaderboard/period/{period}/` - Rankings by period

### API Design

#### RESTful Principles

All endpoints follow REST conventions:
- Use HTTP methods correctly (GET, POST, PUT, DELETE)
- Return appropriate status codes
- Use consistent URL structure
- Return JSON responses

#### Authentication

- Token-based authentication (JWT or DRF tokens)
- Protected endpoints require authentication header
- Public endpoints: registration, login
- Private endpoints: all others

#### Response Format

Success response:
```json
{
  "status": "success",
  "data": { /* response data */ }
}
```

Error response:
```json
{
  "status": "error",
  "message": "Error description",
  "errors": { /* field-specific errors */ }
}
```

## 💾 Database Architecture (MongoDB)

### Why MongoDB?

- **Flexible schema**: Easy to evolve as requirements change
- **Document-based**: Natural fit for JSON API responses
- **Scalability**: Horizontal scaling for future growth
- **Developer-friendly**: Works well with Django via Djongo

### Database Schema

#### Users Collection

```javascript
{
  _id: ObjectId,
  username: String,
  email: String,
  password_hash: String,
  first_name: String,
  last_name: String,
  age: Number,
  fitness_level: String,  // "beginner", "intermediate", "advanced"
  total_points: Number,
  created_at: Date,
  updated_at: Date
}
```

#### Activities Collection

```javascript
{
  _id: ObjectId,
  user_id: ObjectId,
  activity_type: String,  // "running", "walking", "strength", etc.
  duration: Number,       // minutes
  distance: Number,       // kilometers
  calories: Number,
  points_earned: Number,
  notes: String,
  date: Date,
  created_at: Date
}
```

#### Teams Collection

```javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  created_by: ObjectId,
  members: [
    {
      user_id: ObjectId,
      joined_date: Date,
      role: String  // "admin", "member"
    }
  ],
  total_points: Number,
  created_at: Date,
  updated_at: Date
}
```

#### Rankings Collection (Cached)

```javascript
{
  _id: ObjectId,
  entity_type: String,    // "user" or "team"
  entity_id: ObjectId,
  period: String,         // "daily", "weekly", "monthly", "all-time"
  rank: Number,
  points: Number,
  calculated_at: Date
}
```

### Indexing Strategy

For optimal performance:

```javascript
// Users collection
db.users.createIndex({ "username": 1 }, { unique: true })
db.users.createIndex({ "email": 1 }, { unique: true })

// Activities collection
db.activities.createIndex({ "user_id": 1, "date": -1 })
db.activities.createIndex({ "activity_type": 1 })

// Teams collection
db.teams.createIndex({ "name": 1 }, { unique: true })
db.teams.createIndex({ "members.user_id": 1 })

// Rankings collection
db.rankings.createIndex({ "period": 1, "rank": 1 })
db.rankings.createIndex({ "entity_id": 1, "period": 1 })
```

## 🔒 Security Considerations

### Authentication & Authorization

- Password hashing using Django's built-in system
- Token-based API authentication
- Role-based access control for team management
- Input validation on all endpoints

### Data Protection

- CORS configured for frontend domain only
- SQL injection prevented by ORM usage
- XSS protection via React's escaping
- CSRF tokens for state-changing operations

### Environment Variables

Sensitive data stored in environment variables:
- Database connection strings
- Secret keys
- API keys
- Debug mode flags

## 🚀 Deployment Architecture

### Development Environment (Codespaces)

```
GitHub Codespace
├── React Dev Server (port 3000)
├── Django Dev Server (port 8000)
└── MongoDB (port 27017)
```

### Production Ready Architecture

```
┌─────────────┐
│   Browser   │
└──────┬──────┘
       │
┌──────▼──────┐
│    CDN      │ (Static React files)
└──────┬──────┘
       │
┌──────▼──────┐
│  Load       │
│  Balancer   │
└──────┬──────┘
       │
┌──────▼──────┐
│  Django     │ (Multiple instances)
│  Servers    │
└──────┬──────┘
       │
┌──────▼──────┐
│  MongoDB    │ (Replica Set)
│  Cluster    │
└─────────────┘
```

## 📊 Data Flow Examples

### User Logs an Activity

1. User fills activity form in React
2. Frontend validates input
3. POST request to `/api/activities/`
4. Django view receives request
5. Serializer validates data
6. Activity saved to MongoDB
7. Points calculated and added to user
8. Team points updated (if applicable)
9. Response sent to frontend
10. UI updates with new activity
11. Leaderboard refreshes

### Viewing Leaderboard

1. User navigates to leaderboard
2. Frontend requests `/api/leaderboard/individual/?period=weekly`
3. Django checks cache (Rankings collection)
4. If cache valid, returns cached data
5. If cache expired, recalculates rankings
6. Queries Activities collection, aggregates by user
7. Sorts by points, assigns ranks
8. Caches results
9. Returns top 100 users
10. Frontend displays ranked list

## 🔧 Key Design Decisions

### Why This Stack?

1. **React**: Most popular frontend framework, large ecosystem
2. **Django**: Batteries-included, rapid development, strong ORM
3. **MongoDB**: Flexible schema, good for learning, easy scaling
4. **REST API**: Industry standard, simple, well-understood

### Trade-offs

**Chosen**: Django + Djongo
- ✅ Familiar ORM patterns
- ✅ Django admin for data management
- ❌ Less efficient than native MongoDB drivers

**Chosen**: Token authentication
- ✅ Stateless, scalable
- ✅ Works across domains
- ❌ More complex than sessions

**Chosen**: Separate frontend/backend
- ✅ Independent deployment
- ✅ Clear separation of concerns
- ❌ More initial setup

## 📚 Further Learning

### Extending the Architecture

Possible enhancements:
- Add Redis for caching and real-time features
- Implement WebSockets for live leaderboard updates
- Add message queue for async processing
- Integrate third-party fitness APIs
- Add mobile apps using React Native
- Implement GraphQL API alternative

### Advanced Topics

- Microservices architecture
- Container orchestration (Docker, Kubernetes)
- CI/CD pipelines
- Monitoring and logging
- A/B testing infrastructure
- Analytics and reporting systems

---

This architecture provides a solid foundation for a production-ready fitness tracking application while remaining accessible for learning purposes.
