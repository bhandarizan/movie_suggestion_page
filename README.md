
# Movie Search & Display
>>>>>>> 85a4645 (properly written Readme)

A modern, responsive movie search and discovery application built with React. Search through thousands of movies, discover trending films, and track your search history with a sleek, user-friendly interface.

## Overview

Movie Search & Display is a full-stack web application that allows users to search for movies, view detailed information, and discover trending movies. The app integrates with The Movie Database (TMDB) API for comprehensive movie data and uses Appwrite as a backend service to track and display trending searches.

## Features

- **🔍 Search Movies**: Search through thousands of movies with debounced input for optimal performance
- **🎬 Movie Details**: View comprehensive movie information including:
  - Title, release date, and rating
  - Original language
  - Movie poster and images
  - Votes and ratings
- **📈 Trending Section**: See the most searched movies based on user search history
- **⚡ Real-time Updates**: Automatic search count tracking in the database
- **🎯 Debounced Search**: Prevents excessive API calls while typing
- **📱 Responsive Design**: Works seamlessly across all devices
- **⌚ Loading States**: Spinner component for better UX during data fetching
- **🛡️ Error Handling**: Graceful error messages and fallback UI

## Tech Stack

### Frontend
- **React** `19.1.0` - UI library
- **Vite** `6.3.5` - Build tool and dev server
- **Tailwind CSS** - Utility-first CSS framework (via @tailwindcss/vite)

### Backend & Database
- **TMDB API** - Movie data provider
- **Appwrite** `18.1.1` - Backend-as-a-Service for database and search tracking

### Development Tools
- **ESLint** - Code linting and quality
- **Vite Plugins** - React plugin for JSX support

## Project Structure

```
movie_search_display/
├── src/
│   ├── components/
│   │   ├── MovieCard.jsx       # Individual movie card component
│   │   ├── Search.jsx          # Search input component
│   │   └── Spinner.jsx         # Loading spinner component
│   ├── App.jsx                 # Main application component
│   ├── appwrite.js             # Appwrite configuration and utilities
│   ├── main.jsx                # React entry point
│   ├── App.css                 # Application styles
│   └── index.css               # Global styles
├── public/                      # Static assets
├── index.html                  # HTML entry point
├── package.json                # Dependencies and scripts
├── vite.config.js              # Vite configuration
├── eslint.config.js            # ESLint configuration
└── README.md                   # This file
```

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn package manager

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd movie_search_display
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env.local` file in the root directory with your API credentials:
```env
VITE_TMDB_API_KEY=your_tmdb_api_key_here
VITE_APPWRITE_PROJECT_ID=your_appwrite_project_id
VITE_APPWRITE_DATABASE_ID=your_appwrite_database_id
VITE_APPWRITE_COLLECTION_ID=your_appwrite_collection_id
```

### Configuration

#### TMDB API Setup
1. Visit [The Movie Database (TMDB)](https://www.themoviedb.org/) and create an account
2. Generate an API key from your account settings
3. Add the key to your `.env.local` as `VITE_TMDB_API_KEY`

#### Appwrite Setup
1. Create an account at [Appwrite Cloud](https://cloud.appwrite.io/)
2. Create a new project and database
3. Create a collection for storing search history
4. Add the following attributes to your collection:
   - `searchTerm` (String)
   - `count` (Integer)
   - `movie_id` (Integer)
   - `poster_url` (String)
5. Add the credentials to your `.env.local`

## Development

### Run Development Server
```bash
npm run dev
# or
npm start
```

The application will be available at `http://localhost:5173/`

### Build for Production
```bash
npm run build
```

### Preview Production Build
```bash
npm preview
```

### Lint Code
```bash
npm run lint
```

## How It Works

### Search Flow
1. User types in the search input
2. Input is debounced for 500ms to avoid excessive API calls
3. App fetches movies from TMDB API based on search query
4. Search term and first result are tracked in Appwrite database
5. Results are displayed in a grid of movie cards

### Trending Movies
1. On app load, trending movies are fetched from Appwrite
2. Movies are sorted by search count in descending order
3. Top 7 trending movies are displayed in the trending section

### State Management
- **searchTerm**: Current user input
- **debouncedSearchTerm**: Debounced search term used for API calls
- **movieList**: Array of search/discover results
- **trendingMovies**: Array of top trending movies
- **isLoading**: Loading state for async operations
- **errorMessage**: Error message if API call fails

## Key Components

### `App.jsx`
Main application component that handles:
- State management
- API integration with TMDB
- Debouncing search input
- Fetching trending movies
- Error handling

### `MovieCard.jsx`
Displays individual movie information:
- Movie poster
- Title
- Rating
- Release year
- Original language

### `Search.jsx`
Search input component with:
- Text input field
- Search icon
- Real-time value binding

### `Spinner.jsx`
Loading indicator displayed during API calls

## API Integration

### TMDB Endpoints Used
- **Search Movies**: `/search/movie?query={query}`
- **Discover Movies**: `/discover/movie?sort_by=popularity.desc`

### Appwrite Operations
- **updateSearchCount()**: Tracks or updates search queries
- **getTrendingMovies()**: Retrieves top searched movies

## Features in Detail

### Debounced Search
The app uses a 500ms debounce delay to prevent excessive API calls while typing. This improves performance and reduces unnecessary network traffic.

### Error Handling
- Network errors display user-friendly messages
- Invalid responses are caught and logged
- Loading states prevent UI inconsistencies

### Responsive Design
The application is built with Tailwind CSS to be fully responsive across:
- Mobile devices
- Tablets
- Desktop screens

## Future Enhancements

- [ ] Movie detail page with full information
- [ ] Watchlist/favorites feature
- [ ] User authentication and personalized recommendations
- [ ] Filter by genre, release year, rating
- [ ] Dark/light theme toggle
- [ ] Advanced search filters
- [ ] Social sharing features

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Troubleshooting

### Movies not loading
- Verify your TMDB API key is correct and active
- Check network connectivity
- Check browser console for error messages

### Trending section not showing
- Ensure Appwrite credentials are correct
- Verify collection structure matches the expected schema
- Check that database permissions allow read/write operations

### Search not working
- Clear browser cache
- Check that environment variables are properly loaded
- Verify TMDB API key has search endpoint access

## License

This project is open source and available under the MIT License.

## Acknowledgments

- [The Movie Database (TMDB)](https://www.themoviedb.org/) for the comprehensive movie API
- [Appwrite](https://appwrite.io/) for the backend-as-a-service platform
- [React](https://react.dev/) for the UI library
- [Tailwind CSS](https://tailwindcss.com/) for the CSS framework
- [Vite](https://vitejs.dev/) for the build tool

## Support

For questions or issues, please open an issue on the GitHub repository or contact the development team.

---

**Made with ❤️ by Rizan Bhandari**
