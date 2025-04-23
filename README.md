<img src="/assets/spot-hub-heading.png" height="80px">

**A Progressive Web App for mapping skateboarding spots and skateboarding media across the globe.**

Currently in Alpha Release phase, Spot Hub is a project I plan to release publically later this year to fill a gap in the skateboarding community for discovering locations and street obstacles worldwide and the history of tricks done at each spot.

## Objectives

- **Optimised Performance:** Ensure fast, smooth and lag-free rendering of thousands — potentially tens of thousands — of map pins around the globe.

- **Streamlined Content Management:** Simplify the process of adding spots, images, and related information.

- **Intuitive Discovery:** Enable effortless filtering of spots and search functionality.

- **Cross-Platform Compatibility:** Full functionality across Web, Android, and iOS devices.

- **Cost-Efficient Scalability:** Scale dynamically while minimising infrastructure expenses.

## Technical Implementation

An overview of the technologies used and why they were selected

- **React**
  - Modern Javascript Library for building reusable UI components
  - Has a rich developer community and ecosystem of compatible libraries
- **NextJS**
  - React-based framework for simple implementation of SSR for faster page load times and improved SEO
  - Server Components for automatic code splitting and faster data fetching
  - Server Actions for faster, secure, cached calls to the database
- **Jotai**
  - Lightweight, simple, atomic State Management library for global state
- **MapLibre**
  - Free, Open Source Mapping Library (fork of MapBox) with great user experience
- **DeckGL**
  - WebGL-powered visualisation library for a highly scalable map pin layer using GeoJSON
- **Supabase**
  - Open Source Serverless PostgreSQL database allowing for affordable demand-based scalability
  - PostGIS extension for performant GeoSpatial data querying and indexing
  - PostgreSQL functions for complex querying
  - Row Level Security for granular role-based database access
  - Automatically built RESTful API's reduces the need to manage my own CRUD endpoints
- **Mega**
  - For automated database back-up synced to the cloud
- **Google OAuth**
  - Simple, secure User Authentication without the need to store users passwords
- **Yup**
  - Form validation library to prevent errors and improve user experience
- **Cloudinary CDN**
  - Fast, scalable Media Management Store with low latency worldwide
  - Powerful API's for image and video transformation and optimisation - used for compressing assets and adding watermarks on upload
- **React Intersection Observer**
  - For lazy loading images below the fold to improve page load speeds
- **React Icons**
  - Suite of SVG icons for lightweight, SEO-friendly, vector-based icons
- **ShadCN**
  - Customisable React Component Library with built in accessibility
- **TailwindCSS**
  - Lightweight, performance-optimised CSS Design System to aid in consistent styling and rapid development
- **DexieJS**
  - Minimalistic IndexedDB library used for caching data locally on users devices for reducing page load speeds for returning users
- **Redis** via **Upstash**
  - Highly available, infinitly scalable, ultra-low latency key-value data-store, used for caching common database queries for reducing initial page load speeds and calls to the database
- **Serwist**
  - A collection of JS Libraries for implementing PWA's with Service Workers, used to simplify service worker generation, caching strategies and offline support
- **Netlify**
  - Scalable serverless backend used for deploying my Production and Staging Enviroments
  - Simple Git based CI/CD for automatic builds and deploys when code is pushed to github
  - Built in CDN reduces page load speeds by delivering content from edge locations around the globe
- **Sentry**
  - Application Performance Monitoring and Error Tracking
- **ESLint** and **Prettier**
  - Code linting and formatting libraries used to improve code quality and maintainability
- **Git** and **Github**
  - For Version Controlling the codebase including feature branching and managing Production and Staging branches

## Performance Optimisations

### WebGL Layer

Many JavaScript map libraries use DOM nodes to render map layers, such as map pins. However, this approach lacks scalability as maps with thousands of pins will suffer from sluggish performance. Instead, Spot Hub uses DeckGL, a WebGL library that leverages GPU acceleration for significantly faster rendering and smoother interactivity, resulting in a highly scalable map pin layer.

### Images

Spot Hub uses Cloudinary to store images as their CDN provides low-latency delivery worldwide. Cloudinary is configured to automatically optimise images as they are uploaded (a feature available to admin users only). Images are compressed, converted to WebP format, resized to a maximum dimension of 1000px, and watermarked. Additionally, cropped thumbnail versions are generated to provide a smaller, optimised image for each spot.

Spot Hub also uses a combination of Intersection Observer and lazy-loading (using NextJS Image component) to reduce the number of images loaded and thus initial page load speeds.

### Data Pre-Fetching and Caching Strategy

Spot Hub uses a grid-based system for data fetching in order to simplify data caching. Each grid square has a unique ID based on its' coordinates. On initial page load, two concurrent requests for spot data are made to the database:

1. Fetch a shallow set of spot data for all spots worldwide. Shallow spot data provides enough data to display map pins and their thumbnails but does not contain all the data about each spot. If there are over 5000 spots worldwide (~1MB shallow data) then multiple paginated requests are made to the database until all spots are fetched. Fetching this shallow spot data up front means that browsing, filtering and displaying map pins worldwide is instant.
2. Pre-fetch complete spot data for grid squares overlapping the visible search area. This could be the users' viewport, or in the example below, is a 25km search radius (pre-fetched grid squares highlighted in green). Grid square ID's along with timestamp and cache depth (shallow or complete) are stored in IndexedDB to prevent future duplicate requests for the same grid squares.

![](/assets/spot-data-fetching-2.jpg)

As the user moves their search area (or viewport) around the map, map pins are instantly displayed using the shallow spot data and full spot data is pre-fetched in the background after determining which grid squares have not been previously fetched (shown in orange below). These orange grid square ID's are then cross referenced with the shallow spot data to determine which ones contain spots and only make a database request if any grid squares contain spots, preventing unnecessary calls to the database.

If the user interacts with a map pin before the pre-fetched full spot data has been received then a request is made to the database for that single spot data.

In order to prevent requesting too many grid squares at once when the user zooms out on the map, grid squares are only requested below a certain zoom level.

![](/assets/spot-data-fetching-3.jpg)

### Local-First Caching Strategy

![](/assets/spot-hub-caching.png)

The flow for fetching spot data:

1. Check IndexedDB <br/>
   1.a. If found, check cache timestamp <br/>
   1.b. If data is fresh return data, otherwise continue
2. Call to Server Action (running on Netlify Edge Server)
3. Check Redis cache <br/>
   3.a. If found, check cache timestamp <br/>
   3.b. If data is fresh return data, otherwise continue
4. HTTP fetch to Supabase <br/>
   4.a. Edge Server checks in-memory cache for previous matching request <br/>
   4.b. If found, check cache timestamp <br/>
   4.c. If data is fresh return data, otherwise continue <br/>
5. Request made to Supabase

## User Experience

### Image Geolocation

The user experience of adding spots around the globe is streamlined by extracting image geolocation data (if available) to automatically move map pins to their correct location.

![](/assets/spot-upload.gif)

The batch upload features allows up to 50 images to be selected at once. It uses image geolocation data to automatically group images in close proximity together (i.e. photos of the same spot). A drag and drop interface then allows the user to make any corrections to the groups before creating each spot individually.

![](/assets/batch-upload.gif)

## CI/CD

### Staging and Production Environments

Using Netlify and Github I have a very simple CI/CD workflow that automatically deploys commits to my Production or Staging Environments when changes are merged into to the `main` or `staging` branches. I also have a Staging and Production instance of the Supabase database to avoid any accidental or breaking changes made to the Production database during development.

## Next Steps

### Alpha Release Known Issues

- Offline-first not working fully
- Improve offline fallbacks
- Improve loading states and add a loading screen animation
- Improve security of form fields against XSS and DDOS attacks
- Fix Modal top margin on mobile
- Reduce inital page load speeds, add further code splitting by lazy loading client components

### Beta Release Goals

- **Instagram Integration**
  - Integration with Instagram API to display related posts for each map pin
- **Youtube Integration**
  - Integration with Youtube API to display related segment of Youtube videos for each map pin
- **Facebook Auth**
  - Add Facebook Auth and make it the default login option as it affects Instagram API limits
- **Code Rabbit**
  - For AI powered code reviews
- **PostHog**
  - For Web Analytics, session recording and A/B testing
- **Improve Test Coverage**
  - Implement **Vitest** for unit tests
  - Implement **React Testing Library** for integration tests
  - Implement **Playwright/Cypress** for end-to-end tests
  - Integrate automated tests into CI/CD pipeline
- **Stripe**
  - For handling a tiered pricing model to advanced app features

### Speculative Future Enhancements

- **Legend State** or **Zero Sync** for local-first database syncing
- **JSDoc** or **TypeScript** for type checking as the app grows in complexity
- **Remix** as a more performant alternative to NextJS
- **Svelte** or **SolidJS** as a more performant alternative to React
