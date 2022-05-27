 
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
  <div class="margin-left40">
    <SgtRack :nodeList="nodeList" :powerList="powerList" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import SgtRack from "@/lib/components/SgtServerStructure/SgtRack.vue";
@Component({
  name: "LrDemoPage",
  components: { SgtRack },
})
export default class LrDemoPage extends Vue {
  nodeList = [
    {
      name: "node1",
      nodeStatus: "ACTIVE",
      position: 0,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node2",
      nodeStatus: "ACTIVE",
      position: 11,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node3",
      nodeStatus: "ACTIVE",
      position: 5,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node4",
      nodeStatus: "INACTIVE",
      position: 4,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node5",
      nodeStatus: "ACTIVE",
      position: 10,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node6",
      nodeStatus: "STOPPED",
      position: 3,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node7",
      nodeStatus: "ACTIVE",
      position: 8,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
        ],
        expander: "abcde",
      },
    },
    {
      name: "node8",
      nodeStatus: "INACTIVE",
      position: 14,
      powerStatus: "OK",
      server: { status: "Active", temp: "42" },
      storage: {
        status: "Active",
        temp: "42",
        size: "10P",
        controllers: [
          { id: 1, name: "controller1" },
          { id: 2, name: "controller2" },
        ],
        fans: [
          { name: "fan1", status: "ON" },
          { name: "fan2", status: "OFF" },
        ],
        ports: [
          { name: "port1", type: "HBA" },
          { name: "usb1", type: "USB" },
          { name: "usb2", type: "USB" },
        ],
        disk: "",
        diskGroup: [
          { name: "disk1", param1: "abc" },
          { name: "disk2", param1: "xyz" },
          { name: "disk3", param1: "efg" },
          { name: "disk4", param1: "hig" },
          { name: "disk5", param1: "klm" },
          { name: "disk6", param1: "nop" },
          { name: "disk7", param1: "abc" },
          { name: "disk8", param1: "xyz" },
          { name: "disk9", param1: "efg" },
          { name: "disk10", param1: "hig" },
          { name: "disk11", param1: "klm" },
          { name: "disk12", param1: "nop" },
        ],
        expander: "abcde",
      },
    },
  ];

  powerList = [
    { id: 10, name: "power1", powerStatus: "ON" },
    { id: 11, name: "power2", powerStatus: "OFF" },
  ];
}
</script>

<style lang="scss" scoped>
.margin-left40 {
  margin-left: 40%;
}
</style>