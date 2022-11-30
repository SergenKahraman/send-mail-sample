<template>
  <div
    style="
      display: flex;
      flex-direction: column;
      justify-items: center;
      justify-content: center;
    "
    class="hello"
  >
    <h1>Mail Denemesi</h1>

    <div style="display: flex; flex-direction: row; justify-content: center">
      <div
        style="
          display: flex;
          flex-direction: column;
          align-items: flex-start;
          width: 30%;
        "
        class="form"
      >
        <label for="name">Adınız</label>
        <input v-model="name" style="width: 100%" id="name" type="text" />
        <label for="name">Mailiniz</label>
        <input v-model="mail" style="width: 100%" id="mail" type="text" />
        <label for="name">Mesajınız</label>
        <textarea
          v-model="content"
          style="width: 100%"
          id="content"
          cols="30"
          rows="10"
        ></textarea>
        <button @click="submit" style="margin-top: 15px" id="submit">
          Gönder
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
import Email from "../helpers/smtp.js";
</script>
<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      name: null,
      mail: null,
      content: null,
    };
  },
  methods: {
    submit() {
      //TODO: ücretsiz bir hesap aç ve devam et !!!!!!!!!!!!!!!!!!!!
      Email.send({
        Host: "in-v3.mailjet.com",
        Username: "info@3amakinateknolojileri.com.tr",
        Password: "3amakine123",
        To: "sergen_kahraman_@hotmail.com",
        From: "info@3amakinateknolojileri.com.tr",
        Subject: "This is the subject",
        Body: "And this is the body",
      }).then((message) => alert(message));
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form label {
  margin-top: 20px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
