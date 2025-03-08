<template>
  <v-container>
    <v-row>
      <v-col>
        <v-btn-toggle v-model="toggle" divided rounded="xl">
          <v-btn value="nerima"> 練馬駅 </v-btn>
          <v-btn value="nakano"> 中野駅 </v-btn>
        </v-btn-toggle>
      </v-col>
    </v-row>

    <v-row>
      <v-col>
        <v-btn-toggle v-model="toggle" divided rounded="xl">
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
          v-for="busLine in busLines"
          :key="busLine.title"
          :subtitle="busLine.subtitle"
          :title="busLine.title"
        >
          <template v-slot:prepend>
            <v-avatar :color="busLine.color">
              <v-icon color="white">{{ busLine.icon }}</v-icon>
            </v-avatar>
          </template>
        </v-list-item>
      </v-list>
    </v-card>
  </v-container>
</template>

<script setup lang="ts">
const busLines = [
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
