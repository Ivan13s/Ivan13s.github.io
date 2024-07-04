<template>
  <div>
    <h2>Notifications</h2>
    <ul>
      <li v-for="notification in notifications" :key="notification.id">
        {{ notification.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import { ref, onMounted } from 'vue';

export default {
  name: 'TenantNotifications',
  setup() {
    const notifications = ref([]);

    onMounted(() => {
      axios.get('https://6686e1d583c983911b03f5b7.mockapi.io/notifications')
        .then(response => {
          notifications.value = response.data.slice(0, 10);
        })
        .catch(error => {
          console.error("There was an error fetching the notifications!", error);
        });
    });

    return {
      notifications
    };
  }
};
</script>

<style scoped>
h2 {
  margin-bottom: 20px;
}
</style>