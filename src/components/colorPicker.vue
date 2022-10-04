<script>
  export default {
    data: function () {
      return {
        color: "",
      }
    },
    methods: {
      pickColor() {
        this.$emit('colorChanged', this.color)
      }
    },
  props: {
    input: String,

  }
  }
  </script>

  <template>
    <div class='announcementInput'>
      <p> {{input}}</p>
      <input type="text" v-model="color"  />
      <button v-on:click="pickColor()">Pick Colors</button>
    </div>

  </template>

  <style>
  input {
    border: 1px solid black;
    border-radius: 3px;
    padding: 10px;
    font-size: 20px;
  }

  button {
    border: 1px solid black;
    border-radius: 3px;
    padding: 10px;
    margin-left: 15px;
    font-size: 20px;
  }
  </style>



<style>
input {
  border: 1px solid black;
  border-radius: 3px;
  padding: 10px;
  font-size: 20px;
}

button {
  color: #ffffff;
    background-color:  #6897BB;
  border-radius: 3px;
  padding: 10px;
  margin-left: 15px;
  font-size: 20px;
}

</style>
