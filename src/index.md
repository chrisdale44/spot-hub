---
title: Spot Hub
layout: layouts/base.njk
---

<div class="flex flex-col items-center text-md bg-white border-none focus:outline-none [box-shadow:rgba(0,_0,_0,_0.3)_0px_1px_4px_-1px] rounded">
  <div class="bg-[#157] flex align-center justify-center w-full">
    <a href="https://spot-hub.app">
      <h1 class="pacifico text-white text-4xl py-4">Spot Hub - Technical Overview</h1>
      <!-- <img src="/assets/spot-hub-heading.png" alt="Spot Hub" height="80" class="h-20"> -->
    </a>
  </div>
  <div class="px-8 pb-8">
    <div class="flex flex-col my-8 text-sm">
      <a href="https://spot-hub.app" class="text-blue-600 hover:text-blue-800 font-medium mb-6">spot-hub.app</a>
      <p class="mb-4">
        <strong>A Progressive Web App for mapping skateboarding spots and skateboarding media across the globe.</strong>
      </p>
      <p class="text-gray-700 mb-4">
        Currently in Alpha Release phase, Spot Hub is a project I plan to release publicly later this year to fill a gap in the skateboarding community for discovering locations and street obstacles worldwide and the history of tricks done at each spot.
      </p>
    </div>
    <section class="mb-8 text-sm w-full">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">Table of Contents</h2>
      <ol class="list-decimal pl-8">
      <li><a class="pl-1 hover:text-blue-600" href="#objectives">Objectives</a></li>
      <li><a class="pl-1  hover:text-blue-600" href="#technical-implementation">Technical Implementation</a></li>
      <li><a class="pl-1  hover:text-blue-600" href="#performance">Performance Optimisations</a></li>
      <li><a class="pl-1  hover:text-blue-600" href="#user-experience">User Experience</a></li>
      <li><a class="pl-1  hover:text-blue-600" href="#ci-cd">CI/CD</a></li>
      <li><a class="pl-1  hover:text-blue-600" href="#next-steps">Next Steps</a></li>
      </ol>
    </section>
    <section class="mb-8 text-sm w-full" id="objectives">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">Objectives</h2>
      <ul class="list-disc space-y-2 text-md px-8">
        <li class="text-sm"><strong>Optimised Performance:</strong> Ensure fast, smooth and lag-free rendering of thousands — potentially tens of thousands — of map pins around the world.</li>
        <li><strong>Streamlined Content Management:</strong> Simplify the process of adding spots, images, and related information.</li>
        <li><strong>Intuitive Discovery:</strong> Enable effortless filtering of spots and search functionality.</li>
        <li><strong>Cross-Platform Compatibility:</strong> Full functionality across Web, Android, and iOS devices.</li>
        <li><strong>Cost-Efficient Scalability:</strong> Scale dynamically while minimising infrastructure expenses.</li>
      </ul>
    </section>
    <section class="mb-8 text-sm w-full" id="technical-implementation">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">Technical Implementation</h2>
      <div class="text-sm px-4 overflow-x-auto">
    <table class="w-full border-collapse">
      <thead>
        <tr class="border-b border-gray-200">
          <th class="text-left py-3 px-4 font-bold w-1/3">Technology</th>
          <th class="text-left py-3 px-4 font-bold">Why it was selected</th>
        </tr>
      </thead>
      <tbody class="divide-y divide-gray-200">
        <tr>
          <td class="py-3 px-4 align-top font-semibold">React</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5 space-y-1">
              <li>Modern Javascript Library for building reusable UI components</li>
              <li>Rich developer community and ecosystem of compatible libraries</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">NextJS</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5 space-y-1">
              <li>React-based framework for SSR (faster page loads and better SEO)</li>
              <li>Server Components for automatic code splitting</li>
              <li>Server Actions for secure, cached database calls</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Jotai</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Lightweight atomic state management for global state</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">MapLibre GL</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Free WebGL mapping library (MapBox fork) for smooth GPU-accelerated rendering</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">DeckGL</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>WebGL visualization for scalable map pin layers with GPU acceleration</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Supabase</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5 space-y-1">
              <li>Open Source Serverless PostgreSQL with demand-based scaling</li>
              <li>PostGIS for optimised GeoSpatial data querying and indexing</li>
              <li>PostgreSQL functions for complex querying</li>
              <li>Row Level Security for granular role-based access control</li>
              <li>Automatically built RESTful API's reduces CRUD endpoint management</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Mega</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Automated database back-up synced to the cloud</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Google OAuth</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Simple, secure authentication without storing passwords</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Yup</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Form validation library to prevent errors and improve UX</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Cloudinary CDN</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5 space-y-1">
              <li>Global low-latency media delivery</li>
              <li>Powerful API's for automated image transformation and optimisation</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">React Intersection Observer</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Lazy loading images below the fold for faster page loads</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">React Icons</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Lightweight SVG icons that are SEO-friendly</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">ShadCN</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Customisable React components with built-in accessibility</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">TailwindCSS</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Utility-first CSS design system for rapid development and consistent styling</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">DexieJS</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>IndexedDB wrapper for local data caching to improve load times</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Redis (Upstash)</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Low-latency caching for common database queries</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Serwist</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>A collection of JS Libraries for implementing PWA's with Service Workers, used to simplify service worker generation, caching strategies and offline support</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Netlify</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5 space-y-1">
              <li>Serverless deployment with built-in CDN used for production/staging environments</li>
              <li>Git-based CI/CD for automatic deployments</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Sentry</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Error tracking and performance monitoring</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">ESLint/Prettier</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Code quality and formatting enforcement</li>
            </ul>
          </td>
        </tr>
        <tr>
          <td class="py-3 px-4 align-top font-semibold">Git/GitHub</td>
          <td class="py-3 px-4">
            <ul class="list-disc pl-5">
              <li>Version control used for feature branching and production/staging branch management</li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
    </section>
    <section class="mb-8 text-sm w-full" id="performance">
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
        <img src="/assets/spot-data-fetching-2.jpg" alt="Spot data fetching visualization" class="w-full">
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
        <img src="/assets/spot-data-fetching-3.jpg" alt="Spot data fetching visualization" class="w-full">
      </div>
      <h3 class="text-xl font-semibold mt-6 mb-3">Local-First Caching Strategy</h3>
      <div class="my-6">
        <img src="/assets/spot-hub-caching.png" alt="Spot Hub caching strategy" class="w-full">
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
    <section class="mb-8 text-sm w-full" id="user-experience">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">User Experience</h2>
      <h3 class="text-xl font-semibold mt-6 mb-3">Image Geolocation</h3>
      <p class="mb-4">
        The user experience of adding spots around the globe is streamlined by extracting image geolocation data (if available) to automatically move map pins to their correct location.
      </p>
      <div class="my-6">
        <img src="/assets/spot-upload.gif" alt="Spot upload demonstration" class="w-full">
      </div>
      <p class="mb-4">
        The batch upload features allows up to 50 images to be selected at once. It uses image geolocation data to automatically group images in close proximity together (i.e. photos of the same spot). A drag and drop interface then allows the user to make any corrections to the groups before creating each spot individually.
      </p>
      <div class="my-6">
        <img src="/assets/batch-upload.gif" alt="Batch upload demonstration" class="w-full">
      </div>
    </section>
    <section class="mb-8 text-sm w-full" id="ci-cd">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">CI/CD</h2>
      <h3 class="text-xl font-semibold mt-6 mb-3">Staging and Production Environments</h3>
      <p>
        Using Netlify and Github I have a very simple CI/CD workflow that automatically deploys commits to my Production or Staging Environments when changes are merged into to the <code class="bg-gray-100 px-1 rounded">main</code> or <code class="bg-gray-100 px-1 rounded">staging</code> branches. I also have a Staging and Production instance of the Supabase database to avoid any accidental or breaking changes made to the Production database during development.
      </p>
    </section>
    <section class="mb-8 text-sm w-full" id="next-steps">
      <h2 class="text-xl font-bold mb-4 border-b pb-2">Next Steps</h2>
      <h3 class="text-xl font-semibold mt-6 mb-3">Beta Release Goals</h3>
      <ul class="list-disc pl-6 space-y-2">
        <li><strong class="text-md font-bold mb-1">Instagram API Integration:</strong> To display related posts for each map pin</li>
        <li><strong class="text-md mt-1 font-bold mb-1">Youtube API Integration:</strong> To display related segment of Youtube videos for each map pin</li>
        <li><strong class="text-md mt-1 font-bold mb-1">Facebook Auth:</strong> Implement Facebook Auth and make it the default login option as it affects Instagram API limits</li>
        <li><strong class="text-md mt-1 font-bold mb-1">Code Rabbit:</strong> For AI powered code reviews</li>
        <li><strong class="text-md mt-1 font-bold mb-1">PostHog:</strong> For Web Analytics, session recording and A/B testing</li>
        <li><strong class="text-md font-bold mt-1 mb-1">Stripe:</strong> For handling a tiered pricing model to advanced app features</li>
        <li><strong class="text-md mt-1 font-bold mb-1">Improve Test Coverage:</strong>
        <ul class="white-bullets pl-6 space-y-2">
        <li>Implement <strong>Vitest</strong> for unit tests</li>
        <li>Implement <strong>React Testing Library</strong> for integration tests</li>
        <li>Implement <strong>Playwright/Cypress</strong> for end-to-end tests</li>
        <li>Integrate automated tests into CI/CD pipeline</li>
        </ul>
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
</div>
