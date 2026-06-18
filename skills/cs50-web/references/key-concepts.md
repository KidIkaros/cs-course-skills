# CS50 Web — Key Concepts Cheat Sheet

## HTML/CSS

### Semantic HTML5 Elements
```html
<header>    <!-- Page/section header -->
<nav>       <!-- Navigation links -->
<main>      <!-- Main content -->
<article>   <!-- Self-contained content -->
<section>   <!-- Thematic grouping -->
<aside>     <!-- Sidebar content -->
<footer>    <!-- Page/section footer -->
<figure>    <!-- Image with caption -->
<figcaption> <!-- Caption for figure -->
```

### CSS Flexbox
```css
.container {
  display: flex;
  justify-content: space-between; /* main axis */
  align-items: center;            /* cross axis */
  flex-wrap: wrap;
}

.item {
  flex: 1;           /* grow to fill */
  flex-shrink: 0;    /* don't shrink */
  flex-basis: 200px; /* initial size */
}
```

### CSS Grid
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.item {
  grid-column: span 2;  /* span 2 columns */
}
```

### CSS Specificity (low to high)
1. Element selectors (`p`, `div`)
2. Class selectors (`.container`)
3. ID selectors (`#main`)
4. Inline styles (`style=""`)
5. `!important`

---

## JavaScript

### ES6+ Features
```javascript
// Arrow functions
const add = (a, b) => a + b;

// Template literals
const msg = `Hello, ${name}!`;

// Destructuring
const { id, title } = post;
const [first, ...rest] = array;

// Spread operator
const newArray = [...oldArray, newItem];

// Optional chaining
const city = user?.address?.city;

// Nullish coalescing
const value = input ?? 'default';
```

### Promises and Async/Await
```javascript
// Promise
fetch('/api/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// Async/Await
async function loadData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (err) {
    console.error(err);
  }
}
```

### DOM Manipulation
```javascript
// Select
document.querySelector('.class');
document.querySelectorAll('.items');

// Create
const div = document.createElement('div');
div.textContent = 'Hello';
div.classList.add('active');

// Event delegation
document.addEventListener('click', (e) => {
  if (e.target.matches('.btn')) {
    // handle button click
  }
});
```

### Fetch API
```javascript
// GET
const res = await fetch('/api/posts');
const posts = await res.json();

// POST
const res = await fetch('/api/posts', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ title: 'New Post' })
});
```

---

## Python / Django

### Django Project Structure
```
project/
├── project/          # Settings, URLs, WSGI
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── app/              # Application code
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── templates/
│   ├── static/
│   └── tests.py
└── manage.py
```

### Django Models
```python
from django.db import models
from django.contrib.auth.models import User

class Post(models.Model):
    author = models.ForeignKey(User, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    tags = models.ManyToManyField('Tag', blank=True)

    class Meta:
        ordering = ['-created_at']

    def __str__(self):
        return self.title
```

### Django Views
```python
# Function-based view
def post_list(request):
    posts = Post.objects.all()
    return render(request, 'posts/list.html', {'posts': posts})

# Class-based view
from django.views.generic import ListView

class PostListView(ListView):
    model = Post
    template_name = 'posts/list.html'
    context_object_name = 'posts'
    paginate_by = 10
```

### Django URLs
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
    path('<int:pk>/', views.post_detail, name='post_detail'),
    path('create/', views.PostCreateView.as_view(), name='post_create'),
]
```

### Django Templates
```html
{% extends "base.html" %}

{% block content %}
  {% for post in posts %}
    <article>
      <h2>{{ post.title }}</h2>
      <p>{{ post.content|truncatewords:30 }}</p>
      <time>{{ post.created_at|date:"M d, Y" }}</time>
    </article>
  {% empty %}
    <p>No posts yet.</p>
  {% endfor %}
{% endblock %}
```

### Django ORM Queries
```python
# Filter
Post.objects.filter(author=user, status='published')

# Exclude
Post.objects.exclude(status='draft')

# Order
Post.objects.order_by('-created_at')

# Aggregate
from django.db.models import Count
Post.objects.annotate(comment_count=Count('comments'))

# Related objects
post.author.username          # ForeignKey (forward)
post.comments.all()           # Reverse relationship
```

### Django Forms
```python
from django import forms

class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['title', 'content', 'tags']
        widgets = {
            'title': forms.TextInput(attrs={'class': 'form-control'}),
            'content': forms.Textarea(attrs={'rows': 5}),
        }
```

### Django Authentication
```python
from django.contrib.auth import authenticate, login, logout
from django.contrib.auth.decorators import login_required

# Login view
def login_view(request):
    if request.method == 'POST':
        username = request.POST['username']
        password = request.POST['password']
        user = authenticate(request, username=username, password=password)
        if user is not None:
            login(request, user)
            return redirect('home')

# Protect view
@login_required
def dashboard(request):
    return render(request, 'dashboard.html')
```

---

## SQL

### Essential Queries
```sql
-- SELECT with conditions
SELECT * FROM posts WHERE author_id = 1 AND status = 'published';

-- JOIN
SELECT p.title, u.username
FROM posts p
JOIN users u ON p.author_id = u.id;

-- Aggregate
SELECT author_id, COUNT(*) as post_count
FROM posts
GROUP BY author_id
HAVING COUNT(*) > 5;

-- Subquery
SELECT * FROM posts
WHERE author_id IN (SELECT id FROM users WHERE is_active = true);
```

### Database Design Principles
- **Primary Key**: Unique identifier for each row
- **Foreign Key**: References another table's primary key
- **ManyToMany**: Junction/bridge table required
- **Normalization**: Reduce data redundancy (1NF, 2NF, 3NF)
- **Indexing**: Speed up queries on frequently searched columns

---

## React

### Component Structure
```jsx
// Functional component with hooks
function PostList({ posts }) {
  const [expanded, setExpanded] = useState(false);

  return (
    <div className="post-list">
      {posts.map(post => (
        <PostCard
          key={post.id}
          post={post}
          onExpand={() => setExpanded(!expanded)}
        />
      ))}
    </div>
  );
}
```

### useState
```jsx
const [count, setCount] = useState(0);
const [user, setUser] = useState(null);
const [items, setItems] = useState([]);

// Update
setCount(count + 1);
setUser({ ...user, name: 'New Name' });
setItems([...items, newItem]);
```

### useEffect
```jsx
import { useEffect } from 'react';

// Run on mount
useEffect(() => {
  fetchPosts();
}, []);

// Run when dependency changes
useEffect(() => {
  document.title = `${count} items`;
}, [count]);

// Cleanup
useEffect(() => {
  const timer = setInterval(tick, 1000);
  return () => clearInterval(timer);
}, []);
```

### React Router
```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/posts">Posts</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/posts" element={<PostList />} />
        <Route path="/posts/:id" element={<PostDetail />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### Context API
```jsx
const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

// Usage
const { theme } = useContext(ThemeContext);
```

---

## Git

### Essential Commands
```bash
git init                    # Initialize repo
git add .                   # Stage all changes
git commit -m "message"     # Commit
git push origin main        # Push to remote
git pull origin main        # Pull from remote

git checkout -b feature     # Create and switch branch
git merge feature           # Merge branch
git rebase main             # Rebase onto main

git stash                   # Stash changes
git stash pop               # Apply stash
git log --oneline           # View history
git diff                    # View changes
```

### Git Workflow
```
main ─────●─────●─────────●
           \         /
feature     ●───●───●
```

---

## APIs

### RESTful Design
| Method | Endpoint | Action |
|--------|----------|--------|
| GET | `/api/posts` | List posts |
| GET | `/api/posts/:id` | Get post |
| POST | `/api/posts` | Create post |
| PUT | `/api/posts/:id` | Update post |
| DELETE | `/api/posts/:id` | Delete post |

### HTTP Status Codes
- `200` OK
- `201` Created
- `400` Bad Request
- `401` Unauthorized
- `403` Forbidden
- `404` Not Found
- `500` Internal Server Error

---

## Security

### Common Vulnerabilities
- **XSS**: Sanitize user input, escape output, use CSP headers
- **CSRF**: Use CSRF tokens in forms, SameSite cookies
- **SQL Injection**: Use parameterized queries / ORM
- **Session Hijacking**: Use HTTPS, secure cookies, set timeouts

### Django Security Checklist
```python
# settings.py
SECURE_BROWSER_XSS_FILTER = True
SECURE_CONTENT_TYPE_NOSNIFF = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SECURE = True
X_FRAME_OPTIONS = 'DENY'
```
