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
            <nb-text>
              Test test test
            </nb-text>
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

export default {
  components: {},
}
</script>
