# React Native Map Link

An easy way to open a location in a map app of the user's choice, based on the apps they have installed
on their device.

Currently supported apps:

* Apple Maps – `apple-maps`
* Google Maps – `google-maps`
* Citymapper – `citymapper`
* Uber – `uber`
* Lyft – `lyft`
* Navigon – `navigon`
* The Transit App – `transit`
* Waze – `waze`
* Yandex.Navi – `yandex`
* Moovit - `moovit`


## Installation

```
npm i -S react-native-map-link         # or yarn add react-native-map-link
```

### A note about iOS 9+
As of iOS 9, your app needs to provide the `LSApplicationQueriesSchemes` key inside
Info.plist to specify the URL schemes with which the app can interact.

Just put this in your Info.plist depending on which apps you'd like to support.
Omitting these might mean that the library can't detect some of the maps apps installed by the user.

```
<key>LSApplicationQueriesSchemes</key>
    <array>
        <string>comgooglemaps</string>
        <string>citymapper</string>
        <string>uber</string>
        <string>lyft</string>
        <string>navigon</string>
        <string>transit</string>
        <string>waze</string>
        <string>yandexnavi</string>
        <string>moovit</string>
    </array>
```

## Usage

```
import { showLocation } from 'react-native-map-link'

showLocation({
    latitude: 38.8976763,
    longitude: -77.0387185,
    sourceLatitude: -8.0870631,  // optional
    sourceLongitude: -34.8941619,  // not optional if sourceLatitude is specified
    title: 'The White House',  // optional
    googleForceLatLon: false,  // optionally force GoogleMaps to use the latlon for the query instead of the title
    googlePlaceId: 'ChIJGVtI4by3t4kRr51d_Qm_x58',  // optionally specify the google-place-id
    dialogTitle: 'This is the dialog Title', // optional (default: 'Open in Maps')
    dialogMessage: 'This is the amazing dialog Message', // optional (default: 'What app would you like to use?')
    cancelText: 'This is the cancel button text', // optional (default: 'Cancel')
    // app: 'uber'  // optionally specify specific app to use
})
```


## Component usage (alternative usage)

If you want to have a stylized popup with images you can use the Popup component.
<a href="https://imgflip.com/gif/2avtml"><img src="https://i.imgflip.com/2avtml.gif" title="made at imgflip.com"/></a>

```
import { Popup } from 'react-native-map-link';

<Popup
    isVisible={this.state.isVisible}
    onCancelPressed={() => this.setState({ isVisible: false })}
    onAppPressed={() => this.setState({ isVisible: false })}
    onBackButtonPressed={() => this.setState({ isVisible: false })}
    modalProps={{ // you can put all <a href="https://github.com/react-native-community/react-native-modal">react-native-modal</a> props inside.
        animationIn: 'slideInUp',
    }}
    options={{ // You can pass exactly the same options as the showLocation method above
        latitude,
        longitude,
        dialogTitle: 'Lancer l\'itinéraire', // optionnal (default: 'Open with...')
        dialogMessage: 'Choisis grâce à quelle application tu souhaites te rendre à ton ziiin !', // optional (default: '')
        cancelText: 'Annuler', // optional (default: 'Cancel')
    }}
    style={ // optional . You can override default style by passing your values.
      container: {},
      itemContainer: {},
      image: {},
      itemText: {},
      headerContainer: {},
      titleText: {},
      subtitleText: {},
      cancelButtonContainer: {},
      cancelButtonText: {},
      separatorStyle: {},
      activityIndicatorContainer: {}
    }
/>
```
* Every part of the component is editable

* The `sourceLatitude/sourceLongitude` options only work if you specify both. Currently supporting all apps, except `Waze and Navigon`, if you want to specify the source lat/long instead of let the app choose your current location.


## Credits

This library is loosely based on [CMMapLauncher](https://github.com/citymapper/CMMapLauncher), ported to React Native for your pleasure and convenience.


## Authors

This library is developed by [Includable](https://includable.com/), a creative app and web platform
development agency based in Amsterdam, The Netherlands.

* Thomas Schoffelen, [@tschoffelen](https://twitter.com/tschoffelen)

## Contributors

* Johan le Roch, [@JohnLrDev](https://twitter.com/JohnLrDev)