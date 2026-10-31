# video-call

A minimal React + Vite experiment that embeds ZEGOCLOUD's prebuilt video-call UI to run a browser group video call. Open the page, share the generated link, and anyone who opens it joins the same room.

The code follows ZEGOCLOUD's UIKit Prebuilt quick-start sample for React; it is a learning experiment, not a full application.

## How it works

- `src/App.jsx` reads `roomID` from the URL query string, or generates a random 5-character room ID.
- It creates a kit token with `ZegoUIKitPrebuilt.generateKitTokenForTest(appID, serverSecret, roomID, userID, userName)`, using a random user ID and name.
- `ZegoUIKitPrebuilt.create(kitToken).joinRoom(...)` mounts ZEGOCLOUD's prebuilt UI full-screen in **GroupCall** mode, with a "Copy link" button that shares `?roomID=<id>`.

Everything else (camera and microphone selection, pre-join screen, in-call controls) comes from the `@zegocloud/zego-uikit-prebuilt` package.

## Tech stack

| Layer | Technology |
| --- | --- |
| UI | React 18.3 |
| Build tool | Vite 5.4 |
| Video | `@zegocloud/zego-uikit-prebuilt` 2.11 |
| Linting | ESLint 9 |

## Getting started

Prerequisites: Node.js 18+, npm, and a ZEGOCLOUD project (App ID and Server Secret from the ZEGOCLOUD console).

```bash
npm install
```

Copy `.env.example` to `.env` and set `VITE_ZEGO_APP_ID` and `VITE_ZEGO_SERVER_SECRET` to your project's credentials, then:

```bash
npm run dev
```

Open the local URL that Vite prints, copy the room link from the call UI, and open it in a second tab or on another device to join the same call.

Other scripts: `npm run build`, `npm run preview`, `npm run lint`.

## Known limitations

- `generateKitTokenForTest` builds the token in the browser, so the server secret ends up in the client bundle. ZEGOCLOUD intends this only for testing; a real deployment should issue tokens from a backend.
- `src/Constant.js` is not used by the app.
- The page title and favicon are still the Vite template defaults.

## Author

**Lê Văn Trung Tính** — Software Engineer | AI Product Builder

- Website: [trungtinh.site](https://trungtinh.site)
- GitHub: [@tinhne](https://github.com/tinhne)
