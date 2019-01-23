<template>
  <root>
    <nb-container>
      <nb-header />
      <nb-grid>
        <flat-list
          :data="listViewData"
          :render-item="(item) => renderList(item)"
          :on-refresh="fetchMore"
          :refreshing="refreshing"
          :tint-color="'#cccccc'"
          :key-extractor="(item) => item.toString()"
          :style="{ height: 350, backgroundColor: 'skyblue' }"
        />
      </nb-grid>
  </nb-container>
  </root>
</template>
<script>
import React from "react"
import axios from "axios"
import { AsyncStorage, ScrollView, RefreshControl, ListView, FlatList  } from "react-native"
import { Container, Header, Content, List, ListItem, Text, Button, Icon, View, Root } from 'native-base'
import { TabView, TabBar, SceneMap } from 'react-native-tab-view'



export default {
  components: { Root},
  data: function() {
    return {
      ds: new ListView.DataSource({ rowHasChanged: (r1, r2) => r1 !== r2 }),
      basic: true,
      listViewData: [
      ],
      chatContent: '',
      isEdit: false,
      editRow: null,
      refreshing: false
    };
  },
  created() {
  },
  methods: {
    fetchMore: function() {
      this.refreshing = true
      axios
        .get('https://thesimpsonsquoteapi.glitch.me/quotes')
        .then(res => {
          this.listViewData.unshift(res.data[0].quote)
          this.refreshing = false
        })
    },
    renderList: function(item) {
      return (<Text>{item.item}</Text>)
    }
  }
};
</script>
