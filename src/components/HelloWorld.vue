<template>
  <div>
    <input type="text" placeholder="Input link here" v-model="linkInput"> |
    <button @click="getLink()" type="submit">Generate shortened link</button>
    <br>
    <h1> shorten url: </h1>
    <a :href="linkOutput.short_url" target="_blank">{{ linkOutput.short_url }}</a>
    <hr>
  </div>
</template>

<script>
export default {
  data() {
    return {
      linkInput: '',
      linkOutput: '',
    }
  },
  methods: {
    async getLink() {

      const url = new URL(
        "https://t.ly/api/v1/link/shorten"
      );

      const headers = {
        "Authorization": "Bearer UMs01GFU1vhLFcBBFVTFxwowKAXAFv3UuLj1KA0sZtQsjNg12Iqa3SPiBKrY",
        "Content-Type": "application/json",
        "Accept": "*/*",
      };

      let body = {
        "long_url": this.linkInput,
        "domain": "https://t.ly/",
        "expire_at_datetime": "2035-01-17 15:00:00",
        "description": '',
        "public_stats": true,
      };

      this.linkOutput = await fetch(url, {
        method: "POST",
        headers,
        body: JSON.stringify(body),
      }).then(
        async (response) => {
          if (!response.ok) {
            const msg = await response.json()
            this.linkOutput = new Error(msg.message)
            return this.linkOutput
          }
          return await response.json()
        }
      )
    }
  }
}
</script>


<style scoped></style>
