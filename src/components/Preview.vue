<template>
  <div class="preview-wrap">
    <div class="preview-item" v-for="item in items" :key="item.id">
      <img class="preview-img" :src="item.image" />
      <span class="preview-text">{{ item.text }}</span>
      <span class="preview-subtext">{{ item.subtext }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Preview",
  data: function() {
    return {
      items: [
        {
          id: "1",
          text: "Hand made",
          subtext:"by local bakeries",
          image: require("../assets/preview-chief.png")
        },
        {
          id: "2",
          text: "Same price as from bakery",
          subtext:"- but simpler",
          image: require("../assets/preview-coin.png")
        },
        {
          id: "3",
          text: "Send cakes",
          subtext:"anywhere",
          image: require("../assets/preview-delivery.png")
        }
      ]
    };
  }
};
</script>

<style scoped>
.preview-wrap {
  padding: 100px 0 80px;
  display: flex;
  justify-content: center;
}
.preview-item {
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  align-items: center;
  width: 20%;
  font-size: 13px;
}

.preview-item:nth-child(2){
    flex-basis: 25%;
    margin: 0 50px;
}

.preview-img {
  border-radius: 50%;
  background-color: #e7e7e7;
  width: 10vw;
  max-width: 120px;
}

.preview-text {
    padding-top: 18px;
}
</style>
