<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper" @click="$emit('close')">
        <div class="modal-container" @click.stop>
          <div class="modal-body">
            <slot name="body">
              <form @submit.prevent="submitForm">
                <input v-model.trim="user.username" placeholder="UserName" />
                <input v-model.trim="user.password" placeholder="Password" />
                <button class="btn btn-success" type="submit">Submit</button>
              </form>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import axios from "axios";
export default {
  name: "my-modal",
  data() {
    return {
      user: {
        username: "",
        password: ""
      },
      response: ""
    };
  },
  methods: {
    submitForm: function() {
      console.log(`UserName: ${this.user.username}`);
      console.log(`Password: ${this.user.password}`);

      axios
        .post("//jsonplaceholder.typicode.com/users", {
          username: this.user.username,
          password: this.user.password
        })
        .then(response => {
          console.log(JSON.stringify(response, null, 2));
        });
    }
  }
};
</script>

<style scoped>
input {
  padding: 5px;
  margin: 5px !important;
  border: 1px solid black;
}
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 300px;
  margin: 0px auto;
  /* padding: 10px; */
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
  position: relative;
  left: 50%;
  transform: translate(-50%, -50%);
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-footer {
  display: flex;
  justify-content: center;
  align-items: center;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
