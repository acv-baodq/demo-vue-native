<template>
  <nb-container>
    <flat-list
      :data="listViewData"
      :render-item="(item) => renderList(item)"
      :key-extractor="(item) => item.toString()"
      :on-scroll="handleCroll"
    />
  </nb-container>
</template>

<script>
import React, { Component } from 'react';
import { Container, Header, Content, Card, CardItem, Text, Body, View } from 'native-base';
import { Col, Row, Grid } from 'react-native-easy-grid';
import {ScrollView, FlatList} from 'react-native';
import { AsyncStorage } from "react-native"


export default {
  components: {},
  data() {
     return {
       positionY: 0,
      listViewData: [
        '1. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '1. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '1. Maecenas scelerisque urna in luctus aliquam.',
        '1. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '1. Sed suscipit nulla vitae erat consectetur iaculis.',
        '1. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '1. Donec eu quam eu tortor accumsan congue.',
        '1. Proin quis libero quis orci sagittis fringilla.',
        '1. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '2. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '2. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '2. Maecenas scelerisque urna in luctus aliquam.',
        '2. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '2. Sed suscipit nulla vitae erat consectetur iaculis.',
        '2. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '2. Donec eu quam eu tortor accumsan congue.',
        '2. Proin quis libero quis orci sagittis fringilla.',
        '2. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '3. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '3. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '3. Maecenas scelerisque urna in luctus aliquam.',
        '3. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '3. Sed suscipit nulla vitae erat consectetur iaculis.',
        '3. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '3. Donec eu quam eu tortor accumsan congue.',
        '3. Proin quis libero quis orci sagittis fringilla.',
        '3. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '4. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '4. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '4. Maecenas scelerisque urna in luctus aliquam.',
        '4. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '4. Sed suscipit nulla vitae erat consectetur iaculis.',
        '4. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '4. Donec eu quam eu tortor accumsan congue.',
        '4. Proin quis libero quis orci sagittis fringilla.',
        '4. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '5. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '5. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '5. Maecenas scelerisque urna in luctus aliquam.',
        '5. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '5. Sed suscipit nulla vitae erat consectetur iaculis.',
        '5. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '5. Donec eu quam eu tortor accumsan congue.',
        '5. Proin quis libero quis orci sagittis fringilla.',
        '5. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '6. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '6. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '6. Maecenas scelerisque urna in luctus aliquam.',
        '6. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '6. Sed suscipit nulla vitae erat consectetur iaculis.',
        '6. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '6. Donec eu quam eu tortor accumsan congue.',
        '6. Proin quis libero quis orci sagittis fringilla.',
        '6. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '7. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '7. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '7. Maecenas scelerisque urna in luctus aliquam.',
        '7. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '7. Sed suscipit nulla vitae erat consectetur iaculis.',
        '7. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '7. Donec eu quam eu tortor accumsan congue.',
        '7. Proin quis libero quis orci sagittis fringilla.',
        '7. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '8. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '8. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '8. Maecenas scelerisque urna in luctus aliquam.',
        '8. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '8. Sed suscipit nulla vitae erat consectetur iaculis.',
        '8. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '8. Donec eu quam eu tortor accumsan congue.',
        '8. Proin quis libero quis orci sagittis fringilla.',
        '8. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '9. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '9. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '9. Maecenas scelerisque urna in luctus aliquam.',
        '9. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '9. Sed suscipit nulla vitae erat consectetur iaculis.',
        '9. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '9. Donec eu quam eu tortor accumsan congue.',
        '9. Proin quis libero quis orci sagittis fringilla.',
        '9. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.',

        '0. Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
        '0. Phasellus ut nisl pellentesque, aliquam diam nec, convallis sapien.',
        '0. Maecenas scelerisque urna in luctus aliquam.',
        '0. Mauris efficitur nisi ultrices urna iaculis placerat.',
        '0. Sed suscipit nulla vitae erat consectetur iaculis.',
        '0. Sed interdum nisi vel lectus porta, et pulvinar risus gravida.',
        '0. Donec eu quam eu tortor accumsan congue.',
        '0. Proin quis libero quis orci sagittis fringilla.',
        '0. Praesent sagittis eros eget dolor rutrum eleifend ut ac odio.'
      ]
     } 
  },
  mounted() {
    // console.log(Dimensions.get('window').height)
    // console.log(Dimensions.get('window').width)
  },
  methods: {
    renderList: function(item) {
      return (<Text>{item.item}</Text>)
    },
    handleCroll: async function(e) {
			try {
				const value = await AsyncStorage.setItem('positionY', e.nativeEvent.contentOffset.y);
				if (value !== null) {
					console.log(value);
				}
			 } catch (error) {
         console.log('error saving positon')
			 }
    }
  }
}
</script>
