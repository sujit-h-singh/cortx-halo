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
  <v-dialog
    :value="showStorage"
    max-width="500px"
    hide-overlay
    content-class="box-shadow0"
    @click:outside="$emit('close')"
  >
    <v-card class="background-transparent">
      <v-card-title>
        <div class="title-container"></div>
      </v-card-title>
      <v-card-text>
        <div class="server-container">
          <div class="content-container">
            <div
              class="port-container"
              :style="{ width: ele.width }"
              v-for="ele in elements"
              :key="ele.name"
            >
              <v-tooltip right max-width="300">
                <template v-slot:activator="{ on, attrs }">
                  <img
                    v-bind="attrs"
                    v-on="on"
                    :src="require(`@/assets/images/${ele.img}`)"
                    alt=""
                    width="100%"
                    height="50px"
                  />
                </template>
                <span>
                  <template v-if="ele.eleType == 'controller'">
                    <div>
                      controller Name: {{ ele.name }}<br />
                      id : {{ ele.id }}
                    </div></template
                  >
                  <div v-else>
                    {{ ele }}
                  </div>
                </span>
              </v-tooltip>
            </div>
          </div>
        </div>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>
<script lang="ts">
import { Component, Vue, Prop, PropSync } from "vue-property-decorator";
import SgtSvgIcon from "@/lib/components/SgtSvgIcon/SgtSvgIcon.vue";

@Component({
  name: "SgtStorage",
  components: { SgtSvgIcon },
})
export default class SgtStorage extends Vue {
  @PropSync("showDialog", { required: true, default: false })
  private showStorage: boolean;
  @Prop({ required: true }) selectedStorage: any;

  elements:any[] = [];
  index = 0;
  mounted() {
    console.log(this.selectedStorage);
    this.selectedStorage.controllers?.forEach((element) => {
      this.elements.push({
        position: this.index,
        ...element,
        img: "controller.png",
        width: "30%",
        eleType: "controller",
      });
      ++this.index;
    });
    this.selectedStorage.fans?.forEach((element) => {
      this.elements.push({
        position: this.index,
        ...element,
        img: "fan.png",
        width: "20%",
        eleType: "fan",
      });
      ++this.index;
    });
    this.selectedStorage.diskGroup?.forEach((element) => {
      this.elements.push({
        position: this.index,
        ...element,
        img: "disc.png",
        width: "25%",
      });
      ++this.index;
    });
    this.selectedStorage.ports?.forEach((element) => {
      this.elements.push({
        position: this.index,
        ...element,
        img: "port.png",
        width: "20%",
      });
      ++this.index;
    });
    this.elements.push({
      position: this.index,
      img: "hard-drive.png",
      expander: this.selectedStorage.expander,
      width: "50%",
    });
  }
}
</script>
<style lang="scss" scoped>
.server-container {
  width: 400px;
  height: 400px;
  margin-left: 10px;
  background-color: black;
  padding: 20px;
  .content-container {
    background-color: white;
    height: 360px;
  }
}
.background-transparent {
  background: rgba(0, 0, 0, 0) !important;
  box-shadow: 0 0 0;
}
.box-shadow0 {
  box-shadow: 0 0 0 !important;
}
.port-container {
  height: 50px;
  display: inline-block;
  //   width: 30%;
}
</style>
