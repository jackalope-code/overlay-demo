# Realtime Networked Image Overlay
Uses React to build a webpage and the npm express package for the API, among other npm dependencies.
## Installation for development
### Requirements
- Requires Node.js https://nodejs.org/en
- Requires git https://git-scm.com/
- Visual Studio Code or a similar IDE with linting and integrated command line terminals recommended.
- I'm going to Dockerize this at some point but Docker is not required for this to work.
- Something like [Postman](https://www.postman.com/downloads/) can be used to inspect HTTP and WebSocket requests/responses from a GUI.

Clone the repo from the command line:  
```git clone https://github.com/jackalope-code/stream-overlay```  


### Starting the API server for the first time
From the command line:  
1. `cd` into the cloned repo directory (stream-overlay)
2. Go into the server directory  
`cd server`
3. Install dependencies  
`npm install`
4. Start the node server with live reloading on code changes (defaults to http://localhost:4000)  
`npm run dev`

### Starting the webpage for the first time
From the command line:
1. `cd` into the cloned repo directory (stream-overlay)
2. Install dependencies  
`npm install`
3. Start the create-react-app development server with live reloading at http://localhost:3000  
`npm start`

Running `npm run dev` from the server directory and `npm start` from the root stream-overlay directory is enough to start the API server and the webpage respectively, once npm dependencies are installed.

Once the app is deployed, the API will run on a remote server and the webpage interfaces with the API. Users can then access the app from the browser with no dependency requirements.

When the basic functionality is working I'll host a version of the API for awhile. I don't currently have a good way to host the webpage for multiple users. I may be able to get away with hosting the page on GitHub, but I would not be able to create dynamic sessions that way (GitHub only supports static sites).

## Local testing
- Start the development servers for the API and the webpage
- Open two browser windows to the url http://localhost:3000
- Updates to one window should be mirrored to the other window

## Local development
**In the src folder:**  
The entrypoint for the React App webpage is App.tsx. Right now it just contains Overlay.tsx

Overlay.tsx and Widget.tsx are the two primary components for the overlay. Overlay.tsx manages networking and widget data. Widget.tsx sets up event handlers and manages what is displayed for each moveable widget.

## Remaining work
- Image linking. It's easier to require people host their own images and link, but this is insecure if they can change the resource and have the same url.
- Some form of authorization or authentication
- Newly connected clients should fetch data from the server to update properly
- Editing component data from PUT or adding a new component from POST should update locally and broadcast updates to other clients
- Add a GUI for adding and editing onscreen components
  - Editor GUI should have an on screen rendering area and an off-screen area 
- Have an editor view and a live overlay view
- Allow linking videos and ensure they play through without restarting constantly  
Requires time sync updates for live playback control
- Networked component controls:
  - Show/hide all
  - Clear all (confirm and have auth)
  - Toggle snap/drag movement
  - Snap to grid?
- Site hosting
- Session management
- Redis for persistance?
- Image uploading? More secure to manage from the app, but managing uploads and storage becomes a concern.
- I think an image/resource approval interface would be cool
- Bundle for faster deployment

## Troubleshooting
- If objects are not working or nothing is letting you drag it, make sure the server is running and connected properly. Server error statuses would be good to add in the future.

## Environment variables
TODO

## How to deploy
TODO
