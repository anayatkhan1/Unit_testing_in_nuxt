# Setting Up Unit Testing with Vitest in Nuxt 3

<p> The Nuxt auto import mechanism greatly simplifies development ☺️ but it can introduce challenges when it comes to unit testing 🥹. 
However, rather than altering component imports to be explicit, there's a more effective approach to initiate unit testing. 
Below, I'll provide you with a step-by-step guide on how to start unit testing in Nuxt. </p>


### Step 1: Initially, we require certain packages to be installed for the purpose of unit testing.

----------
- Install `vitest` for unit testing
  
 ```js
  npm install -D vitest
  ```
- Install `vitejs plugin` library. 
- Offers support for Vue 3 Single File Components.

 ```js
  npm install -D vitejs/plugin-vue
  ```

#### Create a `vitest.config.ts` configuration file for vitest.

 - In the config file we need to import `defineConfig` also we have to import `vue` from that plugin library.
  
![import](https://github.com/anayatkhan1/oneheadlight/assets/73161735/63317623-993a-4e16-8ce6-84acf20d3df0)

  - Open the `tsconfig.json` file and include the `Vitest global types`.
  
  ```js
  // tsconfig.json
    "compilerOptions": {
        "types": ["vitest/globals"]
    }
```
   #### tsconfig.json
    
  ![tsconfig1](https://github.com/anayatkhan1/oneheadlight/assets/73161735/c63c39f8-0a08-4539-bce4-1b30f96e99cc)
  

#### Create a folder called `test` and place a file named `imports.test.ts` or `imports.spec.ts` inside the folder.

- In this specific file, the Vue `import` statement actaully works for a component.
  
 ![importss](https://github.com/anayatkhan1/oneheadlight/assets/73161735/8de72fc8-03cd-4646-9733-5b56f162f61a)
 
---

https://github.com/anayatkhan1/Unit_testing_in_nuxt/assets/73161735/34e23e83-0262-41fb-9662-d56c8109ed2e

---
> #### **Note**
> > ##### Sometimes, red squiggly lines might appear under this import statement.

  Add a new file named `vue-shims.d.ts` within the root of your project. Then, copy and paste the provided code into the file:
   
  ```js
  //vue-shims.d.ts
  declare module '*.vue' {
    import { defineComp } from 'vue'
    const component: ReturnType<typeof defineComponent>
    export default component
  }
  ```

### Step 2: Install unplugin-auto-import 
  
 ```js
 npm i -D unplugin-auto-import
```

#### Automatically, the `auto-imports.d.ts` file is created within your project's root directory. 

---

https://github.com/anayatkhan1/Unit_testing_in_nuxt/assets/73161735/8b79ff1f-3dc6-48ea-aace-ee674aaab0b8

---
> #### **Note**
> > ##### Sometimes, the `auto-imports.d.ts` file is not generated automatically.
> > > In this scenario, we need to generate the file manually.
> > > - Go to the `.nuxt` folder in the root of your project's main folder
> > > - Find `imports.d.ts` file and then copy the entire modules
> > > - Create a `auto-imports.d.ts` file and paste it.

Thats it !

### Congratulations, you are now ready to start unit testing in Nuxt 3 ☺️
