# Recipe App

[![JavaScript](https://img.shields.io/badge/Primary%20Language-JavaScript-yellow)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Node.js](https://img.shields.io/badge/Runtime-Node.js-green)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Project Overview

The Recipe App is a full-stack web application that allows users to discover, search, save, and manage their favorite recipes. Built with modern JavaScript technologies, this application provides a seamless user experience for food enthusiasts to explore culinary possibilities. The app features a responsive design, real-time search functionality, user authentication, and a comprehensive recipe management system.

## Features

### Core Functionality
- 🔍 **Advanced Recipe Search** - Search recipes by ingredients, cuisine type, dietary restrictions, and cooking time
- 📖 **Recipe Collection** - Browse through a diverse collection of recipes with detailed instructions
- ⭐ **Favorites System** - Save and organize favorite recipes for quick access
- 👤 **User Authentication** - Secure user registration, login, and profile management
- 📱 **Responsive Design** - Optimized for desktop, tablet, and mobile devices

### Advanced Features
- 🏷️ **Recipe Categories** - Organized categorization by meal type, cuisine, and difficulty level
- 📊 **Nutritional Information** - Detailed nutritional breakdown for each recipe
- 🛒 **Shopping Lists** - Generate shopping lists from selected recipes
- 📝 **Recipe Reviews** - Rate and review recipes with community feedback
- 🔄 **Recipe Sharing** - Share favorite recipes with other users

## Tech Stack

### Frontend
- **Language**: JavaScript (ES6+)
- **Framework/Library**: React.js / Vanilla JavaScript
- **Styling**: CSS3, SCSS/Sass
- **Build Tool**: Webpack / Vite
- **Package Manager**: npm

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB / PostgreSQL
- **Authentication**: JWT (JSON Web Tokens)
- **API**: RESTful API architecture

### Development Tools
- **Version Control**: Git
- **Code Quality**: ESLint, Prettier
- **Testing**: Jest, Cypress
- **Deployment**: Docker, CI/CD pipeline

## Folder Structure

```
Recipe-app/
├── client/                 # Frontend application
│   ├── src/
│   │   ├── components/     # Reusable React components
│   │   ├── pages/          # Application pages/views
│   │   ├── hooks/          # Custom React hooks
│   │   ├── services/       # API service functions
│   │   ├── utils/          # Utility functions
│   │   ├── styles/         # CSS/SCSS stylesheets
│   │   └── App.js          # Main application component
│   ├── public/             # Static assets
│   └── package.json        # Frontend dependencies
├── server/                 # Backend application
│   ├── controllers/        # Route controllers
│   ├── models/             # Database models
│   ├── routes/             # API route definitions
│   ├── middleware/         # Custom middleware
│   ├── config/             # Configuration files
│   ├── utils/              # Server utility functions
│   ├── tests/              # Server-side tests
│   ├── server.js           # Main server file
│   └── package.json        # Backend dependencies
├── public/                 # Shared static assets
├── docs/                   # Documentation files
├── .gitignore              # Git ignore rules
├── .env.example            # Environment variables template
├── docker-compose.yml      # Docker configuration
└── README.md               # Project documentation
```

## API Endpoints

### Authentication Endpoints
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | User registration | No |
| POST | `/api/auth/login` | User login | No |
| POST | `/api/auth/logout` | User logout | Yes |
| GET | `/api/auth/profile` | Get user profile | Yes |
| PUT | `/api/auth/profile` | Update user profile | Yes |

### Recipe Endpoints
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/recipes` | Get all recipes | No |
| GET | `/api/recipes/:id` | Get recipe by ID | No |
| POST | `/api/recipes` | Create new recipe | Yes |
| PUT | `/api/recipes/:id` | Update recipe | Yes |
| DELETE | `/api/recipes/:id` | Delete recipe | Yes |
| GET | `/api/recipes/search` | Search recipes | No |
| GET | `/api/recipes/category/:category` | Get recipes by category | No |

### Favorites Endpoints
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/favorites` | Get user's favorite recipes | Yes |
| POST | `/api/favorites/:recipeId` | Add recipe to favorites | Yes |
| DELETE | `/api/favorites/:recipeId` | Remove from favorites | Yes |

### Review Endpoints
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/reviews/:recipeId` | Get recipe reviews | No |
| POST | `/api/reviews/:recipeId` | Add recipe review | Yes |
| PUT | `/api/reviews/:reviewId` | Update review | Yes |
| DELETE | `/api/reviews/:reviewId` | Delete review | Yes |

## Installation & Setup

### Prerequisites
- Node.js (version 14.0 or higher)
- npm (version 6.0 or higher)
- MongoDB or PostgreSQL database
- Git

### Step-by-Step Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Clou-D-Walker/Recipe-app.git
   cd Recipe-app
   ```

2. **Install Dependencies**
   ```bash
   # Install backend dependencies
   cd server
   npm install
   
   # Install frontend dependencies
   cd ../client
   npm install
   ```

3. **Environment Configuration**
   ```bash
   # Copy environment template
   cp .env.example .env
   
   # Edit .env file with your configuration
   # DATABASE_URL=your_database_connection_string
   # JWT_SECRET=your_jwt_secret_key
   # PORT=3000
   ```

4. **Database Setup**
   ```bash
   # For MongoDB (if using MongoDB)
   # Ensure MongoDB is running locally or provide cloud connection string
   
   # For PostgreSQL (if using PostgreSQL)
   # Create database and run migrations
   npm run migrate
   ```

5. **Start the Application**
   ```bash
   # Start backend server (from server directory)
   npm run dev
   
   # Start frontend application (from client directory)
   npm start
   ```

6. **Access the Application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

### Docker Setup (Alternative)
```bash
# Build and run with Docker Compose
docker-compose up --build
```

## Usage Examples

### Basic Recipe Search
```javascript
// Search for recipes by keyword
const searchRecipes = async (query) => {
  try {
    const response = await fetch(`/api/recipes/search?q=${query}`);
    const recipes = await response.json();
    return recipes;
  } catch (error) {
    console.error('Search failed:', error);
  }
};
```

### Add Recipe to Favorites
```javascript
// Add recipe to user's favorites
const addToFavorites = async (recipeId) => {
  try {
    const response = await fetch(`/api/favorites/${recipeId}`, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${authToken}`,
        'Content-Type': 'application/json'
      }
    });
    return await response.json();
  } catch (error) {
    console.error('Failed to add to favorites:', error);
  }
};
```

## Contributing Guidelines

We welcome contributions from the community! Please follow these guidelines:

### Getting Started
1. Fork the repository on GitHub
2. Clone your fork locally
3. Create a new branch for your feature or bug fix
4. Make your changes and commit them with descriptive messages
5. Push your branch to your fork
6. Submit a Pull Request

### Code Standards
- Follow ESLint and Prettier configurations
- Write meaningful commit messages
- Include tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

### Pull Request Process
1. **Create Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

2. **Make Changes**
   ```bash
   git add .
   git commit -m "Add amazing feature"
   ```

3. **Push Changes**
   ```bash
   git push origin feature/amazing-feature
   ```

4. **Submit Pull Request**
   - Provide clear description of changes
   - Reference any related issues
   - Include screenshots if applicable

### Code Review Guidelines
- All PRs require at least one approval
- Address reviewer feedback promptly
- Keep PRs focused and atomic
- Include relevant tests and documentation

## Testing

### Running Tests
```bash
# Run backend tests
cd server
npm test

# Run frontend tests
cd client
npm test

# Run end-to-end tests
npm run test:e2e
```

### Test Coverage
- Aim for at least 80% test coverage
- Include unit tests for utilities and components
- Add integration tests for API endpoints
- Write E2E tests for critical user flows

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### MIT License Summary
- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use
- ❌ Liability
- ❌ Warranty

## Contact Information

### Project Maintainer
**Clou-D-Walker**
- GitHub: [@Clou-D-Walker](https://github.com/Clou-D-Walker)
- Repository: [Recipe-app](https://github.com/Clou-D-Walker/Recipe-app)

### Support
- **Issues**: [GitHub Issues](https://github.com/Clou-D-Walker/Recipe-app/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Clou-D-Walker/Recipe-app/discussions)
- **Email**: Contact through GitHub profile

### Contributing
- **Pull Requests**: [Create PR](https://github.com/Clou-D-Walker/Recipe-app/pulls)
- **Feature Requests**: [Submit Issue](https://github.com/Clou-D-Walker/Recipe-app/issues/new)
- **Bug Reports**: [Report Bug](https://github.com/Clou-D-Walker/Recipe-app/issues/new)

---

## Acknowledgments

- Thanks to all contributors who have helped improve this project
- Special thanks to the open-source community for inspiration and tools
- Recipe data sources and API providers

## Changelog

For detailed changes and version history, see [CHANGELOG.md](CHANGELOG.md)

---

**⭐ If you find this project helpful, please consider giving it a star on GitHub!**
