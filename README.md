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

## 3. swiper breakpoint not work in ssr mode slidePerView is just what it is in first load 
  i happen because in server side we dont have window or document to see size . we can init swiper in client side or better way that i find is not using breakpoints . we must set slides-per-view="auto" and add css class for size to swiper-slide \
  ` <swiper-container free-mode="true"
                                      slides-per-view="auto"
                                      space-between="14"
                                      loop="true"
                                      autoplay-delay="3000"
                                      navigation-next-el=".swiper-button-next"
                                      navigation-prev-el=".swiper-button-prev"

                                      class=" p-px">
                        <swiper-slide v-for="(item , index) in productSlider4.items" :key="index" class="w-50" > ` 
  
  

