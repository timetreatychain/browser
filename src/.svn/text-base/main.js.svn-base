// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import router from './router'
import './css/reset.css'
import 'jquery'
import {
  getCookie
} from './common/cookie.js'
import {
  Pagination,
  Table,
  TableColumn
} from 'element-ui'
import VueI18n from 'vue-i18n'
Vue.prototype.$ELEMENT = {
  size: 'small'
}
Vue.use(VueI18n)
Vue.use(Pagination)
Vue.use(Table)
Vue.use(TableColumn)
Vue.config.productionTip = false

function lang () {
  // 将选择的语言存在localStorage中
  let t = window.localStorage.getItem('language')
  if (t) return t
  // 默认中文
  else return 'en'
}

const language = lang()
const i18n = new VueI18n({
  locale: language,
  messages: {
    'zh': require('./common/lang/zh'),
    'en': require('./common/lang/en')
  }
})
window.eventBus = new Vue()
/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: {
    App
  },
  i18n,
  template: '<App/>'
})
