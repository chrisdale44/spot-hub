<img src="/assets/spot-hub-heading.png" height="80px">

A Progressive Web App for mapping skateboarding spots and skateboarding media across the globe - a current gap in the skateboarding community which has not been filled by any of the existing solutions. Spot Hub is a project I've been wanting to build for many years and has been an excellent learning experience to complete an MVP version.

## MVP Objectives

- **Optimized Performance:** Ensure smooth, lag-free rendering of thousands — potentially tens of thousands — of map pins around the globe.

- **Streamlined Content Management:** Simplify the process of adding spots, images, and related information.

- **Intuitive Discovery:** Enable effortless spot filtering and search functionality.

- **Offline Accessibility:** Deliver a seamless user experience even without an internet connection.

- **Cross-Platform Compatibility:** Full functionality across Web, Android, and iOS devices.

## Technical Implementation

An overview of the technologies used and why they were selected

- **React 18**
  - Modern Javascript Library for building reusable UI components
  - Has a rich developer community and ecosystem of compatible libraries
- **NextJS 15**
  - React-based framework for simple implementation of SSR for faster page load times and improved SEO
  - Server Components for automatic code splitting and faster data fetching
  - Server Actions for faster, secure, cached calls to the database
- **Jotai**
  - Lightweight, simple, atomic State Management library for global state
- **MapLibre**
  - Free, Open Source Mapping Library (fork of MapBox) with great user experience
- **DeckGL**
  - WebGL-powered visualisation library for a highly scalable map pins layer using GeoJSON
- **Supabase**
  - Open Source PostgreSQL cloud database with automatically built RESTful API's
  - PostGIS extension for performant GeoSpatial data querying and indexing
  - PostgreSQL functions for complex querying
  - Row Level Security for granular role-based database access
- **Mega**
  - For automated database back-up syncing to the cloud
- **Google OAuth**
  - Secure, trusted User Authentication
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

## Technical Challenges

### Spot Thumbnails on Mobile

## Cool Features

### Image GeoLocation

In order to streamline the user experience of adding pins to the map, the image upload feature uses image geolocation data (if available) to automatically move map pins to the correct location.

![](/assets/spot-upload.gif)

#### Image Batch Uploads

To streamline the process of uploading batches of images, geolocation data is extracted from each image and used to group images together that are in close proximity to each other as they are likely multiple images of the same spot. A drag and drop interface then allows the user to make any corrections to the groups before creating each spot individually.

![](/assets/batch-upload.gif)

### Data Pre-Fetching and Caching Strategy

Spot Hub uses a grid-based system for data fetching in order to simplify caching and increase the likelihood of there being cached results when fetching data. Each grid square has a unique ID based on its' coordinates. Two types of spot data fetches are made to the database: shallow and deep. Shallow spot data provides enough data to display map pins and their thumbnails, whereas deep spot data provides all data about a spot. The easiest way to show how spot data is pre-fetched is using a search radius area, as shown below:

![](/assets/spot-data-fetching.jpg)

When the page initially loads, a bounding box of relevant grid squares is calculated (shown in green below) based on the selected/default search area. A deep request is made to the database for this data so that when the user interacts with map pins in this search area, no time is spent waiting for spot data to load. Upon successful response from the database, the data and list of corresponding grid square IDs, are stored in app state and cached in indexedDB along with a cache timestamp.

At the same time this deep request is being made, a second request is also made to the database in the background to shallow fetch a copy of _all_ spot data (providing one is not already found in cache).

![](/assets/spot-data-fetching-2.jpg)

As the user moves the search area around the map, map pins are instantly displayed using the shallow spot data already available. The cached list of grid ID's is used to determine which grid squares already has freshly-cached deep spot data, and which need to be requested from the database (shown in orange below). Using an array of bounding boxes, a single request is then made to the database to deep fetch data for the orange area only, reducing the amount of data transferred and thus request latency too.

![](/assets/spot-data-fetching-3.jpg)

### Offline-First Caching Strategy

## Deprecated Tech

Libraries implemented but later removed or replaced with better alternatives

- **LeafletJS**
  - The standard choice of free, Open Source map libraries but I found it to be buggy and required too much patching to work as desired
- **Google Maps**
  - The leading, most advanced Javascipt maps library. Deprecated in favour of the free, Open Source solution, MapLibre, due to concerns regarding affordability of Google Maps services at scale
- **PixiJS**
  - A WebGL library for rendering 2D graphics, initially used for rendering map pins over the top of LeafletJS via my own custom middleware. However, after switching to Google Maps, DeckGL appeared to be the standard, easier WebGL library to integrate which didn't require any custom middleware
- **PlanetScale**
  - Highly performant MySQL cloud database. After they sunset their generous free plan I looked to other database options and settled on Supabase which worked out for the best due to Postgres' powerful Geospatial library, POSTGis
- **DrizzleORM**
  - Used for handling SQL queries to PlanetScale and migration generation but no longer needed after switching to Supabase
- **SendGrid**
  - Email API service used to handle passwordless 'magic-link' sign-in. Deprecated in favour of using OAuth.

## Next Steps

### Alpha Release Known Issues

- Offline-first not working fully
- Improve offline fallbacks
- Improve loading states and add a loading screen animation
- Improve UX of side nav filters, especially tags
- Improve security of form fields against XSS and DDOS attacks
- Fix Modal top margin on mobile
- Reduce inital page load speeds, add further code splitting by lazy loading client components
- Geolocation extraction from uploaded images not working on mobile
- Upgrade React version once other libraries add support

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
- **Stripe**
  - For handling a tiered pricing model to advanced app features

### Speculative Future Enhancements

- **Legend State** or **Zero Sync** for local-first database syncing
- **Remix** as a more performant alternative to NextJS
- **Svelte** or **SolidJS** as a more performant alternative to React
