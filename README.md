# react-native-default-source

## Github [https://github.com/rlterry00/react-native-default-source](https://github.com/rlterry00/react-native-default-source)

# About

This a small library that extends the default `<Image />` component of react native to have a default source image that works on both Android and iOS in debug mode. By default Android ignores the defaultSource prop in debug mode so if your image url fails no image will show on Android during development.

# Installation

`npm i react-native-default-source`

# Using The Library

Instead of using the standard `<Image />` component you will use `<DefaultSourceImage />` which extends the standard image component. All original `<Image />` props are available in `<DefualtSourceImg />`
