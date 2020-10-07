<template>
  <div>
    <div>Login <input type="text" v-model="login" placeholder="Login" /></div>

    <div>
      Password <input type="text" v-model="password" placeholder="Password" />
    </div>
    <div>
      <button :disabled="!isLoginAndPassword" @click="checkLoginPassword">
        Go
      </button>
    </div>
    <div
      :class="{
       'message': authorization === false,
        'message-ivan': authorization === false && login === 'Ivan',
      }"
    >
      {{ messageResult }}
    </div>
    <div v-show="authorization">
      <img
        src="https://media0.giphy.com/media/VJCUALuSUpjsGyvUrs/giphy.gif?cid=6c09b952d8ff53e597766e6d4780d0473d2a6b7a8ec1c8fb&rid=giphy.gif"
        alt=""
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginAndPassword",

  props: {
    userList: {
      type: Array,
      default: () => []
    }
  },

  data() {
    return {
      login: null,
      password: null,
      authorization: null,
    };
  },

  computed: {
    messageResult() {
      if (this.authorization) return `welcome ${this.login}`;
      else if (this.authorization === false)
        return "Incorect login or password, check your login and password";
      else return "Put your login and password, please";
    },

    isLoginAndPassword() {
      return this.login && this.password;
    },
  },

  methods: {
    checkLoginPassword() {
      if (this.login && this.password) {
        const USER = this.userList.find(
          (item) => item.log === this.login && item.pass === this.password
        );

        if (USER) this.authorization = true;
        else this.authorization = false;
      }
    },
  },

};
</script>

<style lang="css" scoped>
.message {
  color: red;
}

.message-ivan {
  color: dodgerblue;
}
</style>