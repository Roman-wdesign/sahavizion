## About

### How use emit, props, $event with ts + vue3 + composition api script setup

---

├──📁 src/ # root directory  
│  
├──📁 assets/ # assets directory  
│  
├──📁 components/ # components directory  
│ ├──📄 TheButton.vue/ # child component # <code style="color : aquamarine"> emit</code> event <span style="color:#7375dd"> click</span> to TheModal.vue  
│ ├────📄 TheModal.vue/ # **child** of TheWelcome.vue, but **parent** of TheButton # <span style="color:#e9918c"> emit</span> </span> event <span style="color:#7375dd"> update:isOpen</span> to TheWelcome.vue and watch <span style="color:#e9918c"> props<span style="color:#7375dd"> isOpen</span> </span> and synchronizes local <span style="color:#7375dd"> oModal</span>  
│ └───────📄 TheWelcome.vue/ # parent component # use <span style="color:#e9918c"> reactive</span> <span style="color:#7375dd"> openModal</span>. Use <span style="color:#7375dd"> isOpen </span> as <span style="color:#e9918c"> props</span> to TheModal.vue. Use <span style="color:#7375dd"> update:isOpen</span> to synchronize with TheModal.vue
│  
|   
│  
│  
│  
│  
│  
└──📁 styles/ # styles directory

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run serve
```
