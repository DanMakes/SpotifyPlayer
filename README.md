# react-spotify-web-playback

[![npm version](https://badge.fury.io/js/react-spotify-web-playback.svg)](https://www.npmjs.com/package/react-spotify-web-playback) [![build status](https://travis-ci.org/gilbarbara/react-spotify-web-playback.svg)](https://travis-ci.org/gilbarbara/react-spotify-web-playback) [![Maintainability](https://api.codeclimate.com/v1/badges/9b6d6817ca7bdfe47f5e/maintainability)](https://codeclimate.com/github/gilbarbara/react-spotify-web-playback/maintainability) [![Test Coverage](https://api.codeclimate.com/v1/badges/9b6d6817ca7bdfe47f5e/test_coverage)](https://codeclimate.com/github/gilbarbara/react-spotify-web-playback/test_coverage)

#### A Spotify player with [Spotify's Web Playback SDK](https://developer.spotify.com/documentation/web-playback-sdk/).

View the [demo](https://react-spotify-web-playback.gilbarbara.dev/)

Check the [supported browser](https://developer.spotify.com/documentation/web-playback-sdk/#supported-browsers) list. This library will try to use the user's devices to work with mobile and unsupported browsers.

## Setup

```bash
npm i react-spotify-web-playback
```

## Getting Started

```jsx
import SpotifyPlayer from 'react-spotify-web-playback';

<SpotifyPlayer
  token="BQAI_7RWPJuqdZxS-I8XzhkUi9RKr8Q8UUNaJAHwWlpIq6..."
  uris={['spotify:artist:6HQYnRM4OzToCYPpVBInuU']}
/>;
```

## Props

**autoPlay**: `boolean`  
Start the player immediately.

**callback**: `(state) => any`  
Get status updates from the player. Check `CallbackState` in the [types](src/types/common.ts) for the `state` structure.

**name** `string` _default: Spotify Web Player_  
The name of the player.

**offset** `number`  
The position of the list/tracks you want to start the player.

**persistDeviceSelection** `boolean`  
Save the device selection.

**showSaveIcon** `boolean`  
Display a Favorite button. Needs additional scopes in your token!

**syncExternalDeviceInterval** `number` _default: 5_  
The time in seconds that the player will sync with external devices

**token** `string` **REQUIRED**  
A Spotify token. More info below.

**styles** `object`  
Customize the player appearance. Check `StylesOptions` in the [types](src/types/common.ts).

**uris** `string | string[]`  
A list of Spotify [URIs](https://developer.spotify.com/documentation/web-api/#spotify-uris-and-ids).

## Spotify Token

It needs a Spotify token with the following scopes:

- streaming
- user-read-birthdate
- user-read-email
- user-read-private
- user-read-playback-state (to read other devices' status)
- user-modify-playback-state (to update other devices)

If you want to show the Favorite button (💚) you'll need the additional scopes:

- user-library-read
- user-library-modify

Please refer to Spotify's Web API [docs](https://developer.spotify.com/documentation/web-api/) for more information.

> This library doesn't handle token generation and expiration. You'll need to handle that by yourself.

## Styling

You can customize the UI with a `styles` prop. Check all the available options [here](src/types/common.ts#L44).

```tsx
<SpotifyWebPlayer
  ...
  styles={{
    bgColor: '#333',
    color: '#fff',
    loaderColor: '#fff',
    rangeColor: '#1cb954',
    savedColor: '#fff',
    trackArtistColor: '#ccc',
    trackNameColor: '#fff',
  }}
/>
```

## Issues

If you find a bug, please file an issue on [our issue tracker on GitHub](https://github.com/gilbarbara/react-spotify-web-playback/issues).

## License

MIT
