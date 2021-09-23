<template>
  <div v-loading="loading" :style="'height:'+ height">
    <iframe :src="modelerUrl" frameborder="no" style="width: 100%;height: 100%" scrolling="auto" />
  </div>
</template>

<script>
  export default {
    name: "ActivitiDesinger",
    data() {
      return {
        modelerUrl: "",
        height: document.documentElement.clientHeight - 94.5 + "px;",
        loading: true,
      };
    },
    created() {
      this.OnlineDrawingProcess()
    },
    mounted: function() {
      setTimeout(() => {
        this.loading = false;
      }, 230);
      const that = this;
      window.onresize = function temp() {
        that.height = document.documentElement.clientHeight - 94.5 + "px;";
      };
    },
    methods: {
      // 加载界面
      OnlineDrawingProcess() {
        localStorage.setItem("VUE_APP_BASE_API", process.env.VUE_APP_BASE_API)
        this.modelerUrl = "/bpmnjs/index.html?type=addBpmn";
      },
      
    }
  };
</script>
