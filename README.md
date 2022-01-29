# react-native-default-source

## Github [https://github.com/rlterry00/react-native-default-source](https://github.com/rlterry00/react-native-default-source)

# About

This a small library that extends the default `<Image />` component of react native to have a default source image that works on both Android and iOS in debug mode. By default Android ignores the defaultSource prop in debug mode so if your image url fails no image will show on Android during development. This a good tool to use if you are not using a UI library that could have a built in solution in ther `<Image />` components. The only dependencies in this library are react and react-native. 

# License
### MIT License
A short and simple permissive license with conditions only requiring preservation of copyright and license notices. Licensed works, modifications, and larger works may be distributed under different terms and without source code.

# Installation

`npm i react-native-default-source`

# Using The Library

Instead of using the standard `<Image />` component you will use `<DefaultSourceImage />` which extends the standard image component. All original `<Image />` props are inherited in `<DefualtSourceImg />`

| Prop                 | Description                                                       | Type   | Default                           |
|----------------------|-------------------------------------------------------------------|--------|-----------------------------------|
| sourceImg            | Source image for image component.                                 | object | Required                          |
| defaultSourceImg     | Default image if image does not load.                             | object | Required                          |
| imageContainerStyle  | Styles for the container view wrapped around the image component. | object | Optional                          |
| imageStyle           | Styles for the image.                                             | object | Required for URL or remote images |
| <Image {...props} /> | Inherited props from React Native's Image component               | props  | Optional                          |

### Example

```js
import React, {useState, useEffect} from 'react';
import {StyleSheet, View} from 'react-native';
import DefaultSourceImage from 'react-native-default-source';

const Component = props => {
  const [userImage, setUserImage] = useState([]);
  useEffect(() => {
    //Fetching user image
    const getUserImage = async () => {
      return fetch('https://randomuser.me/api/')
        .then(response => response.json())
        .then(json => {
          const data = json.picture.large;
          setUserImage(data);
        })
        .catch(error => {
          console.error(error);
        });
    };
    getUserImage();
  }, []);
  

  return (
    <View style={styles.container}>
        <DefaultSourceImage
          imageStyle={styles.image}
          defaultSourceImg={require('../assets/avatar.png')}
          sourceImg={{uri: userImage}}
          resizeMode="cover"
        />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  image: {
    width: 100,
    height: 100,
    marginLeft: 5,
  },
});```





