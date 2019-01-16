<template>
	<!-- <nb-container>
		<nb-header>
			 <nb-left>
				<nb-button transparent>
					<nb-icon ios='ios-menu' android='md-menu'/>
				</nb-button>
			</nb-left>
			<nb-body>
				<nb-title>Books</nb-title>
			</nb-body>
			<nb-right />
		</nb-header> -->
	</nb-container>
  <tab-nav></tab-nav>
</template>

<script>
import Vue from "vue-native-core";
import { VueNativeBase, Header, Container, Left, Right, Body, Icon, Text } from "native-base";
import { View } from "react-native";
import Chat from "./chat.vue";
import Fiction from "./screen/fiction.vue";
import { TabNavigator, TabBarTop } from "vue-native-router";


const tabNav = TabNavigator(
  {
    Home: Chat,
    Fiction: Fiction,
  },
  {
    tabBarPosition: 'top',
 }
);


export default {
  components: { tabNav}
};
</script>
