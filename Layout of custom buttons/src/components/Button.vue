<template>
    <div class="sell-buy-btn-wrapper">
        <div class="sell-btn-wrapper btn-wrapper">
            <button  class="sell-btn"  :class="{active: redA, grey: redG}"  @mouseover="testClick('sell')" @click="testClick('sell')">
                <strong>SELL</strong>
                <span>
                    <slot name="sell" />
                </span>
            </button>
        </div>
        <div class="buy-btn-wrapper btn-wrapper">
            <button class="buy-btn"   :class="{active: greenA, grey: greenG}" @mouseover="testClick('buy')" @click="testClick('buy')">
                <strong>BUY</strong>
                <span>
                    <slot name="buy" />
                </span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "ButtonSB",
     data: {
    redA: false,
    redG: false,
    redN: true,
    greenA: false,
    greenN: true,
    greenG: false
  },
  data() {
      return {
          redA: this.redA,
          redN: this.redN,
          redG: this.redG,
          greenA: this.greenA,
        greenG: this.greenG,
        greenN: this.greenN,
      }
  },
    props: {
        down: {
            type: Boolean,
            default: false
        },
        up: {
            type: Boolean,
            default: false
        }
    },
    methods: {
        testClick(v) {
            if(v === "sell") {
                this.redA = true
                this.greenG = true
                this.greenA = false
                this.redG = false
            } else {
                  this.redA = false
                  this.redG = true
                this.greenG = false
                this.greenA = true
            }
             // this.isActive= !this.isActive
            console.log("click from " + v);
           
        }
    },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@500;700&display=swap');

button {
    position: relative;
    display: block;
    border: none;
    background: none;
    font-family: 'Roboto', sans-serif;
    cursor: pointer;
}

.btn-wrapper {
    display: block;
    position: relative;
}

.btn-wrapper::after {
    content: "";
    display: block;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: -1;
}

button>strong,
button>span {
    display: block;
    margin: 0;
    padding: 0;
    color: #FFFFFF;
    text-transform: uppercase;
}

button>strong {
    font-weight: 700;
    font-size: 16px;
    line-height: 19px;
}

button>span {
    font-weight: 500;
    font-size: 12px;
    line-height: 14px;
}
.sell-btn {
  
    width: 150px;
    height: 70px;
    z-index: 2;
    padding-right: 20px;
    background: url("../assets/btns/1.png") 0 0  / cover no-repeat;
}
.sell-btn.active{
    background: url("../assets/btns/1_a.png") 0 0  / cover no-repeat;
}
 .sell-btn.grey{
    background: url("../assets/btns/1_n.png") 0 0  / cover no-repeat;
}

.buy-btn {
 
    width: 150px;
    height: 70px;
    padding-left: 20px;
    background: url("../assets/btns/2.png") 0 0  / cover no-repeat;
    position: relative;
    left: -63px;
    z-index: 1;
}
.buy-btn.active {
     background: url("../assets/btns/2_a.png") 5px 10px  / 144px 57px no-repeat;
}
.buy-btn.grey {
     background: url("../assets/btns/2_n.png") 0 0 / cover no-repeat;
}

.sell-buy-btn-wrapper {
    display: flex;
}
</style>
