# calendar-app
vue.jsにてカレンダー作成
## Project setup
npm install -g @vue/cli

vue create vue-calendar
? Please pick a preset: Manually select features
? Check the features needed for your project:
 (*) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 (*) Router
 (*) Vuex
>(*) CSS Pre-processors
 (*) Linter / Formatter
 (*) Unit Testing
 (*) E2E Testing
 
? Choose a version of Vue.js that you want to start the project with 3.x
? Use history mode for router? (Requires proper server setup for index fallback in production) No
? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default): Sass/SCSS (with dart-sass)
? Pick a linter / formatter config: Prettier
? Pick additional lint features: Lint on save
? Pick a unit testing solution: Jest
? Pick an E2E testing solution: Cypress
? Where do you prefer placing config for Babel, ESLint, etc.? In package.json
? Save this as a preset for future projects? Yes
? Save preset as: vue-calendar

cd vue-calendar
yarn serve

## install FullCalendar
npm install --save @fullcalendar/vue @fullcalendar/core @fullcalendar/daygrid


## install Sass
npm install sass-loader
npm install -g node-sass

## install vue-router
npm install vue-router

##構文チェックツール
yarn run lint --fix