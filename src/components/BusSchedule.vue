<template>
  <v-container>
    <v-row>
      <v-col>
        <v-btn-toggle v-model="departure" divided rounded="xl">
          <v-btn value="nerima"> 練馬駅 </v-btn>
          <v-btn value="nakano"> 中野駅 </v-btn>
        </v-btn-toggle>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn-toggle v-model="dayType" divided rounded="xl">
          <v-btn value="weekday"> 平日 </v-btn>
          <v-btn value="saturday"> 土曜 </v-btn>
          <v-btn value="sunday"> 日曜・祝日 </v-btn>
        </v-btn-toggle>
      </v-col>
    </v-row>

    <v-divider class="my-4" />

    <v-card class="mx-auto" max-width="300">
      <v-list>
        <v-list-item
          v-for="busSchedule in busSchedules"
          :key="busSchedule.title"
          :subtitle="busSchedule.subtitle"
          :title="busSchedule.title"
        >
          <template v-slot:prepend>
            <v-avatar :color="busSchedule.color">
              <v-icon color="white">{{ busSchedule.icon }}</v-icon>
            </v-avatar>
          </template>
        </v-list-item>
      </v-list>
    </v-card>
  </v-container>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
import { scheduleData } from "@/assets/BusSchedules";

// 出発地点と曜日タイプの状態管理
const departure = ref("nerima"); // 初期値: 練馬駅
const dayType = ref("weekday"); // 初期値: 平日

// 状態変更を監視
watch([departure, dayType], ([newDeparture, newDayType]) => {
  console.log("出発地点:", newDeparture);
  console.log("曜日タイプ:", newDayType);
  // ここでバススケジュールを更新する処理を追加予定
  updateBusSchedules();
});

// バススケジュールを更新する関数
function updateBusSchedules() {
  // 将来的に実装予定: 出発地点と曜日タイプに基づいてスケジュールを更新
  // 現在はダミーデータを使用
}

const busSchedules = [
  {
    color: "blue",
    icon: "mdi-bus",
    subtitle: "07:12",
    title: "中92",
  },
  {
    color: "amber",
    icon: "mdi-bus",
    subtitle: "07:12",
    title: "中3",
  },
];
</script>
