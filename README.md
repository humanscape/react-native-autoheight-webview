# react-native-autoheight-webview

An auto height webview for React Native, even auto width for inline html.

[![NPM Version](http://img.shields.io/npm/v/react-native-autoheight-webview.svg?style=flat-square)](https://www.npmjs.com/package/react-native-autoheight-webview)
[![NPM Downloads](https://img.shields.io/npm/dt/react-native-autoheight-webview.svg?style=flat-square)](https://www.npmjs.com/package/react-native-autoheight-webview)

## versioning

`npm install react-native-autoheight-webview --save` (rn >= 0.59, be capable of Hooks)

`npm install react-native-autoheight-webview@1.0.1 --save` (0.57 <= rn < 0.59)

Read [README_old](./README_old.md) for earlier version guide and please note that fixes and new features will only be included in the last version.

## showcase

![react-native-autoheight-webview iOS](https://media.giphy.com/media/tocJYDUGCgwac0kkyB/giphy.gif)&nbsp;
![react-native-autoheight-webview Android](https://media.giphy.com/media/9JyX1wZshYIxuPklHK/giphy.gif)

## usage

```javascript
import AutoHeightWebView from 'react-native-autoheight-webview'

import { Dimensions } from 'react-native'

<AutoHeightWebView
    style={{ width: Dimensions.get('window').width - 15, marginTop: 35 }}
    customScript={`document.body.style.background = 'lightyellow';`}
    customStyle={`
      * {
        font-family: 'Times New Roman';
      }
      p {
        font-size: 16px;
      }
    `}
    onSizeUpdated={({size => console.log(size.height)})},
    files={[{
        href: 'cssfileaddress',
        type: 'text/css',
        rel: 'stylesheet'
    }]}
    source={{ html: `<p style="font-weight: 400;font-style: normal;font-size: 21px;line-height: 1.58;letter-spacing: -.003em;">Tags are great for describing the essence of your story in a single word or phrase, but stories are rarely about a single thing. <span style="background-color: transparent !important;background-image: linear-gradient(to bottom, rgba(146, 249, 190, 1), rgba(146, 249, 190, 1));">If I pen a story about moving across the country to start a new job in a car with my husband, two cats, a dog, and a tarantula, I wouldn’t only tag the piece with “moving”. I’d also use the tags “pets”, “marriage”, “career change”, and “travel tips”.</span></p>` }}
    scalesPageToFit={true}
    zoomable={false}
    /*
    other react-native-webview props
    */
  />
```

## properties

| Prop                         | Default |                                                      Type                                                       | Description                                                                                                                                                                                                  |
| :--------------------------- | :-----: | :-------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| style                        |    -    |                                              `ViewPropTypes.style`                                              | The width of this component will be the width of screen by default, if there are some text selection issues on iOS, the width should be reduced more than 15 and the marginTop should be added more than 35. |
| customScript                 |    -    |                                               `PropTypes.string`                                                | -                                                                                                                                                                                                            |
| customStyle                  |    -    |                                               `PropTypes.string`                                                | The custom css content will be added to the page's `<head>`.                                                                                                                                                 |
| onSizeUpdated                |    -    |                                                `PropTypes.func`                                                 | Either updated height or width will trigger onSizeUpdated.                                                                                                                                                   |
| files                        |    -    | `PropTypes.arrayOf(PropTypes.shape({ href: PropTypes.string, type: PropTypes.string, rel: PropTypes.string }))` | Using local or remote files. To add local files: Add files to android/app/src/main/assets/ (depends on baseUrl) on android; add files to web/ (depends on baseUrl) on iOS.                                   |
| source                       |    -    |                                               `PropTypes.object`                                                | BaseUrl now contained by source. 'web/' by default on iOS; 'file:///android_asset/' by default on Android or uri.                                                                                            |
| scalesPageToFit              |  false  |                                                `PropTypes.bool`                                                 | False by default (different from react-native-webview which true by default on Android). When scalesPageToFit was enabled, it will apply the scale of the page directly instead of using viewport meta script.    |
| scrollableWhenZoomin                     |  false   |                                                `PropTypes.bool`                                                 | Making the webview scrollable on iOS when zoomed in even if scrollEnabled is false.                                                                        |
| zoomable                     |  true   |                                                `PropTypes.bool`                                                 | Only works on iOS when disable scalesPageToFit, in other conditions, using custom scripts to create viewport meta to disable zooming.                                                                        |
| showsVerticalScrollIndicator |  false  |                                                `PropTypes.bool`                                                 | False by default (different from react-native-webview).                                                                                                                                                      |
| showsVerticalScrollIndicator |  false  |                                                `PropTypes.bool`                                                 | False by default (different from react-native-webview).                                                                                                                                                      |
| originWhitelist              |  ['*']  |                                      `PropTypes.arrayOf(PropTypes.string)`                                      | -                                                                                                                                                                                                            |

## demo

```
npx react-native run-ios/anroid
```

You may have to use yarn to install the dependencies of the demo and remove "demo/node_modules/react-native-autoheight-webview/demo" manually, cause of installing a local package with npm will create symlink, but there is no supporting of React Native to symlink (https://github.com/facebook/watchman/issues/105) and "yarn install" ignores "files" from local dependencies (https://github.com/yarnpkg/yarn/issues/2822).
For android, you may have to copy the "Users\UserName\.android\debug.keystore" to "demo/android/app/".

## supporting rnaw

One-time donation via PayPal:

[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/iou90)