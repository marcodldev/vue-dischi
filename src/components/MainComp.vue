<template>
  <div>
    <div class="calc">
      <div class="card p-4">
        <div class="card" style="width: 18rem">
          <img :src="card.poster" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">{{card.title}}</h5>
            <p class="card-text">
                {{card.author}} <br>
                {{card.year}}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainComp",
  props: {
    card: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
    background-color: #424242;
    height: 450px;
    border: none;

  img {
    height: 250px;
    width: 250px;
    align-self: center;
  }

  h5 {
    color: white;
  }

  p {
    color: lightslategray;
  }
}


</style>