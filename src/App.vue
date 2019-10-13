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
              <div class="up-arrow">
                <i class="arrow up"></i>
              </div>
              <div class="down-arrow">
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
            <div class="card-history">
              <span class="content-history">Post 1 moved from index 1 to index 4</span>
              <div class="card-button">
                <button class="travel-button">Time travel</button>
              </div>
            </div>
            <div class="card-history">
              <span class="content-history">Post 1 moved from index 1 to index 4</span>
              <div class="card-button">
                <button class="travel-button">Time travel</button>
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
      values: [
        {
          userId: 1,
          id: 1,
          title:
            "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
          body:
            "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
        },
        {
          userId: 1,
          id: 2,
          title: "qui est esse",
          body:
            "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
        },
        {
          userId: 1,
          id: 3,
          title: "ea molestias quasi exercitationem repellat qui ipsa sit aut",
          body:
            "et iusto sed quo iure\nvoluptatem occaecati omnis eligendi aut ad\nvoluptatem doloribus vel accusantium quis pariatur\nmolestiae porro eius odio et labore et velit aut"
        },
        {
          userId: 1,
          id: 4,
          title: "eum et est occaecati",
          body:
            "ullam et saepe reiciendis voluptatem adipisci\nsit amet autem assumenda provident rerum culpa\nquis hic commodi nesciunt rem tenetur doloremque ipsam iure\nquis sunt voluptatem rerum illo velit"
        },
        {
          userId: 1,
          id: 5,
          title: "nesciunt quas odio",
          body:
            "repudiandae veniam quaerat sunt sed\nalias aut fugiat sit autem sed est\nvoluptatem omnis possimus esse voluptatibus quis\nest aut tenetur dolor neque"
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: -webkit-fill-available;
  background-color: #f5f5f5;
}
.background-div {
  padding: 10px 30px 10px 10px;
  background-color: #845bff;
  -webkit-clip-path: polygon(100% 0, 0 100%, 0 0);
  clip-path: polygon(100% 0, 0 100%, 0 0);
  height: 150px;
  position: absolute;
  width: calc(100% - 40px);
}
.appMain {
}
.section-left {
  width: calc(50% - 50px);
  padding: 25px;
  float: left;
  position: relative;
}
.left-main {
}
.left-header {
  font-size: 20px;
  font-weight: 600;
  text-align: left;
  padding-bottom: 16px;
  color: #fff;
}
.card-content {
  height: 52px;
  background-color: #fff;
  padding: 8px;
  border-radius: 4px;
  box-shadow: 3px 7px 13px #888888;
  display: flex;
  justify-content: space-between;
  margin-bottom: 24px;
}
.content-main {
  width: 94%;
  text-align: left;
  padding-top: 15px;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 1;
  display: -webkit-box;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
}
.card-arrows {
  width: 6%;
  position: relative;
}
.card-arrows div {
  position: absolute;
  right: 0px;
  font-size: 20px;
  cursor: pointer;
}
.up-arrow {
  top: 0px;
}
.down-arrow {
  bottom: 0px;
}
i {
  border: solid #505050;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
}
.up {
  transform: rotate(-135deg);
  -webkit-transform: rotate(-135deg);
}

.down {
  transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
}
.section-right {
  width: calc(50% - 50px);
  padding: 25px;
  float: left;
  position: relative;
}
.right-main {
    box-shadow: 2px 4px 14px #888888;
    border-radius: 4px;
    background-color: #f5f5f5;
}
.right-header {
    background-color: #fff;
    padding: 12px;
    border-radius: 4px 4px 0px 0px;
    font-size: 20px;
    font-weight: 600;
    text-align: left;
}
.right-header span {

}
.right-body {
  padding: 15px;
}
.card-history {
  height: 38px;
  background-color: #fff;
  padding: 8px;
  border-radius: 4px;
  box-shadow: 1px 3px 14px #888888;
  display: flex;
  justify-content: space-between;
  margin-bottom: 2px;
}
.content-history {
  width: 94%;
  text-align: left;
  padding-top: 10px;
  font-size: 15px;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 1;
  display: -webkit-box;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
}
.card-button {

}
.travel-button {
    width: 94px;
    background-color: #8ef98e;
    color: #080;
    border: none;
    border-radius: 4px;
    height: 100%;
    font-size: 14px;
    font-weight: 600;
    transition: 0.3s;
}
.travel-button:hover {
    background-color: #080;
    color: #8ef98e;
    cursor: pointer;
}
.travel-button:focus {
    outline: none;
}

@media only screen and (max-width: 991px) {
  .section-left, .section-right {
    width: calc(100% - 50px);
  }
}
</style>
