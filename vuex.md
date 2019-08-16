## VUEX

```
npm install vuex
```

Create `store.js` indside `js` folder

```
import Vue from 'vue'
import Vuex from 'vuex'
import user from './modules/ModuleName'

Vue.use(Vuex)

export default new Vuex.Store({
    modules: {
        ModuleName,
    }
})

```

Inside `app.js`

```
window.Vue = require('vue');
import Router from './router.js'
import store from './store'


const app = new Vue({
    router: Router,
    store,
}).$mount('#app')
```

Create `modules` folder inside `js` folder

Create Modules inside modules folder like this

```
import axios from 'axios'

const state = {
    variableName: value,
};

const getters = {
    getterName: state => state.variableName
};

const actions = {
    async actionName( { commit }, variableName1 ){
        const response = await axios.get('https://jsonplaceholder.typicode.com/todos');
        commit('mutationName', response.data);
    }
};

const mutations = {
    ModuleName: (state, variableName) => {state.variableName = variableName},
}

export default {
    state,
    getters,
    actions,
    mutations
};
```

Add this module into `store.js`