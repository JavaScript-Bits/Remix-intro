 


### Introduction
A full stack web framework on top of the react router.
Useloader from router v6 borrows heavily from tanstack router. Remix is a classic evolution of route v6.
#### React
React has always been a rendering lib. 
Huge rendering bundles have ended up blocking fetches even though fetches are barebones json.
Initiating fetches is something fetch libs(Axios et al) do. Not react. 
#### URL loading libs(React Router V6 & Tanstack Router)
We can forego fetch libs (Axios) and initiate fetches at the url level
Loaders initiate the fetching and every route has its own loader function to do this.

#### Traditional Fetching in SPAs.
- Load a JS bundle to the frontend with a fetching lib like Axios and unbundle it on the browser.
- Make a fetch request with a state machine(react query, redux) that initiates loading states.

#### Cons of useEffect
- You need to pass values in the use effect array for changes tied to URLs.
- You need inbuilt error handling.
- Cleanup fn for unresolved promises or else you’ll have a memory leak.
- Instantiate refetches whenever anything changes.

#### Cons of React Query
- Solves re-fetches and useEffect issues but doesn’t solve spinners and UI blocking.
	If you have fetch calls three routes deep, you’ll get spinners in all of them.
	- Remix parallelism the unblocked fetches.
You need to still load Axios, fallbacks, error states etc.


#### Decoupling of logic
What remix does is to seperate all these: 
- Initiate fetches at the route level
- Read the data
- Render the data (or the fallbacks)
    - If you render then fetch, heavy assets block your UI. 
Fetching before rendering ensures you unblock your UI.

### UP NEXT: 
- RSC: Moves rendering and data fetching on the server.
- How Remix Fetches in parallel for nested routes.
- Remix and Mutations for nested logic.
