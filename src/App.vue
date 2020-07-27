<template>
  <div id="app" class="bg-secondary">
    <div class="row justify-content-center">
      <div class="col-12 text-center">
        <img alt="Vue logo" src="./assets/logo.png" />
        <h1>{{target.name}}</h1>
        <h2
          class="text-success"
          :class="{ 'text-warning': target.health <=75, 'text-danger': target.health <=50 }"
        >{{target.health}}</h2>
        <h3>{{target.hits}}</h3>
      </div>
      <div class="col-4 text-center">
        <button
          type="button"
          class="btn btn-primary m-1"
          v-for="(attack) in attacks"
          :key="attack.name"
          :disabled="target.health <= 0"
          @click="attackTarget(attack.damage)"
        >{{attack.name}}</button>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-2 text-center">
        <button
          :disabled="target.health>0"
          class="btn btn-block btn-danger m-1"
          @click="reset()"
        >Reset</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      target: {
        name: "Kayden",
        health: 100,
        hits: 0,
      },
      attacks: [
        {
          name: "Slap",
          damage: 1,
        },
        {
          name: "Kick",
          damage: 5,
        },
        {
          name: "Punch",
          damage: 10,
        },
      ],
    };
  },
  methods: {
    attackTarget(damage) {
      (this.target.health -= damage), this.target.hits++;
    },
    reset() {
      this.target.health = 100;
      this.target.hits = 0;
    },
  },
};
</script>
