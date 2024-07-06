# help-in-laravel-inertia-vuejs
problem and answer for some problem in handling a website with inertia + laravel + vuejs and have ssr


## 1. problem with ziggy in ssr mode route not defined :
  this problem happen because in ssr mode route() in app.balde.php not accessible. when run 'php artisan inertia:start-ssr' \
  [ziggy github link](https://github.com/tighten/ziggy?tab=readme-ov-file#vue) \ 
  what to do : \ 
  use alternative way instead of use route that make in blade \
  we generate a route file named ziggy.js using command `php artisan ziggy:generate` \
  add `app.use(ZiggyVue, Ziggy);` and `app.config.globalProperties.$route = route in createSSRApp()` function in ssr.js \
  that they imported from 
  `import {ZiggyVue} from 'ziggy-js';
  import {Ziggy} from "./ziggy";`

  in every component that we want to use route \
`import { inject } from 'vue'
const route = inject('route')`

  after that use it \
  **important** : you must regenerate ziggy.js after change in routes \

  
## 2. error onMount funciton in ssr 
  must use beforeMount()
  
  

