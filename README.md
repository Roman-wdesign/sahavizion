## About

### How use emit, props, $event with ts + vue3 + composition api script setup

---

├──📁 src/ # root directory  
│  
├──📁 assets/ # assets directory  
│  
├──📁 components/ # components directory  
│ ├──📄 TheButton.vue/ # child component # $\textcolor{#e9918c}{\textsf{emit}}$ event $\textcolor{#7375dd}{\textsf{click}}$ to TheModal.vue  
│ ├────📄 TheModal.vue/ # **child** of TheWelcome.vue, but **parent** of TheButton # $\textcolor{#e9918c}{\textsf{emit}}$ event $\textcolor{#7375dd}{\textsf{update:isOpen}}$ to TheWelcome.vue and watch $\textcolor{#e9918c}{\textsf{props}}$ $\textcolor{#7375dd}{\textsf{isOpen}}$ and synchronizes local $\textcolor{#7375dd}{\textsf{oModal}}$  
│ └───────📄 TheWelcome.vue/ # parent component # use $\textcolor{#e9918c}{\textsf{reactive}}$ $\textcolor{#7375dd}{\textsf{openModal}}$. Use $\textcolor{#7375dd}{\textsf{isOpen}}$ as $\textcolor{#e9918c}{\textsf{props}}$ to TheModal.vue. Use $\textcolor{#7375dd}{\textsf{update:isOpen}}$ to synchronize with TheModal.vue

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
