<template>
  <div class="chat-list-element">
    <div class="info">
      <div class="chat__logo" @click="$emit('join-chat', chat_id)">
        {{ chatLetter }}
      </div>
      <div class="chat__block">
        <div
          class="chat__name"
          v-bind:style="[
            user_id === owner_id ? { width: '70%' } : { width: '95%' },
          ]"
          @click="$emit('join-chat', chat_id)"
        >
          {{ chat_name }}
        </div>
        <div class="form_btn" v-if="user_id === owner_id" @click="$emit('delete-chat', chat_id)">
          <form class="button_form">
            <div class="delete_btn left__btn">Delete</div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatListElement",
  props: ["chat_name", "chat_id", "owner_id", "user_id"],
  data() {
    return {
      active: false,
      chatLetter: "",
    };
  },
  created() {
    this.chatLetter = this.chat_name[0].toUpperCase();
  },
};
</script>

<style scoped>
.chat_list_element,
.info,
.chat__logo,
.chat__block {
  display: flex;
}

.chat_list_element {
  overflow: hidden;
  justify-content: space-between;
}

.info {
  margin-right: auto;
  width: 646px;
  min-height: 61px;
  margin-bottom: 10px;
  overflow-wrap: break-word;
}

.chat__block {
  overflow: auto;
  box-sizing: border-box;
  width: 90%;
}

.info:hover {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border: 2px solid;
  background-color: lavender;
}

.chat__name,
.chat__logo,
.button_form {
  font-family: "Playfair Display", serif;
  font-size: 22px;
}

.chat__name {
  padding: 12px 15px 12px 15px;
  float: right;
  cursor: pointer;
}

.chat__logo {
  background-color: black;
  color: white;
  margin-top: 1px;
  margin-left: 15px;
  width: 55px;
  height: 55px;
  border-radius: 50%;
  justify-content: center;
  align-items: center;
}

.form_btn {
  width: 120px;
  position: relative;
  border: 2px solid rgb(137, 137, 137);
  margin-top: 6px;
  height: 50px;
  margin-bottom: 5px;
}

.form_btn:hover {
  background-color: black;
  color: white;
  border: 2px solid black;
  cursor: pointer;
}

.button_form {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 23%;
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
}
</style>