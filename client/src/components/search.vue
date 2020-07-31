<template>
  <section class="search">
    <h1>Apex Stats</h1>
    <form v-on:submit.prevent="onSubmit">
      <div class="form-group">
        <label for="platform">Platform</label>
        <select name="platform" id="platform" v-model="platform">
          <option value="psn">PlayStation</option>
          <option value="xbl">Xbox</option>
          <option value="origin">Origin</option>
        </select>
      </div>
      <div class="form-group">
        <label for="gamertag">Gamertag</label>
        <input type="text" name="text" v-model="gamertag" id="gamertag" placeholder="Player name...">
      </div>
      <div class="form-group">
        <input type="submit" value="Submit" class="btn">
      </div>
    </form>
  </section>
</template>

<script>
  export default {
    name: 'Search',
    data() {
      return {
        platform: "xbl",
        gamertag: ""
      };
    },
    beforeCreate(){
      document.body.className="body-bg-image";
    },
    methods:{
      onSubmit(){
        if(!this.gamertag){
          this.$toasted.show("Enter Gamertag",{
            duration: 3000,
            icon: "exclamation-circle"
          });
        }
        else{
          this.$router.push(`/profile/${this.platform}/${this.gamertag}`);
        }
      }
    }
  };

</script>

<style>

</style>
