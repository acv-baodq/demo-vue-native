<template>
  <root>
    <nb-container>
      <nb-header />
      <nb-grid>
        <nb-row :size='3'>
          <flat-list
            :data="listViewData"
            :render-item="(item) => renderList(item)"
            :on-refresh="fetchMore"
            :refreshing="refreshing"
            :tint-color="'#cccccc'"
            :key-extractor="(item) => item.toString()"
          />
        </nb-row>
        <nb-row :size='1'>
          <nb-content>
            <nb-form>
              <nb-item>
                <nb-input v-model="chatContent" placeholder="Type Something..." />
                <nb-icon :onPress="sendMessage" active name="send" />
              </nb-item>
            </nb-form>
        </nb-row>
      </nb-grid>

  </nb-container>
  </root>
</template>
<script>
import React from "react"
import { AsyncStorage, ScrollView, RefreshControl, ListView, FlatList  } from "react-native"
import { Container, Header, Content, List, ListItem, Text, Button, Icon, View, Root } from 'native-base'
import { Col, Row, Grid } from 'react-native-easy-grid';


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
    AsyncStorage.getItem('listViewData').then((val) => {
      if(val.length > 0) {
        this.listViewData = JSON.parse(val)
      } else {
        this.listViewData = []
      }
    })
  },
  methods: {
      fetchMore: function() {
        console.log('huhuh')
        this.refreshing = true
        alert('hihi')
        this.refreshing = false
      },
      editMessage: function(data, secId,rowId, rowMap) {
        this.isEdit = true
        this.chatContent = data
        this.editRow = rowId
      },
      sendMessage: function() {
        if(this.isEdit) {
          this.listViewData[this.editRow] = this.chatContent
          this.isEdit = false
        } else {
          this.listViewData.push(this.chatContent)
        }
        AsyncStorage.setItem('listViewData', JSON.stringify(this.listViewData))
        this.chatContent = ''
      },
      deleteRow: function(secId, rowId, rowMap) {
        rowMap[`${secId}${rowId}`].props.closeRow();
        const newData = [...this.listViewData];
        newData.splice(rowId, 1);
        this.listViewData = newData;
        AsyncStorage.setItem('listViewData', JSON.stringify(this.listViewData))
      },
      getLeftHiddenRowComponet: function(data, secId, rowId, rowMap) {
        return (
          <Button full onPress={() => this.editMessage(data, secId, rowId, rowMap)}>
            <Icon active name="information-circle" />
          </Button>
        );
      },
      getRighttHiddenRowComponet: function(data, secId, rowId, rowMap) {
        return (
          <Button full danger onPress={_ => this.deleteRow(secId, rowId, rowMap)}>
            <Icon active name="trash" />
          </Button>
        );
      },
      getListArr: function() {
        return this.ds.cloneWithRows(this.listViewData);
      },
      getListItemRow: function(data) {
        return (
          <ListItem>
            <Text>{data}</Text>
          </ListItem>
        );
      },
      renderList: function(item) {
        return (<Text>{item.item}</Text>)
      }
    }
};
</script>
