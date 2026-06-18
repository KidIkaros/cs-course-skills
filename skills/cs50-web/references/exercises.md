# CS50 Web — Practice Exercises

## HTML/CSS Exercises

### Exercise 1: Personal Portfolio
Build a responsive personal portfolio page.
- Use semantic HTML5 elements
- Implement CSS Grid for project cards
- Add flexbox navigation bar
- Mobile-first responsive design
- Dark/light theme toggle with CSS

### Exercise 2: Form with Validation
Create a registration form with client-side validation.
- Required field indicators
- Email format validation
- Password strength meter
- Real-time error messages
- Accessible error announcements

### Exercise 3: CSS Animation Gallery
Build a page showcasing CSS animations.
- Keyframe animations (fade, slide, bounce)
- Transition effects on hover
- Loading spinner with CSS
- Responsive image gallery with smooth transitions

---

## JavaScript Exercises

### Exercise 4: Todo Application
Build a todo app with vanilla JavaScript.
- Add, complete, delete tasks
- Filter by status (all, active, completed)
- Local storage persistence
- Drag-and-drop reordering
- Keyboard shortcuts

### Exercise 5: API Weather Dashboard
Create a weather dashboard using a public API.
- Fetch data from OpenWeatherMap API
- Display current conditions and forecast
- Search by city name
- Geolocation support
- Error handling for failed requests

### Exercise 6: Debounced Search
Implement a search feature with debouncing.
- Input field with debounced API calls
- Display search results in dropdown
- Keyboard navigation (arrow keys, enter)
- Loading states
- Cancel previous requests on new input

---

## Django Exercises

### Exercise 7: Blog Platform
Build a blog with Django.
- User registration and authentication
- Create, edit, delete posts (owner only)
- Comment system
- Tag/category filtering
- Pagination
- Image uploads

### Exercise 8: REST API
Create a REST API for a bookstore.
- CRUD operations for books, authors, genres
- Filtering and search
- Pagination (page number and offset)
- Authentication with tokens
- Rate limiting
- API documentation

### Exercise 9: Real-time Chat
Build a chat application with Django Channels.
- WebSocket connections
- Multiple chat rooms
- Message history
- Online user status
- Typing indicators

---

## SQL Exercises

### Exercise 10: Database Design
Design a schema for a library management system.
- Books, authors, genres (many-to-many)
- Members and borrowing records
- Reservations and waitlists
- Fine calculation for overdue books
- Write queries for:
  - Most borrowed books
  - Members with overdue items
  - Author popularity ranking

### Exercise 11: Query Optimization
Optimize slow database queries.
- Add appropriate indexes
- Use select_related / prefetch_related
- Avoid N+1 query problems
- Profile query performance with django-debug-toolbar
- Rewrite subqueries as joins where appropriate

---

## React Exercises

### Exercise 12: Shopping Cart
Build a shopping cart with React.
- Product listing with filtering
- Add to cart with quantity management
- Cart persistence (localStorage)
- Checkout form
- Order summary

### Exercise 13: GitHub User Finder
Create a GitHub profile search tool.
- Search users by username
- Display profile info and repositories
- Repository details with language stats
- Favorites list with context API
- Loading and error states

### Exercise 14: Multi-step Form
Implement a multi-step registration form.
- Step navigation (next, previous)
- Form state management across steps
- Validation per step
- Progress indicator
- Summary page before submission

---

## Git Exercises

### Exercise 15: Branching Workflow
Practice Git branching strategies.
- Create feature branches
- Resolve merge conflicts
- Interactive rebase
- Cherry-pick commits
- Bisect to find bug introduction

---

## Full-Stack Exercises

### Exercise 16: Task Management System
Build a complete task management app.
- Django backend with REST API
- React frontend
- User authentication (JWT)
- Task boards (To Do, In Progress, Done)
- Drag-and-drop between boards
- Team collaboration features
- Activity log

### Exercise 17: E-commerce Platform
Create a minimal e-commerce site.
- Product catalog with categories
- Shopping cart and checkout
- Payment simulation (Stripe test mode)
- Order tracking
- Admin dashboard
- Email notifications (console)
- Search and filtering

### Exercise 18: Social Media Dashboard
Build a social media analytics dashboard.
- Django backend with aggregated data
- React charts (Chart.js or D3)
- Date range filtering
- Export to CSV
- Real-time updates with polling
- Responsive data tables

---

## Testing Exercises

### Exercise 19: Test Coverage
Write comprehensive tests for a Django app.
- Model tests (creation, validation, methods)
- View tests (status codes, context, redirects)
- Form tests (validation, save)
- API tests (CRUD, authentication, permissions)
- Achieve 90%+ coverage

### Exercise 20: React Component Tests
Write tests for React components.
- Unit tests with Jest
- Component rendering with React Testing Library
- User interaction simulation
- API mocking
- Snapshot testing

---

## Deployment Exercises

### Exercise 21: Production Deployment
Deploy a Django app to production.
- Set up production database (PostgreSQL)
- Configure static file serving (WhiteNoise)
- Environment variables for secrets
- HTTPS with Let's Encrypt
- Set up CI/CD pipeline with GitHub Actions
- Configure logging and monitoring

### Exercise 22: Docker Deployment
Containerize a Django + React app.
- Dockerfile for Django backend
- Dockerfile for React frontend
- docker-compose.yml for orchestration
- PostgreSQL container
- Nginx reverse proxy
- Volume mounting for development
