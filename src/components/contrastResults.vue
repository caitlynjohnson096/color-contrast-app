<script>
  import ColorContrastChecker from 'color-contrast-checker';
import Contrast from 'color-contrast-checker';
  export default {
    data: function () {
      return {
        // contrastForeground: '#000000',
        // contrastBackground: "#ffffff",
        fontAA: " ",
        fontAAA: "",
        contrastRatio: 21,
        colorAA: "",
        colorAAA: ""
      }
    },
    props: {
      // colorContrast: {
      //   type: Number
      // },
      contrastForeground:{
        type: String
      },
      contrastBackground:{
        type: String
      }
    },
    watch: {
      contrastForeground: function () {
        console.log("foregroun")
        var ccc = new Contrast();
        var color1 = this.contrastBackground;
        var color2 = this.contrastForeground;
        if(ccc.isLevelAA(color1,color2,16)){
            this.fontAA = "Passed";
            this.colorAA = "#008000";
        }
        else{
          this.fontAA ="Failed";
          this.colorAA ="#D2042D";
        }
        if(ccc.isLevelAAA(color1,color2,8)){
        this.fontAAA = "Passed";
        this.colorAAA = "#008000";
       }
       else{
        this.fontAAA = "Failed";
        this.colorAAA = "#D2042D";
       }
       var l1 = ccc.hexToLuminance(color1); /* higher value */
      var l2 = ccc.hexToLuminance(color2); /* lower value */
      this.contrastRatio = ccc.getContrastRatio(l1, l2);
      },
      contrastBackground: function () {
        console.log("contrast background");
        var ccc = new Contrast();
        var color1 = this.contrastBackground;
        var color2 = this.contrastForeground;
        console.log(this.contrastRatio + "the contrast ratio");
        console.log(color1 + "background");
        console.log(color2 + "foreground ");
        if(ccc.isLevelAA(color1,color2,16)){
            this.fontAA = "Passed";
            this.colorAA = "#008000";
        }
        else{
          this.fontAA ="Failed";
          this.colorAA ="#D2042D";
        }
        if(ccc.isLevelAAA(color1,color2,8)){
        this.fontAAA = "Passed";
        this.colorAAA = "#008000";
       }
       else{
        this.fontAAA = "Failed";
        this.colorAAA ="#D2042D";
       }
        var l1 = ccc.hexToLuminance(color1); /* higher value */
      var l2 = ccc.hexToLuminance(color2); /* lower value */
      this.contrastRatio = ccc.getContrastRatio(l1, l2);
      }
    }
  }
  </script>

  <template>
<div>
      <h1> Contrast Results</h1>
      <div class="two-column">
      <div class="thelevels">
      <div class="aa">
      <p><strong>AA: </strong>{{ this.fontAA }} </p>
    </div>
    <div class="aaa">
      <p><strong>AAA: </strong> {{this.fontAAA}}</p>
    </div>
  </div>
    <div class="ratio">
      <p> <strong>Contrast Ratio: </strong> </p>
<div class="number">
      <p>{{ this.contrastRatio}}</p>
    </div>
    </div>
  </div>
    </div>
  </template>

  <style>
  strong {
    font-weight: bold;
  }
  h1{
    color:v-bind(forecolor);
    background-color: v-bind(backcolor);
    text-align: center;
    padding-bottom: 60px;;
  }
  p{
    font-size: 32px;
  }
  .thelevels{
    padding-right: 300px;
  }
  .aa p{
    color: v-bind(colorAA);
    padding-bottom: 60px;


  }
  .aaa p{
    color: v-bind(colorAAA);

  }
  .ratio{
    font-size: 40px;
    text-align:center;
    padding: 20px;
    border: 4px solid #6897BB;


  }
  .number p{
    font-size: 60px;
  }
  .two-column{
    display: flex;
  }



  </style>
