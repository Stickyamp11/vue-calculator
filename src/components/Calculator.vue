<template lang="html">
<div class="backgroundStyled"></div>
  <section class="calculator">
    <template class="row main-zone rounded">

        <div class="col-12 m-4 p-4 resultArea rounded">{{previosValue == '' ? '' : previosValue}} {{operator == '' ? ' ' : operator}} {{inputValue == '' ? 0 : inputValue}}</div>

        <div class="col-12 p-5 buttonsArea">
          <div class="row ">
            <div class="col-3 pt-2 pb-2" v-for="x in calculatorInputs" :key="x" >
              <button class="btn buttonCalc pt-4 pb-4"  :class="{'green': ['CE','/','-','+','%','=','x','(',')'].includes(x)}" v-on:click="processOperation(x)">
                {{x}}
              </button>
            </div>

          </div>


        </div>


    </template>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'calculator-vue',
    props: [],
    mounted () {

    },
    data () {
      return {
        inputValue: '',
        operator: null,
        previosValue: '',
        calculatorInputs: ['(',')','%','CE',7,8,9,'/',4,5,6,'x',1,2,3,'-',0,'.','=','+'],
      }
    },
    methods: {

      processOperation (calcInput) {
       
        try {

          if(!isNaN(calcInput) || calcInput === '.') {
            this.inputValue = this.inputValue += calcInput + '';
          }

          if(['/','-','+','x'].includes(calcInput)){
            if(calcInput === 'x') {
              calcInput = '*';
            }
            this.operator = calcInput;
            this.previosValue = this.inputValue;
            this.inputValue = '';
          }

          if(calcInput === 'CE'){
            this.operator = null;
            this.previosValue = '';
            this.inputValue = '';
          }

          if( calcInput === '%'){
            this.inputValue = this.inputValue / 100 + '';
          }

          if( calcInput === '='){
            if(this.previosValue !== '' && this.operator !== null && this.inputValue !== '') {
          
            this.inputValue = eval(this.previosValue + this.operator + this.inputValue);
            this.previosValue = '';
            this.operator = null;
            
            }
            else
            {
              console.error('Bad usage of calculator');
            }
          }


        }
        catch (error) {
          console.log('Something wrong happened',error);

        }
      },

    },
    computed: {

    }
}


</script>

<style scoped lang="scss">
  .calculator {
    justify-content: center;
    align-items: center;
    display: flex;
    width: 100%;
    height: 100%;
    background-color: transparent;
  }

  .main-zone{
    width: 40%;
    justify-content: center;
    align-items: center;
    display: flex;
    background-color: rgb(62, 65, 62);
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }

  .resultArea{
    text-align: right;
    width: 90%;
    height: 15%;
    background-color: rgb(201, 202, 201);
    font-size: 2rem;
    font-weight: 500;

  }

  .green{
    background-color: rgb(130, 199, 139) !important;
  }

  .buttonCalc{
    color: white;
    background-color: rgb(119, 117, 117);
    width: 60%;
  }
  .buttonCalc:hover{
    background-color: rgb(155, 223, 155) !important;
    transition: .5s;
  }

  .backgroundStyled{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgb(64,130,105);
    background: linear-gradient(78deg, rgba(64,130,105,1) 16%, rgba(97,210,168,1) 77%, rgba(97,210,168,1) 77%, rgba(138,245,138,1) 100%);
    z-index: -1;
  }

 @media only screen and (max-width: 1000px) {

  .buttonCalc{

    width: 100%;
  }

 }
 @media only screen and (max-width: 600px) {
 
  .buttonCalc{

    width: 3.5rem;
  }

  .calculator {
    margin: 0;
    justify-content: center;
    align-items: center;
    display: flex;
    width: 100%;
    height: 100%;
    background-color: transparent;
  }

  .main-zone{
    width: 90%;
    justify-content: center;
    align-items: center;
    display: flex;
    background-color: rgb(62, 65, 62);
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }

  .resultArea{
    text-align: right;
    width: 90%;
    height: 15%;
    background-color: rgb(201, 202, 201);
    font-size: 2rem;
    font-weight: 500;

  }
}
    
  
</style>
