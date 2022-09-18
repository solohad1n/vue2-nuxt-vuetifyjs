<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8>
      <v-card min-width="400">
        <v-card-title> <h1>Nuxt Чат</h1> </v-card-title>
        <v-card-text>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :counter="16"
              :rules="nameRules"
              label="Ваше имя"
              required
            ></v-text-field>

            <v-text-field
              v-model="room"
              :rules="roomRules"
              label="Введите комнату"
              required
            ></v-text-field>

            <v-btn
              :disabled="!valid"
              color="primary"
              class="mr-4"
              @click="submit"
            >
              Войти
            </v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  layout: "empty",
  sockets: {
    connect: function () {
      console.log("socket connected");
    },
  },
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Введите имя",
      (v) => (v && v.length <= 16) || "Имя не должно привышать 16 символов",
    ],
    room: "",
    roomRules: [(v) => !!v || "Введите комнату"],
  }),

  methods: {
    submit() {
      this.$refs.form.validate();
    },
  },
};
</script>