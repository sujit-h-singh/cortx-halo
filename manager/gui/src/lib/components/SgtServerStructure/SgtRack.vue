 <!--
* CORTX-CSM: CORTX Management web.
* Copyright (c) 2020 Seagate Technology LLC and/or its Affiliates
* This program is free software: you can redistribute it and/or modify
* it under the terms of the GNU Affero General Public License as published
* by the Free Software Foundation, either version 3 of the License, or
* (at your option) any later version.
* This program is distributed in the hope that it will be useful,
* but WITHOUT ANY WARRANTY; without even the implied warranty of
* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
* GNU Affero General Public License for more details.
* You should have received a copy of the GNU Affero General Public License
* along with this program. If not, see <https://www.gnu.org/licenses/>.
* For any questions about this software or licensing,
* please email opensource@seagate.com.
-->
<template>
  <div class="server-container">
    <div class="content-container">
      <div class="node-container" v-for="node in getNodes" :key="node.name">
        <div v-if="node.isEmpty">
          <v-tooltip right>
            <template v-slot:activator="{ on, attrs }">
              <img
                v-bind="attrs"
                v-on="on"
                :src="require(`@/assets/images/hard-drive.png`)"
                alt=""
                width="100%"
                height="40px"
              />
            </template>
            <span>
              <div>Empty</div>
            </span>
          </v-tooltip>
        </div>
        <div v-else>
          <v-tooltip left>
            <template v-slot:activator="{ on, attrs }">
              <img
                v-bind="attrs"
                v-on="on"
                :src="require(`@/assets/images/server.png`)"
                alt=""
                width="40%"
                height="40px"
                @click="openServer(node.server)"
              />
            </template>
            <span>
              <div>
                Server: {{ node.position }}
                <div>name: {{ node.name }}</div>
                <div>Status: {{ node.nodeStatus }}</div>
                <div>Temp: {{ node.server.temp }}</div>
              </div>
            </span>
          </v-tooltip>
          <v-tooltip right>
            <template v-slot:activator="{ on, attrs }">
              <img
                v-bind="attrs"
                v-on="on"
                :src="require(`@/assets/images/storage.png`)"
                alt=""
                width="60%"
                height="40px"
                @click="openStorage(node.storage)"
              />
            </template>
            <span>
              <div>
                Storage: {{ node.position }}
                <div>name: {{ node.name }}</div>
                <div>Status: {{ node.nodeStatus }}</div>
                <div>Size: {{ node.storage.size }}</div>
              </div>
            </span>
          </v-tooltip>
        </div>
      </div>
      <div class="port-container" v-for="power in powerList" :key="power.name">
        <v-tooltip right max-width="300">
          <template v-slot:activator="{ on, attrs }">
            <img
              v-bind="attrs"
              v-on="on"
              :src="require('@/assets/images/port.png')"
              alt=""
              width="100%"
              height="50px"
            />
          </template>
          <span>Power {{ power.powerStatus }}</span>
        </v-tooltip>
      </div>
    </div>
    <SgtStorage
      v-if="showStorage"
      :showDialog.sync="showStorage"
      :selectedStorage="selectedComponent"
      @close="showStorage = false"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import SgtStorage from "./SgtStorage.vue";
@Component({
  name: "SgtRack",
  components: { SgtStorage },
})
export default class SgtRack extends Vue {
  @Prop({ required: true }) private nodeList: any[];
  @Prop({ required: true }) private powerList: any[];
  showStorage = false;
  selectedComponent = {};
  list = [
    { id: 0, position: 0, isEmpty: true },
    { id: 1, position: 1, isEmpty: true },
    { id: 2, position: 2, isEmpty: true },
    { id: 3, position: 3, isEmpty: true },
    { id: 4, position: 4, isEmpty: true },
    { id: 5, position: 5, isEmpty: true },
    { id: 6, position: 6, isEmpty: true },
    { id: 7, position: 7, isEmpty: true },
    { id: 8, position: 8, isEmpty: true },
    { id: 9, position: 9, isEmpty: true },
    { id: 10, position: 10, isEmpty: true },
    { id: 11, position: 11, isEmpty: true },
    { id: 12, position: 12, isEmpty: true },
    { id: 13, position: 13, isEmpty: true },
    { id: 14, position: 14, isEmpty: true },
    { id: 15, position: 15, isEmpty: true },
  ];
  get getNodes() {
    this.nodeList.sort((a, b) => a.position - b.position);
    this.nodeList.forEach((ele, i) => {
      this.list.splice(ele.position, 1, { id: i, isEmpty: false, ...ele });
    });
    console.log(this.list);
    return this.list;
  }

  openServer(server: any) {
    //
  }

  openStorage(storage: any) {
    this.selectedComponent = storage;
    this.showStorage = true;
  }
}
</script>

<style lang="scss" scoped>
.server-container {
  width: 200px;
  height: 730px;
  margin-left: 10px;
  background-color: black;
  padding: 20px;
  .content-container {
    background-color: white;
    height: 690px;
  }
}
.node-container {
  height: 40px;
}
.port-container {
  height: 50px;
  display: inline-block;
  width: 50%;
}
img:hover {
  // transform: scale(1.1);
  border: 1px solid #ffffff;
  box-shadow: -1px 1px #ffffff;
  cursor: pointer;
}
</style>