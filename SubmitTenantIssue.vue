<template>
  <div>
    <h2>Submit an Issue</h2>
    <form @submit.prevent="submitIssue">
      <div>
        <label for="title">Title:</label>
        <input type="text" id="title" v-model="title" required>
      </div>
      <div>
        <label for="description">Description:</label>
        <textarea id="description" v-model="description" required></textarea>
      </div>
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
import { ref } from 'vue';

export default {
  name: 'SubmitTenantIssue',
  setup() {
    const title = ref('');
    const description = ref('');

    const submitIssue = () => {
      const issue = {
        title: title.value,
        body: description.value,
        userId: 1
      };
      axios.post('https://6686e1d583c983911b03f5b7.mockapi.io/issues', issue)
        .then(response => {
          console.log('Issue submitted:', response.data);
          title.value = '';
          description.value = '';
        })
        .catch(error => {
          console.error("There was an error submitting the issue!", error);
        });
    };

    return {
      title,
      description,
      submitIssue
    };
  }
};
</script>

<style scoped>
h2 {
  margin-bottom: 20px;
}
form {
  display: flex;
  flex-direction: column;
}
div {
  margin-bottom: 10px;
}
label {
  margin-bottom: 5px;
}
textarea {
  resize: none;
}
button {
  align-self: flex-start;
}
</style>