---
title: Spot Hub
layout: layouts/base.njk
---

<div class="flex flex-col items-center text-md  mb-8">

  <div class="flex flex-col mb-8 text-sm">
    <a href="https://spot-hub.app" class="mb-4">
      <img src="/assets/spot-hub-heading.png" alt="Spot Hub" height="80" class="h-20">
    </a>
    <a href="https://spot-hub.app" class="text-blue-600 hover:text-blue-800 font-medium mb-6">spot-hub.app</a>
    <p class="mb-4">
      <strong>A Progressive Web App for mapping skateboarding spots and skateboarding media across the globe.</strong>
    </p>
    <p class="text-gray-700 mb-4">
      Currently in Alpha Release phase, Spot Hub is a project I plan to release publicly later this year to fill a gap in the skateboarding community for discovering locations and street obstacles worldwide and the history of tricks done at each spot.
    </p>
  </div>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">Objectives</h2>
    <ul class="list-disc pl-6 space-y-2 text-md">
      <li class="text-sm"><strong>Optimised Performance:</strong> Ensure fast, smooth and lag-free rendering of thousands — potentially tens of thousands — of map pins around the world.</li>
      <li><strong>Streamlined Content Management:</strong> Simplify the process of adding spots, images, and related information.</li>
      <li><strong>Intuitive Discovery:</strong> Enable effortless filtering of spots and search functionality.</li>
      <li><strong>Cross-Platform Compatibility:</strong> Full functionality across Web, Android, and iOS devices.</li>
      <li><strong>Cost-Efficient Scalability:</strong> Scale dynamically while minimising infrastructure expenses.</li>
    </ul>
  </section>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">Technical Implementation</h2>
    <p class="mb-6">An overview of the technologies used and why they were selected</p>
    
    <div class="grid md:grid-cols-2 gap-6 text-sm">
      <div>
        <h3 class="text-md font-bold mb-3">React</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Modern Javascript Library for building reusable UI components</li>
          <li>Has a rich developer community and ecosystem of compatible libraries</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">NextJS</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>React-based framework for simple implementation of SSR for faster page load times and improved SEO</li>
          <li>Server Components for automatic code splitting and faster data fetching</li>
          <li>Server Actions for faster, secure, cached calls to the database</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">Jotai</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Lightweight, simple, atomic State Management library for global state</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">MapLibre GL</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Free, Open Source WebGL Mapping Library (fork of MapBox) for smooth map rendering using GPU acceleration</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">DeckGL</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>WebGL visualisation library for a highly scalable map pin layer using GPU acceleration</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">Supabase</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Open Source Serverless PostgreSQL database allowing for affordable demand-based scalability</li>
          <li>PostGIS extension for performant GeoSpatial data querying and indexing</li>
          <li>PostgreSQL functions for complex querying</li>
          <li>Row Level Security for granular role-based database access</li>
          <li>Automatically built RESTful API's reduces the need to manage my own CRUD endpoints</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">Mega</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>For automated database back-up synced to the cloud</li>
        </ul>
      </div>
      <div>
        <h3 class="text-md font-bold mb-3">Google OAuth</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Simple, secure User Authentication without the need to store users passwords</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">Yup</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Form validation library to prevent errors and improve user experience</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">Cloudinary CDN</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Fast, scalable Media Management Store with low latency worldwide</li>
          <li>Powerful API's for image and video transformation and optimisation - used for compressing assets and adding watermarks on upload</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">React Intersection Observer</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>For lazy loading images below the fold to improve page load speeds</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">React Icons</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Suite of SVG icons for lightweight, SEO-friendly, vector-based icons</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">ShadCN</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Customisable React Component Library with built in accessibility</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">TailwindCSS</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Lightweight, performance-optimised CSS Design System to aid in consistent styling and rapid development</li>
        </ul>
        
        <h3 class="text-md font-bold mt-4 mb-3">DexieJS</h3>
        <ul class="list-disc pl-6 space-y-1">
          <li>Minimalistic IndexedDB library used for caching data locally on users devices for reducing page load speeds for returning users</li>
        </ul>
      </div>
    </div>
  </section>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">Performance Optimisations</h2>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">WebGL</h3>
    <p class="mb-4">
      Many JavaScript map libraries use DOM nodes to render map layers, such as map pins. However, this approach lacks scalability as maps with thousands of pins will suffer from sluggish performance. Instead, Spot Hub uses DeckGL, a WebGL library that leverages GPU acceleration for significantly faster rendering and smoother interactivity, resulting in a highly scalable map pin layer.
    </p>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Images</h3>
    <ul class="list-disc pl-6 space-y-2">
      <li><strong>CDN Delivery:</strong> Spot Hub uses Cloudinary to store images as their CDN provides low-latency delivery worldwide</li>
      <li><strong>Image size:</strong> Cloudinary is configured to automatically optimise images as they are uploaded (a feature available to admin users only). Images are compressed, converted to WebP format, resized to a maximum dimension of 1000px, as well as watermarked with the Spot Hub logo</li>
      <li><strong>Thumbnails:</strong> Thumbnail versions of spot images are automatically generated by Cloudinary (200x200px) to provide a faster-loading preview image for each each spot</li>
      <li><strong>Lazy Loading:</strong> A combination of the Intersection Observer API and lazy-loading attribute (using NextJS Image component) are used to reduce the number of images loaded on initial page load</li>
      <li><strong>SVG Icons:</strong> SVG's are used for icons throughout Spot Hub to provide light-weight and styleable vector icons that reduce HTTP requests, improve rendering performance, and scale perfectly across all devices</li>
      <li><strong>Service Worker:</strong> Caches images using the browser cache API to reduce HTTP requests</li>
    </ul>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Data Pre-Fetching and Caching Strategy</h3>
    <p class="mb-4">
      Spot Hub uses a grid-based system for data fetching in order to simplify data caching. Each grid square has a unique ID based on its' coordinates. On initial page load, two concurrent requests for spot data are made to the database:
    </p>
    
    <ol class="list-decimal pl-6 space-y-2 mb-4">
      <li>Fetch a shallow set of spot data for all spots worldwide. Shallow spot data provides enough data to display map pins and their thumbnails but does not contain all the data about each spot. If there are over 5000 spots worldwide (~1MB shallow data) then multiple paginated requests are made to the database until all spots are fetched. Fetching this shallow spot data up front means that browsing, filtering and displaying map pins worldwide is instant.</li>
      <li>Pre-fetch complete spot data for grid squares overlapping the visible search area. This could be the users' viewport, or in the example below, is a 25km search radius (pre-fetched grid squares highlighted in green). Grid square ID's along with timestamp and cache depth (shallow or complete) are stored in IndexedDB to prevent future duplicate requests for the same grid squares.</li>
    </ol>
    
    <div class="my-6">
      <img src="/assets/spot-data-fetching-2.jpg" alt="Spot data fetching visualization" class="rounded-lg shadow-md w-full">
    </div>
    
    <p class="mb-4">
      As the user moves their search area (or viewport) around the map, map pins are instantly displayed using the shallow spot data and full spot data is pre-fetched in the background after determining which grid squares have not been previously fetched (shown in orange below). These orange grid square ID's are then cross referenced with the shallow spot data to determine which ones contain spots and only make a database request if any grid squares contain spots, preventing unnecessary calls to the database.
    </p>
    
    <p class="mb-4">
      If the user interacts with a map pin before the pre-fetched full spot data has been received then a request is made to the database for that single spot data.
    </p>
    
    <p class="mb-4">
      In order to prevent requesting too many grid squares at once when the user zooms out on the map, grid squares are only requested below a certain zoom level.
    </p>
    
    <div class="my-6">
      <img src="/assets/spot-data-fetching-3.jpg" alt="Spot data fetching visualization" class="rounded-lg shadow-md w-full">
    </div>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Local-First Caching Strategy</h3>
    <div class="my-6">
      <img src="/assets/spot-hub-caching.png" alt="Spot Hub caching strategy" class="rounded-lg shadow-md w-full">
    </div>
    
    <p class="mb-2">The flow for fetching spot data:</p>
    <ol class="list-decimal pl-6 space-y-1">
      <li>Check IndexedDB <br/>
        1.a. If found, check cache timestamp <br/>
        1.b. If data is not stale return data, otherwise continue</li>
      <li>Call to Server Action (running on Netlify Edge Server)</li>
      <li>Check Redis cache <br/>
        3.a. If found, check cache timestamp <br/>
        3.b. If data is not stale return data, otherwise continue</li>
      <li>HTTP fetch to Supabase <br/>
        4.a. Edge Server checks in-memory cache for previous matching request <br/>
        4.b. If found, check cache timestamp <br/>
        4.c. If data is not stale return data, otherwise continue <br/></li>
      <li>Request made to Supabase</li>
    </ol>
  </section>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">User Experience</h2>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Image Geolocation</h3>
    <p class="mb-4">
      The user experience of adding spots around the globe is streamlined by extracting image geolocation data (if available) to automatically move map pins to their correct location.
    </p>
    
    <div class="my-6">
      <img src="/assets/spot-upload.gif" alt="Spot upload demonstration" class="rounded-lg shadow-md w-full">
    </div>
    
    <p class="mb-4">
      The batch upload features allows up to 50 images to be selected at once. It uses image geolocation data to automatically group images in close proximity together (i.e. photos of the same spot). A drag and drop interface then allows the user to make any corrections to the groups before creating each spot individually.
    </p>
    
    <div class="my-6">
      <img src="/assets/batch-upload.gif" alt="Batch upload demonstration" class="rounded-lg shadow-md w-full">
    </div>
  </section>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">CI/CD</h2>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Staging and Production Environments</h3>
    <p>
      Using Netlify and Github I have a very simple CI/CD workflow that automatically deploys commits to my Production or Staging Environments when changes are merged into to the <code class="bg-gray-100 px-1 rounded">main</code> or <code class="bg-gray-100 px-1 rounded">staging</code> branches. I also have a Staging and Production instance of the Supabase database to avoid any accidental or breaking changes made to the Production database during development.
    </p>
  </section>

  <section class="mb-8 text-sm">
    <h2 class="text-xl font-bold mb-4 border-b pb-2">Next Steps</h2>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Beta Release Goals</h3>
    <ul class="list-disc pl-6 space-y-2">
      <li><strong>Instagram Integration</strong><br/>
        Integration with Instagram API to display related posts for each map pin</li>
      <li><strong>Youtube Integration</strong><br/>
        Integration with Youtube API to display related segment of Youtube videos for each map pin</li>
      <li><strong>Facebook Auth</strong><br/>
        Add Facebook Auth and make it the default login option as it affects Instagram API limits</li>
      <li><strong>Code Rabbit</strong><br/>
        For AI powered code reviews</li>
      <li><strong>PostHog</strong><br/>
        For Web Analytics, session recording and A/B testing</li>
      <li><strong>Improve Test Coverage</strong><br/>
        Implement <strong>Vitest</strong> for unit tests<br/>
        Implement <strong>React Testing Library</strong> for integration tests<br/>
        Implement <strong>Playwright/Cypress</strong> for end-to-end tests<br/>
        Integrate automated tests into CI/CD pipeline</li>
      <li><strong>Stripe</strong><br/>
        For handling a tiered pricing model to advanced app features</li>
    </ul>
    
    <h3 class="text-xl font-semibold mt-6 mb-3">Speculative Future Enhancements</h3>
    <ul class="list-disc pl-6 space-y-2">
      <li><strong>Legend State</strong> or <strong>Zero Sync</strong> for local-first database syncing</li>
      <li><strong>JSDoc</strong> or <strong>TypeScript</strong> for type checking as the app grows in complexity</li>
      <li><strong>Remix</strong> as a more performant alternative to NextJS</li>
      <li><strong>Svelte</strong> or <strong>SolidJS</strong> as a more performant alternative to React</li>
    </ul>
  </section>
</div>
