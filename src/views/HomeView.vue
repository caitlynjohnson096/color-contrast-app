<script>
  import colorPicker from '@/components/ColorPicker.vue';
  import contrastResults from '@/components/contrastResults.vue';
  export default {
    components: {
      colorPicker,
      contrastResults
    },
    data: function () {
      return {
        forecolor:"#000000",
        backcolor:"#ffffff"
      }
    },
    methods: {
      changeForeground(c) {
        this.forecolor=c
        ;
      },
      changeBackground(a){
      this.backcolor=a
      ;
      }
    }
  }
  </script>

  <template>
    <h1> Contrast Checker</h1>
    <div id="app">
      <div class="colorPickers">
        <div class="colorpicker1">
      <colorPicker input="Foreground" v-on:colorChanged="changeForeground"/>
    </div>
    <div class="colorpicker2"></div>
      <colorPicker input="Background" v-on:colorChanged="changeBackground"/>
    </div>
      <contrastResults v-bind:contrastForeground="forecolor" v-bind:contrastBackground="backcolor"/>


    </div>
  </template>

  <style>
  #app > * {
    margin-bottom: 1em;
    color: #6897BB;
    background-color: #ffffff;
  }
  h1{
color: v-bind(forecolor);
background-color: v-bind(backcolor);
  }
.colorPickers{
display: flex;
}
.colorpicker1{
  padding-right: 100px;
}
  </style>
