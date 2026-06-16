# CineHub — Flutter Movie App (TMDB)

A complete movie discovery app: trending/popular/top-rated/upcoming lists, search, detail pages with cast & recommendations, and a favorites list.

## Setup

1. Get a free API key at https://www.themoviedb.org/settings/api (v3 auth)
2. Open `lib/services/tmdb_service.dart` and replace:
   ```dart
   static const String _apiKey = 'YOUR_TMDB_API_KEY';
   ```
3. Install dependencies:
   ```
   flutter pub get
   ```
4. Run:
   ```
   flutter run
   ```

## Project Structure

```
lib/
├── main.dart                  # App entry, theme, bottom nav
├── models/
│   └── movie.dart              # Movie, MovieDetail, Genre, CastMember
├── services/
│   ├── tmdb_service.dart       # All TMDB API calls
│   └── favorites_provider.dart # Favorites state (Provider)
├── screens/
│   ├── home_screen.dart        # Trending/Popular/Top Rated/etc rows
│   ├── search_screen.dart      # Debounced live search
│   ├── movie_detail_screen.dart# Full detail + cast + recommendations
│   └── favorites_screen.dart   # Saved movies grid
└── widgets/
    ├── movie_card.dart         # Poster card with rating badge
    └── movie_section.dart      # Horizontal scroll section
```

## Features

- Trending, Now Playing, Popular, Top Rated, Upcoming rows
- Featured backdrop banner
- Live search with debounce
- Movie detail: backdrop, overview, genres, runtime, rating, cast carousel
- "You might also like" recommendations
- Favorites with heart toggle (in-memory via Provider)
- Cached network images, dark theme

## Notes

- Favorites are in-memory only (reset on app restart). To persist, add `shared_preferences` or `sqflite`.
- For production, don't hardcode the API key in source — use `--dart-define` or a `.env` file with `flutter_dotenv`.
