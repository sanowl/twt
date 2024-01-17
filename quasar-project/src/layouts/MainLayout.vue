<template>
  <q-layout view="lHr lpR fFf">

    <q-header bordered class="bg-white text-black">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-weight-bold">
          Trendr
        </q-toolbar-title>

      </q-toolbar>
    </q-header>
    <q-drawer v-model="leftDrawerOpen" side="left" bordered show-if-above>
      <div class="drawer-icon-container">
        <i class="fa fa-eye fa-3x"></i>
      </div>
      <q-list>
        <q-item to="/" clickable v-ripple @click="setActiveTab('home')">
          <q-item-section avatar>
            <q-icon :color="activeTab === 'home' ? 'primary' : 'black'" name="home" size="md" />
          </q-item-section>
          <q-item-section class="text-h6 text-weight-bold">Home</q-item-section>
        </q-item>

        <q-item to="/about" clickable v-ripple @click="setActiveTab('about')">
          <q-item-section class="icon-section" avatar>
            <q-icon :color="activeTab === 'about' ? 'primary' : 'black'" name="book" size="md" />
          </q-item-section>
          <q-item-section class="text-h6 text-weight-bold">About</q-item-section>
        </q-item>

        <q-item to="/profile" clickable v-ripple @click="setActiveTab('profile')">
          <q-item-section class="icon-section" avatar>
            <q-icon :color="activeTab === 'profile' ? 'primary' : 'black'" name="person" size="md" />
          </q-item-section>
          <q-item-section class="text-h6 text-weight-bold">Profile</q-item-section>
        </q-item>
        <q-item to="/notification" clickable v-ripple @click="setActiveTab('notification')">
          <q-item-section class="icon-section" avatar>
            <q-icon :color="activeTab === 'Notification Active' ? 'primary' : 'black'" name="person" size="md" />
          </q-item-section>
          <q-item-section class="text-h6 text-weight-bold">notification</q-item-section>
        </q-item>

      </q-list>
    </q-drawer>
    <p class="deep-purple-9">....</p>

    <q-drawer v-model="rightDrawerOpen" side="right" bordered show-if-above>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)
    const activeTab = ref('home')

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value
    }

    const setActiveTab = (tab) => {
      activeTab.value = tab
    }

    return {
      leftDrawerOpen,
      rightDrawerOpen,
      activeTab,
      toggleLeftDrawer,
      toggleRightDrawer,
      setActiveTab
    }
  }
}
</script>

<style>
.drawer-icon-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  /* Adjust the height as needed */
}
</style>
