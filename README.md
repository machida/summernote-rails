# Summernote::Rails

To gemify Super Simple WYSIWYG Editor on Bootstrap for Ruby on Rails version 4.0

Website of Summernote, https://github.com/hackerwins/summernote

The version of summernote-rails is matched for the summernote editor.

## Installation

Add the following gems to your application's Gemfile:

    gem 'simple_form', github: 'plataformatec/simple_form', tag: 'v3.0.0.beta1'
    gem 'bootstrap-sass'
    gem 'font-awesome-rails'
    gem 'summernote-rails', github: 'rorlab/summernote-rails'

And then execute:

    $ bundle

## Usage

First of all, the summernote editor works on Bootstrap and so it is assumed that you have already set it up.

In app/assets/javascripts/application.js, you should added the following:

```
//= require summernote.min
```

In app/assets/stylesheets/application.css, you should added the following:

```
*= require font-awesome
*= require summernote
```

For example, if you have a post form, in app/assets/javascripts/posts.js.coffee, you should add the following code:

```
$ ->

  # to set summernote object
  # You should change '#post_content' to your textarea input id
  summer_note = $('#post_content')

  # to call summernote editor
  summer_note.summernote
    # to set options
    height:300  

  # to set code for summernote
  summer_note.code summer_note.val()

  # to get code for summernote
  summer_note.closest('form').submit ->
    # alert $('#post_content').code()[0]
    summer_note.val summer_note.code()[0]
    true
```

In app/views/posts/_form.html.erb, you should add 'summernote' class name to the textarea input as the following:

```
<%= simple_form_for(@post) do |f| %>
  <%= f.error_notification %>

  <div class="form-inputs">
    <%= f.input :title %>
    <%= f.input :content, class:'summernote' %>
  </div>

  <div class="form-actions">
    <%= f.button :submit %>
  </div>
<% end %>
```

That's it. 

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request