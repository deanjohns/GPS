<template>
  <div id="app">
    <div class="appMain">
      <div class="background-div"></div>
      <div class="section-left">
        <div class="left-main">
          <div class="left-header">Sortable Post List</div>
          <div v-for="value in values" :key="value.id" class="card-content">
            <span class="content-main">{{ value.title }}</span>
            <div class="card-arrows">
              <div 
                class="up-arrow" 
                v-on:click="reArrangeUp(value.id)" 
                v-bind:style="{ 
                    display: value.id === firstEl ? 'none' : 'block',
                    top: value.id === lastEl ? '18px' : '0px'
                  }"
              >
                <i class="arrow up"></i>
              </div>
              <div 
                class="down-arrow" 
                v-on:click="reArrangeDown(value.id)" 
                v-bind:style="{ 
                    display: value.id === lastEl ? 'none' : 'block',
                    bottom: value.id === firstEl ? '18px' : '0px'
                  }"
              >
                <i class="arrow down"></i>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="section-right">
        <div class="right-main">
          <div class="right-header">
            <span>List of actions committed</span>
          </div>
          <div class="right-body">
            <span v-bind:style="{ display: history.length > 0 ? 'none' : 'block' }" class="emptyActions">No actions committed</span>
            <div v-for="event in history" :key="event.historyId" class="card-history">
              <span class="content-history">Post {{ event.postId }} moved from index {{ event.currentIndex }} to index {{ event.newIndex }}</span>
              <div class="card-button">
                <button class="travel-button" v-on:click="timeTravel(event.historyId)">Time travel</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      values: [],
      history: [],
      historyId: 0,
      firstEl: 0,
      lastEl: 0,
    };
  },
  methods: {

    //get all post data from url
    getData: function() {
      this.$http.get("https://jsonplaceholder.typicode.com/posts").
      then (function(data){
        this.values = data.body.slice(0,5);
      })
    },

    //style arrow buttons of first and last posts
    checkFirstAndLast: function() {
      this.values.forEach(each => {
        if (this.values.indexOf(each) === 0) {
          this.firstEl = each.id;
        }
        if (this.values.indexOf(each) === 4) {
          this.lastEl = each.id;
        }
      });
    },

    //get a post up
    reArrangeUp: function(id) {
      let currentIndex = 0;
      let upIndex = 0;
      this.values.forEach(each => {
        if (each.id === id) {
          currentIndex = this.values.indexOf(each);
          upIndex = currentIndex - 1;
          this.createHistory(currentIndex, upIndex, id);
        }
      });
      this.values[currentIndex] = this.values.splice(upIndex, 1, this.values[currentIndex])[0];
      this.checkFirstAndLast();
    },

    //get a post down
    reArrangeDown: function(id) {
      let currentIndex = 0;
      let downIndex = 0;
      this.values.forEach(each => {
        if (each.id === id) {
          currentIndex = this.values.indexOf(each);
          downIndex = currentIndex + 1;
          this.createHistory(currentIndex, downIndex, id);
        }
      });
      this.values[currentIndex] = this.values.splice(downIndex, 1, this.values[currentIndex])[0];
      this.checkFirstAndLast();
    },

    //create the posts history
    createHistory: function(currentIndex, newIndex, postId) {
      this.historyId += 1;
      this.history.unshift(
        {
          historyId: this.historyId,
          postId: postId,
          currentIndex: currentIndex,
          newIndex: newIndex
        }
      )
    },

    //time travel to selected moment
    timeTravel: function(historyId) {
      let travelList = [];
      let removeList = [];
      let prevHistory = this.history;
      prevHistory.some(function (each) {
        travelList.push(each);
        removeList.push(each.historyId);
        return each.historyId === historyId;
      });

      travelList.forEach(each => {
        let currentIndex = each.newIndex;
        let prevIndex = each.currentIndex;
        this.values[currentIndex] = this.values.splice(prevIndex, 1, this.values[currentIndex])[0];        
      });

      this.checkFirstAndLast();
      this.history.splice(0,removeList.length);

    }
  },

  //initial function calls
  mounted () {
    this.checkFirstAndLast();
    this.getData();
  },
};
</script>
