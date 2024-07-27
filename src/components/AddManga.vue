<template>
    <div class="modal" v-if="visible">
    <div class="modal-content">
      <span class="closeM" @click="closeModal">&times;</span>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: { 
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    closeModal() {
      this.$emit('close');
    }
  }
}
</script>

<style>

.modal {
  display: block;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 70%;
  border-radius: 10px;
}

.closeM {
  align-self: end;
  color: #aaa;
  font-size: 28px;
  font-weight: bold;
}

.closeM:hover,
.closeM:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

form {
  display: flex;
  align-items: center;
  flex-direction: column;
}

h2 {
    margin-bottom: 5px;;
}

.form-element {
    border: 1px solid #e1d9d9;
    padding: 5px 10px 8px;
    margin: 5px;
    width: 500px;
    background: #0002;
    border-radius: 5px;
}

input:focus {
    border-color: #2020209f;
    outline: none;
}

#Status {
  width: 525px;
}

#mangafile {
  margin: 6px;
  background-color: #0002;
  border-radius: 5px;
  padding: 5px;
  width: 515px;
}


#check {
  color: #373636;
  align-self: end;
  padding: 6px;
  border: 0.5px solid #7f7e7e;
  border-radius: 6px;
  box-shadow: 1px 1px 1px #808080db;
  width: 60px;
  background-color: #c1c5d9;
  font-size: 14px;
  font-weight: bold;
}

#check:hover,
#check:focus {
  color: black;
  border: 1px solid black;
  text-decoration: none;
  cursor: pointer;
}


</style>