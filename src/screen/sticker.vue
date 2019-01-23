<template>
  <nb-container>
    <nb-header />
    <nb-content>
      <nb-card>
        <nb-card-item header>
          <nb-text>NativeBase</nb-text>
        </nb-card-item>
        <nb-card-item>
          <nb-body>
              <image
                :style="{width: 150, height: 150}"
                :source="{uri: 'https://media.giphy.com/media/5z5NIlNjK0NxpsecKh/giphy.gif'}"
              />
          </nb-body>            
        </nb-card-item>
        <nb-card-item footer>
          <nb-text>GeekyAnts</nb-text>
        </nb-card-item>
      </nb-card>
    </nb-content>
  </nb-container>
</template>

<script>
import React, { Component } from 'react';
import { Container, Header, Content, Card, CardItem, Text, Body } from 'native-base';
import { Image } from 'react-native';
import CatSticker from '../../assets/giphy.gif'
import Iconne from '../../assets/icon.png'


export default {
  components: {},
}
</script>
