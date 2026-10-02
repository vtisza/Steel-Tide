STEEL TIDE - browser build

This folder is a static website. Serve it over HTTPS (or http://localhost for testing)
and open index.html in a desktop browser with WebGL 2 (current Chrome, Edge, Firefox, Safari).
Opening index.html straight from disk (file://) does not work.

Online multiplayer needs the Steel Tide relay server (server/relay.py in the source repository).
By default the game looks for it at /relay on the same server; ?relay=wss://host/relay in the
page address, or the Relay server field in the Multiplayer screen, points it elsewhere.
Single player needs no server beyond the static files.

Press H in game for help.

Third-party art, sounds and fonts are credited in THIRD_PARTY_ASSETS.md;
their licence texts are in the licenses/ folder.
