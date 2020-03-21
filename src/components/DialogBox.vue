<template>
  <div class="message-box dialog-mask" @click="$close">
    <div class="dialog-content">
      <div class="dialog-body">
        <img v-bind:alt="content.ItemName" v-bind:src="content.PhotoName"/>
        <h2>{{ content.ItemName }}</h2>
        <span>{{content.ItemID}}</span>
       <div v-if="content.Description">{{content.Description}}</div>
       <div v-else>Description coming soon.</div>
       <span>{{content.Dimensions}}</span>
       <span>{{content.BasePrice | currency}}</span>
      </div>
      <footer>
        <button class="el-button" type="text"  @click="$close">Close</button>
      </footer>
    </div>
  </div>
</template>


<style scoped lang="scss">
.dialog-mask {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    display: -ms-flexbox;
    display: flex;
    -ms-flex-align: center;
    align-items: center;
    -ms-flex-pack: center;
    justify-content: center;
    background-color: rgba(0,0,0,.33);
}

.message-box .dialog-content {
    max-width: 400px;
    text-align: center;
    font-size: 16px;
}

.dialog-content {
    margin: 0 20px;
    padding: 20px 30px;
    border: 1px solid #ebeef5;
    border-radius: 4px;
    background-color: #fff;
    box-shadow: 0 2px 12px 0 rgba(0,0,0,.1);
    color: #303133;
}

.dialog-content footer {
    display: -ms-flexbox;
    display: flex;
    margin-top: 24px;
}
.dialog-content .el-button {
    -ms-flex: 1;
    flex: 1;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
}

.el-button {
    display: inline-block;
    line-height: 1;
    white-space: nowrap;
    cursor: pointer;
    background: #3a8ee6;
    border-color: #3a8ee6;
    color: #fff;
    -webkit-appearance: none;
    text-align: center;
    box-sizing: border-box;
    outline: 0;
    margin: 0;
    transition: .1s;
    padding: 12px 20px;
    font-size: 14px;
    border-radius: 4px;
    border-style: none;
}

.el-button:focus, .el-button:hover {
    color: #409eff;
    border-color: #c6e2ff;
    background-color: #ecf5ff;
}
img {
  max-width: 300px;
}
</style>