# FitnessPoint

A comprehensive fitness awareness website with social features, calorie calculator, personalized food suggestions, and fitness tips and exercises.

## Features

- **User Authentication**: Secure registration and login system with JWT tokens
- **Social Feed**: Post, like, and comment on fitness journeys to encourage each other
  - Edit and delete your own posts
  - Upload photos with posts
- **Calorie Calculator**: Calculate your daily calorie needs and macronutrient targets based on your goals
- **Food Suggestions**: Get personalized meal suggestions based on your calorie needs and dietary preferences (Halal, Vegan, Vegetarian, Lactose-Free, Gluten-Free, Keto, Paleo, Low-Carb, High-Protein)
- **Fitness Tips & Exercises**: Get personalized fitness advice and exercise recommendations
- **User Profiles**: Manage your personal information and fitness goals

## Tech Stack

### Backend
- Node.js with Express
- TypeScript
- SQLite database
- JWT authentication
- bcrypt for password hashing

### Frontend
- React with TypeScript
- React Router for navigation
- Tailwind CSS for styling
- Axios for API calls
- Heroicons for icons

## Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn

### GitHub Codespaces Setup (Automatic) 🚀

When you open this project in GitHub Codespaces, everything is set up automatically:

1. **Dependencies are installed automatically** - All required packages (root, server, and client) will be installed automatically when the container is created. Just wait for the `postCreateCommand` to finish.

2. **Ports are forwarded automatically** - Ports 3000 (Frontend) and 5000 (Backend) are automatically forwarded and accessible via public URLs.

3. **API URL is detected automatically** - The frontend automatically detects the Codespace environment and connects to the backend using the correct external URL. No manual configuration needed!

4. **Start the servers** (run this command in the **root directory**):
   ```bash
   npm run dev
   ```
   This single command starts both the backend server (port 5000) and frontend development server (port 3000) simultaneously.

5. **Access the application**:
   - After running `npm run dev`, wait for both servers to start (you'll see "Compiled successfully" for the frontend)
   - **Method 1**: Click on the port notification that appears in the bottom-right corner (port 3000)
   - **Method 2**: Go to the **Ports** tab in VS Code (usually at the bottom), find port **3000**, and click the 🌐 icon or right-click → "Open in Browser"
   - **Method 3**: Look for a message like "On Your Network: http://xxx-3000.app.github.dev" in the terminal and copy that URL
   - The frontend will automatically connect to the backend using the correct Codespace URL - no manual configuration needed!
   
   **Note**: In Codespace, the browser doesn't open automatically. You need to manually open the port URL from the Ports tab or notification.

**Note:** The `.env` file is optional. The server uses default values (PORT=5000, JWT_SECRET=default) if no `.env` file exists.

### Local Development Setup

#### Installation

1. Install all dependencies (root, server, and client):
```bash
npm run install-all
```

2. Start the development servers (run this command in the **root directory**):
```bash
npm run dev
```

This will start both the backend server (port 5000) and the frontend development server (port 3000) simultaneously using `concurrently`.

### Manual Setup (Alternative)

If you prefer to set up manually:

1. Install root dependencies:
```bash
npm install
```

2. Install server dependencies:
```bash
cd server
npm install
cd ..
```

3. Install client dependencies:
```bash
cd client
npm install
cd ..
```

4. Start the backend server:
```bash
cd server
npm run dev
```

5. In a new terminal, start the frontend:
```bash
cd client
npm start
```

## Environment Variables

The `.env` file is **optional**. The server uses default values if no `.env` file exists:
- `PORT=5000` (default)
- `JWT_SECRET=your-secret-key-change-in-production` (default)

To customize these values, create a `.env` file in the `server` directory:

```
PORT=5000
JWT_SECRET=your-secret-key-change-in-production
```

**Note:** In production, always set a strong `JWT_SECRET` value.

## Project Structure

```
FitnessPoint/
├── server/                 # Backend code
│   ├── src/
│   │   ├── index.ts       # Server entry point
│   │   ├── database.ts    # Database initialization
│   │   ├── middleware/    # Auth middleware
│   │   └── routes/        # API routes
│   └── package.json
├── client/                 # Frontend code
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── pages/         # Page components
│   │   ├── context/       # React context
│   │   └── App.tsx        # Main app component
│   └── package.json
└── package.json           # Root package.json (contains npm run dev)
```

**Important:** Always run `npm run dev` from the **root directory**, not from `server/` or `client/` directories. The root `package.json` uses `concurrently` to start both servers simultaneously.

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user

### Users
- `GET /api/users/me` - Get current user profile
- `PUT /api/users/me` - Update user profile
- `GET /api/users/:id` - Get user by ID
- `POST /api/users/:id/follow` - Follow a user
- `DELETE /api/users/:id/follow` - Unfollow a user

### Posts
- `GET /api/posts` - Get all posts (feed)
- `POST /api/posts` - Create a new post (with optional image)
- `PUT /api/posts/:id` - Update a post (owner only)
- `DELETE /api/posts/:id` - Delete a post (owner only)
- `POST /api/posts/:id/like` - Like/unlike a post
- `GET /api/posts/:id/comments` - Get comments for a post
- `POST /api/posts/:id/comments` - Add a comment to a post

### Calories
- `POST /api/calories/calculate` - Calculate calorie needs
- `POST /api/calories/suggest-foods` - Get food suggestions based on calorie needs and dietary preferences

### Fitness
- `GET /api/fitness/tips?goal=lose|maintain|gain` - Get fitness tips
- `GET /api/fitness/exercises?goal=lose|maintain|gain` - Get exercises

## Database Schema

The application uses SQLite with the following tables:
- `users` - User accounts and profiles
- `posts` - Social media posts (with optional image_url)
- `comments` - Comments on posts
- `likes` - Likes on posts
- `follows` - User follow relationships
- `foods` - Food database with nutritional information and dietary tags

## License

MIT
