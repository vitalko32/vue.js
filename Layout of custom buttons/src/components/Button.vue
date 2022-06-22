<template>
    <div class="sell-buy-btn-wrapper">
        <div class="sell-btn-wrapper btn-wrapper">
            <button class="sell-btn" @click="testClick('sell')">
                <strong>SELL</strong>
                <span>
                    <slot name="sell" />
                </span>
            </button>
        </div>
        <div class="buy-btn-wrapper btn-wrapper">
            <button class="buy-btn" @click="testClick('buy')">
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

.sell-buy-btn-wrapper {
    display: flex;
}

.sell-btn {
    position: relative;
    padding: 7.5px 60.5px 7.5px 34px;
    mask-image: url("../assets/sell.svg");
    mask-size: contain;
    mask-position: center;
    mask-repeat: no-repeat;
    border: 1px solid;
    border-image-source: linear-gradient(263.05deg, #9E291D 0%, #EA6E61 42.28%, #C02313 84.57%);
}

.sell-btn:active {
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25)) drop-shadow(-4px 0px 12px #5B0D05);
}

.sell-btn::before {
    content: "";
    position: absolute;
    top: -50px;
    right: -50px;
    bottom: -50px;
    left: -50px;
    display: block;
    z-index: -1;
    background: linear-gradient(250deg, #E44232 28.32%, #C22B1C 82.02%);
    transition: transform 0.5s ease-in-out;
}

@media (hover: hover) {
    .sell-btn:hover::before {
        transform: rotate(180deg);
    }
}

.sell-btn-wrapper::after {
    background: rgba(228, 65, 50, 0.7);
    filter: blur(12px);
    border-radius: 50px 0 50px 50px;
}

.buy-btn {
    padding: 7.5px 34px 7.5px 55px;
    mask-image: url("../assets/buy.svg");
    mask-size: contain;
    mask-position: center;
    mask-repeat: no-repeat;
    margin-left: -48px;
    border: 1px solid;
    border-image-source: linear-gradient(95.75deg, #1AB670 21%, #57D69C 56.19%, #13AB66 92.12%);
}

.buy-btn::before {
    content: "";
    position: absolute;
    top: -50px;
    right: -50px;
    bottom: -50px;
    left: -50px;
    display: block;
    z-index: -1;
    background: linear-gradient(110deg, #39CA85 43.57%, #41A073 98.33%);
    transition: transform 0.5s ease-in-out;
}

@media (hover: hover) {
    .buy-btn:hover::before {
        transform: rotate(180deg);
    }
}

.buy-btn-wrapper::after {
    background: rgba(37, 212, 130, 0.7);
    filter: blur(12px);
    border-radius: 50px 50px 50px 0;
}
</style>