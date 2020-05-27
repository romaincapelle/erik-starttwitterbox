<template>
  <div>
    <h1>Project Twitter Box Client</h1>
    <div class="box">
      <textarea type="text" v-model="tweet" />
      <button @click="sendTweet">Tweeter</button>
      <div class="count">
        <p>{{ remainingLetterCount }}/280</p>
      </div>
    </div>
    <div class="alert" v-if="tweetTooLong">
      <p>
        Tweets must be less than 280 characters
      </p>
    </div>
    <div class="box tweets" v-for="tweet in tweets" :key="tweet">
      <div>
        <p>{{ tweet }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TwitterBox",
  data() {
    return {
      tweet: "",
      tweets: []
    }
  },
  computed: {
    remainingLetterCount: function() {
      return 280 - this.tweet.length
    },
    tweetTooLong: function() {
      return this.remainingLetterCount <= 0 ? true : false
    }
  },
  methods: {
    sendTweet() {
      if (!this.tweetTooLong) {
        this.tweets.push(this.tweet)
        this.tweet = ""
      } else {
        alert("Tweet is too long !")
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  width: 33%;
  border: #1da1f2 2px solid;
  height: 100px;
  margin: 0 auto 20px auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 10px 10px -5px rgba(0, 0, 0, 0.04);
}
.count {
  margin-right: 20px;
  margin-left: 20px;
  color: #1da1f2;
  font-weight: 400;
  padding: 5px 15px;
}
.tweets {
  background-color: #1da1f2;
  color: white;
}
.tweets div {
  padding: 2%;
}
.alert {
  width: 33%;
  margin: 0 auto;
  color: white;
  background: red;
  padding: 20px 20px;
}
button {
  margin-left: 20px;
  padding: 18px 28px;
  border-radius: 15px 50px 30px 5px;
}
textarea {
  min-width: 45%;
  min-height: 50px;
  margin-left: 20px;
  padding: 2%;
  font-size: 14px;
}
button {
  margin-left: 20px;
  padding: 18px 28px;
  border-radius: 50px 50px 50px 50px;
  background-color: #1da1f2;
  color: white;
  font-weight: 600;
  border: 0px;
}
</style>
