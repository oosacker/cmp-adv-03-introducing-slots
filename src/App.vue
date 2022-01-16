<template>
  <div>
    <the-header></the-header>
    <!-- <TheHeader /> -->
    <badge-list></badge-list>

    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>

    <!-- SCOPED Slots -->
    <!-- access the "goals" items from outside the slotted component -->
    <course-goals>
        <template  v-slot="slotProps">
          <h1>{{ slotProps.item }}</h1>

          <!-- Another prop has a dash so treat like an array -->
          <p>{{ slotProps['another'] }}</p>
          <!-- <p>{{ slotProps['another'] }}</p> -->
        </template>
    </course-goals>

    <!-- Dynamic Components -->
    <!-- Use keep-alive to save input data when switch component!!! -->
    <button @click="setSelectedComp('active-goals')">Active Goals</button>
    <button @click="setSelectedComp('manage-goals')">Manage Goals</button>
    <!-- <active-goals></active-goals>
    <manage-goals></manage-goals> -->
    <keep-alive>
      <component :is="activeComp"></component>
    </keep-alive>

  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import BadgeList from './components/BadgeList.vue';
import UserInfo from './components/UserInfo.vue';
import CourseGoals from './components/CourseGoals.vue';
import ActiveGoals from './components/ActiveGoals.vue';
import ManageGoals from './components/ManageGoals.vue';

export default {
  components: {
    TheHeader,
    BadgeList,
    UserInfo,
    CourseGoals,
    ActiveGoals,
    ManageGoals
  },
  data() {
    return {
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
      activeComp: ''
    };
  },
  methods: {
    setSelectedComp(comp) {
      this.activeComp = comp
    }
  }
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>