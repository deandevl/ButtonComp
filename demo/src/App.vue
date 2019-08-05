<template>
  <div class="demo_container">
    <div class="buttons_box">
      <button-comp
          :css_variables="styled_css_variables"
          v-on:button_comp_clicked="change_font_weight">Change Font Weight
      </button-comp>

      <button-comp
          :css_variables="increase_css_variables"
          v-on:button_comp_clicked="increase_font_size">Increase Font Size
      </button-comp>

      <button-comp
          :css_variables="decrease_css_variables"
          v-on:button_comp_clicked="decrease_font_size">Decrease Font Size
      </button-comp>
    </div>

    <p :style="{fontSize: target_font_size + 'px', fontWeight: target_font_weight}">{{target_text}}</p>
  </div>
</template>

<script>
  import ButtonComp from 'buttoncomp';

  export default {
    name: 'App',
    data: function() {
      return {
        target_text: 'We have no oranges today.',
        target_font_size: 12,
        target_font_weight: 'normal',
        increase_css_variables: {
          button_comp_font_size: '1.2rem',
          button_comp_color: 'green'
        },
        decrease_css_variables: {
          button_comp_font_size: '1.2rem',
          button_comp_color: 'red'
        },
        styled_css_variables: {
          button_comp_font_size: '1.2rem',
          button_comp_background: 'linear-gradient(to bottom, #a3ff33 0, #3cc72a 13%, #2eba1e 33%, #4bba37 64%, #4bba37 100%)',
          button_comp_hover_background: 'linear-gradient(to bottom, #a3ff33 0, #4bba37 100%)'
        }
      };
    },
    components: {
      ButtonComp
    },
    methods: {
      //functions that responds to 'button_comp_clicked' events
      change_font_weight: function(){
        console.log('Button "font-weight" clicked');
        if(this.target_font_weight === 'normal') {
          this.target_font_weight = 'bold';
        }else {
          this.target_font_weight = 'normal';
        }
      },
      increase_font_size: function(){
        console.log('Button "increase font-size" clicked');
        this.target_font_size += 12;
      },
      decrease_font_size: function(){
        console.log('Button "decrease font-size" clicked');
        this.target_font_size -= 12;
      }
    }
  }
</script>

<style>
  .demo_container {
    padding: 30px;
  }
  .buttons_box {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    height: 100%;
    max-width: 70rem;
    max-height: 60rem;
    margin-top: 40px;
  }
  p {
    margin-top: 50px;
  }
</style>