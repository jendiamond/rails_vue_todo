# README

+ Ruby version 2.5.1
+ Rails ~> 5.2.1


https://www.udemy.com/ruby-on-rails-react-angular

#### rails g controller Welcome home
+ update config/routes
```
Rails.application.routes.draw do
  root 'welcome#home'
  get 'welcome/home'
end
```

`bundle`

#### yarn add vue
`yarn install`

### Add Vue
#### Create a new file
**`app/javascript/packs/app.js`**
```
import Vue from 'vue';
```

**`app/views/layouts/application.html.erb`**
```html
<!DOCTYPE html>
<html>
  <head>
    <title>RailsVueTodo</title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>

    <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
    <%= javascript_pack_tag 'application' %>
    <%= javascript_pack_tag 'app' %>

  </head>

  <body>
    <%= yield %>
  </body>
</html>
```

### Config Vue
**`config/webpack/custom.js`**
```
import Vue from 'vue';
```

---

#### Create a new Rails app; adding webpack and skipping coffeescript and turbolinks. Then stop the Spring server.
$ `rails new task-manager-app --webpack --skip-coffee --skip-turbolinks
cd task-manager-app`
$ `spring stop`

#### Add a new Controller called Welcome with the action `home`
$ `rails g controller Welcome home`

#### Update the `config/routes.rb` to route the opening page to the home page
```
Rails.application.routes.draw do
  root 'welcome#home'
  get 'welcome/home'
end
```

#### Start the app
`rails server`

Load `localhost:3000` in your browser

#### Add yarn and Vue to the application
$ `yarn add vue`
$ `yarn install`

#### Create a new file
**`app/javascript/packs/app.js`**
```
import Vue from 'vue';
```

#### Update `app/views/layouts/application.html.erb` add
```
<%= javascript_pack_tag 'application' %>
<%= javascript_pack_tag 'app' %>
to the <head>  element
```

#### Create `custom.js` in `config/webpack`
Add this to the file:  
**`config/webpack/custom.js`**
```
module.exports = {
  resolve: {
    alias: {
      vue: 'vue/dist/vue.min.js'
    }
  }
}
```

#### Update `config/webpack/environment.js`
```
const { environment } = require('@rails/webpacker')
const customConfig = require('./custom')
environment.config.merge(customConfig)
module.exports = environment
```
