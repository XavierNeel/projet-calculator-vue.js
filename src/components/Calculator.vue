<template>

<div class="calculator">
    <div class="input" id="input">
        {{ output }}
    </div>
  
    <div class="buttons">
        <div class="leftPanel">
            <div class="numbers">
                <div @click= "getNumber('7')">7</div>
                <div @click= "getNumber('8')">8</div>
                <div @click= "getNumber('9')">9</div>
            </div>
            <div class="numbers">
                <div @click= "getNumber('4')">4</div>
                <div @click= "getNumber('5')">5</div>
                <div @click= "getNumber('6')">6</div>
            </div>
            <div class="numbers">
                <div @click= "getNumber('1')">1</div>
                <div @click= "getNumber('2')">2</div>
                <div @click= "getNumber('3')">3</div>
            </div>
            <div class="numbers"> 
                <div @click= "getNumber('0')">0</div>
                <div @click= "getDot()">.</div>
                <div @click="clear">C</div>
            </div>
        </div>
        <div class="operators">
            <div @click="getOperation('addition')">+</div>
            <div @click="getOperation('substraction')">-</div>
            <div @click="getOperation('multiplication')">*</div>
            <div @click="getOperation('division')">/</div>
        </div>
    </div>
    <div @click="result" class="equal" id="result">=</div>
</div>
</template>

<script>
export default {
    data() {
        return {
            output:'',
            previousValue: null,
            nextValue: false,
        }
    },
    methods: {
        clear() {
            this.output = ''
        },
        getNumber(number) {
            if(this.nextValue){
                this.output = '';
                this.nextValue = false;
            }
            this.output =`${this.output}${number}`;
        },
        getDot() {
            if(this.output.indexOf('.') === -1) {
                this.output = this.output + '.' ;
            }
        },
        getOperation(string) {
            switch (string){
                case 'addition':
                    this.operation = (a,b) => {
                        return parseFloat(a) + parseFloat(b);
                    }
                    break;
                case 'substraction':
                    this.operation = (a,b) => {
                        return parseFloat(a) - parseFloat(b);
                    }
                    break;
                case 'multiplication':
                    this.operation = (a,b) => {
                        return parseFloat(a) * parseFloat(b);
                    }
                    break;
                case 'division':
                    this.operation = (a,b) => {
                        return parseFloat(a) / parseFloat(b);
                    }
                    break;
                }
                this.previousValue = this.output;
                this.nextValue = true;
            },
            result() {
                this.output = `${this.operation(this.previousValue, this.output)}`;
                this.previousValue = null;
            }
        }
    }
</script>

<style>

body {
    width: 23%;
    margin: 5% auto;
    font-family: 'Source Sans Pro', sans-serif;
    font-size: 1.8rem;
}

.calculator {
    background-color: #e4e1e1;
    -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    border-radius: 1px;
}

.input {
    color: white;
    margin-left: 2%;
    margin-right: 2%;
    width: 96%;
    background-color: #000000;
    border: 1px solid #ddd;
    border-radius: 1px;
    height: 60px;
    text-align: right;
    margin-right: 6px;
    font-size: 2.5rem;
    overflow-x: auto;
    transition: all .2s ease-in-out;
}

.input:hover {
    border: 1px solid #3d3c3c;
    -webkit-box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    box-shadow: inset 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
}

.operators {
    display: flex;
    flex-direction: column;
    width: 25%;
}

.operators div {
    color: white;
    display: inline-block;
    border: 1px solid #ec441a;
    border-radius: 1px;
    width: 80px;
    text-align: center;
    padding: 10px;
    margin: 10px 4px 10px 4px;
    cursor: pointer;
    background-color: #ec441a;
    transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}

.operators div:hover {
    -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    opacity:0.5;
}

.operators div:active {
  font-weight: bold;
}

.leftPanel {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left:2%;
}

.numbers div {
    color: white;
    display: inline-block;
    border: 1px solid #000000;
    border-radius: 1px;
    width: 80px;
    text-align: center;
    padding: 10px;
    margin: 10px 4px 10px 0;
    cursor: pointer;
    background-color: #000000;
    transition: border-color .2s ease-in-out, background-color .2s, box-shadow .2s;
}

.numbers div:hover {
    -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
    opacity: 0.5;
}

.numbers div:active {
    font-weight: bold;
}

.equal {
    border: 1px solid #ec441a;
    border-radius: 1px;
    width: 96%;
    text-align: center;
    margin-left: 2%;
    margin-right: 2%;
    vertical-align: top;
    cursor: pointer;
    color: #FFF;
    background-color: #ec441a;
    transition: all .2s ease-in-out;
}

div.equal:hover {
  -webkit-box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 1px 4px 0px rgba(0, 0, 0, 0.2);
  opacity: 0.5;
}

div.equal:active {
  font-weight: bold;
}
.buttons {
    display:flex;
}


</style>