<template>
    <footer class="footer">
        <div class="container text-left" v-once>
            <ul>
                <li>粘粘游鱼&nbsp;
                    <a href="javascript:;" rel="nofollow" target="_blank" title="粘粘记录器">{{codeVersion}}
                    </a>&nbsp;Copyright (c) 2018 &nbsp;
                    <a href="" rel="nofollow" target="_blank">
                        <!-- {{systemConfig.data[0].registrationNo}} -->
                        鄂ICP 181862号-2
                    </a> All Rights Reserved</li>
                <li class="sitemap">
                    <!-- <router-link to="/sitemap.html" class="">站点地图</router-link>&nbsp;: -->
                    <!-- <a href="http://www.dailyads.cn" target="_blank">每日一广告</a>&nbsp; -->
                </li>
            </ul>
        </div>
    </footer>
</template>
<script>
let packageJson = require("../../../package.json");

import { mapGetters, mapActions } from "vuex";
export default {
  name: "Footer",
  async asyncData({ store, route }, config = {}) {
    const { params: path } = route;
    const base = {
      ...config,
      path
    };
    await store.dispatch("global/footerConfigs/getSystemConfig");
  },
  serverCacheKey: props => "footer",
  computed: {
    ...mapGetters({
      systemConfig: "global/footerConfigs/getSystemConfig"
    }),
    codeVersion() {
      return "good baby " + packageJson.version;
    }
  }
};
</script>
<style lang="scss">

</style>
