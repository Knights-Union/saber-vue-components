<template>
  <div class="container">
    <div v-for="(item, idx) in list" :key="item.id">
      <div class="item">
        <i
          class="icon"
          @click="
            () => {
              onRemove(idx);
            }
          "
        >
          <i class="icon-del"></i>
        </i>
        <span class="desc">{{ item.name }}</span>
        <span class="method">{{ item.method }}</span>
      </div>
      <i class="separtor" v-if="list.length - 1 > idx"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "RoleList",
  props: {
    list: Array,
    onRemove: Function
  }
};

// const mylist = [
//   {
//     id: 112345,
//     method: "或签",
//     name: "业务员A"
//   },
//   {
//     id: 2223232,
//     method: "或签",
//     name: "经理B"
//   },
//   {
//     id: 443244,
//     method: "会签",
//     name: "总经理"
//   }
// ];
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 800px;
  position: relative;
}

.container > div {
  position: relative;
  display: inline-block;
  margin-right: 50px;
}

.item {
  width: 78px;
  height: 80px;
  border: 1px solid #000;
  border-radius: 5px;
  background: center center no-repeat;
  background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAAFmklEQVR4Xu1aW4hWVRT+1j8jPkSB0vSUKRhdCYSIsqisiKxJ3OtMvxhdLLTp8pRZPVSahWakpfRQNhVmFknTnLXBLLOb6EM3hCjS7mT61HSBsCdn/hW7/hlmnP9yzpx1zvyg6+Xn56z1rW9/Z51z9t5rE45xo2N8/ChcgHK5PLVSqVw0ODh4ChF1hBugqv1tbW2/lUqlT3t7e/8s8qYUJgAz3wSgE8CNTQb4BoDtIvJ6EULkLgAzXw3gAQDhN429D2CtiITf3CxXAZh5NYCHMrJ/QkQezohRNzw3AaIoek5V77YgTkTPx3F8jwXW0Ri5COCcu5eI1lsSVtWl3vsNlpgBy1wAZi4DeNOaaBVvgYj0WmKbChBFUaeqvm1JcEzJEl0fx/F2qxymAjDzFgA3W5Grg/OaiNxilcNMgK6urrMqlcrXANqtyNXBGSiVSuf19fV9a5HHTADn3EoietSCVDMMVX3Me7+ymV+S62YCMPOHAK5MktTA5yMRucoAx+Yr0N3dPam/v/8fAJMsSCXAONLR0XFCT0/PkQS+DV1MKsA5N4eIPs5KJk28ql7hvd+VJqaWr4kAURTdqaobs5JJE09Ed8Vx/EKamNwEYOZnACzNSiZl/HoRuS9lzBh3qwrYrqrXZSWTJp6I3onjOCyvM5mJAM65V4nIbHKSZESqusV7f2sS30Y+JgIwc1iurspKJmX8IyISltuZzEQA51wXEb2ViUnKYFW9wXvflzIst3fAdFX9JSuZNPFENCOO4wNpYnL7CgRgZt4H4OyshBLG7xeRcxL6NnQzeQSqAvQAuMOCVAKMF0WkO4FfUxczAZxzjoikaUYDB1Vl7703gLJZCwwRcc7tJqJLLYjVw1DVPd77y6xymFVAIOScW0xEL1mRq4Wjqku89y9b5TAVoPouCPuBYV8wD+sVkQWWwOYCVEU4COBUS6IADonINGNM23fASHLMHHp8U4wI/yUiU42wRsHkUgEhw7x5805ub2/fAeD8jMT3DgwMzN22bdvvGXFqhucmQPVRCBOjFQAWjpP8VgCPi8j+ccY3DctVgKHszLxQVUO36MKmjP5vl39GRBtEJAiQqxUiwNAInHMzAMwBcAERhansudVr36hqmEp/AWCX976wdUWhAuR6K8cJflyAcQpXM6zaHJlGRKvjOP7ZEjuKoktUdZWqbvbev2KFnbkCOjs7p0yePHmRqi4CMGsEsWdVdZP3/sssZJl5LhEtUdWuIRxVfQ9AECIcp8lk4xbAOTcTQBj0IiI6rQGL0M4OU9jEbe1yudwxODhYVtUwpQ4vzXr2ORFtPnz48OadO3eGxkxqSy2Ac25WqVRaXL3jJ6bIeAjAJ6r6AYDv68TNBnA5gNlEdFIK7B9CRQDYKCJ/pIhLNxWOomhZpVJZkZJcGj5Zffep6pPe+9CmT2SJKmD+/PkXl0ql5QDmJkKdeKetpVJpTV9f31fNqDQVIIqi5aoaBl9U47MZ56TX/65Ww5pGAQ0FcM7tIKJrkmZsRb/wxfDe163cugIwc5iOTm/FQY2D0wERCdPwMVZTAGb+FYD55sM4iFuGHBSRMZ/rMQIw81oA91tmbiGsdSISju0O2ygBJqLFVbQ4R7fURgnAzLsB5LqtXfSAa+TbIyLD2+rDAjjnrg099xYgmDuFcJbBe/9uSDRSgNuIaFPu2VsggarePrSiHBaAmcPL4akW4FcEhQdFJLzsR1VAYQcdixhhoxwjD1qOfASOC1DUUdeWrIAoilhV44kmV0R+IoriOP6vlT/yEZhJRD8WQWCic6jq6d77n0YJEP4wc56d3Yke91D+UR3mWmsBbRWmefAQkVFjrrkajKJonaouy4PARGES0dNxHI9Z5DXaDzhDVUNn98yJIm2U9zsi2isiNTdim26JGZFoWZhjXoB/AdNZ21DF/MCgAAAAAElFTkSuQmCC");
  background-size: 72%;
  background-position: 50% 1px;
  position: relative;
}

.method {
  border-top: 1px solid #000;
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  text-align: center;
  font-size: 14px;
}

.icon {
  position: absolute;
  top: 0px;
  right: 0px;
  z-index: 4;
  overflow: hidden;
}

.icon::after {
  content: "";
  display: block;
  position: absolute;
  top: -2rem;
  right: -2rem;
  width: 3.7rem;
  height: 3.7rem;
  border-radius: 3.7rem;
  background: #1890ff;
}

.icon-del {
  display: block;
  position: relative;
  z-index: 2;
  width: 2rem;
  height: 2rem;
  transform: rotate(44deg);
  left: 0px;
}

.icon-del::before {
  content: "";
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 1rem;
  height: 0.2rem;
  margin: -0.56rem 0px 0px -0.47rem;
  background: rgb(243, 243, 243);
}

.icon-del::after {
  content: "";
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  height: 1rem;
  width: 0.2rem;
  margin: -1rem 0px 0px -0.05rem;
  background: rgb(243, 243, 243);
}

.desc {
  position: absolute;
  bottom: -26px;
  left: 0;
  right: 0;
  text-align: center;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  font-size: 14px;
}

.separtor {
  position: absolute;
  top: 0;
  left: 108%;
  height: 66px;
  width: 40px;
  background: center center no-repeat;
  background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAACl0lEQVR4Xu2aPW/UQBCGZ+xznYCgQyEREh0BBB0U0CBF0JL/cSd51q7iVPaupbv/QVoQEg0U0IHCR4eEOKJ0QXzUd+dFjnwSiXy+Jpld2ev2JM+8z7wz47UPoeMXdlw/OADOAR0n4Fqg4wZwQ9C1gGuBjhNwLdBxA5jZAlLKK4g4AIBHVQFeaa2HQohD7oKwt0CWZWue5/2oE1oUxdUoig44IbADkFI+R8THdSK11i+EEE9aCyBN03Xf9783CZzNZhtxHI+5ILA6IE3TB77vv14C4GEcx29aCaCp/+eCuecAqwNKkUqptwBwb0GF3xHRfa7ql3HYAVQQyjmwfkromIg2OMUbA1BBkABwvRL8lYgEt3ijAEyIrYtppAVsEe8cYGoIOgdYRMDYDMiybAUA1ioWB1EU/TXBxQiAPM93tNbJ/4IRMQnDcJcbAjsApdRTAHi2QOg2Ee1xQmAFMBqNVieTye8mgUEQXOj3+3+4ILACUErdAoD9JeJuE9HHVgLIsuyG53mfm8QVRbEZRdGXtgJY8Tyv0d5FUaxybgTWFiirKqVMEHGnrsJa610hxIntcN5OYAdQnQTrNgH7BjB6Fqg2wvE7gSAIxpyT/8Tzx3lbzPb7G2kBm6A4ADZVw0QuzgEmqFerMAWAa1X8b0QUm8jFiAOUUkcAcOmU4J9EdJkbAjsApVR5FC4fhOquPSLa5oTACsB9HHUfRxf/OWJu+9Z/HJVSvkfEOwtOgx+EEHdbOwNKYXmeb2qtP9WJRMSbYRg2vjA5azisQ3Ce/HA4vDidThOt9dbxkRTxZa/XSwaDwa+zFrjsfkYALEuK83cHgJO2jbGcA2ysCmdOzgGctG2M5RxgY1U4c3IO4KRtYyznABurwpnTP+clx0EhVCnBAAAAAElFTkSuQmCC");
  background-size: 92%;
  transform: rotate(90deg);
  overflow: hidden;
}
</style>
