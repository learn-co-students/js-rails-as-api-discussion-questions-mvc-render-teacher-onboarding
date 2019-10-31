# Discussion Questions: MVC and Rails Render

## Objectives

* Recall the MVC pattern from Rails
* Identify what `render` does in a Rails controller
* Implement controller actions that render different types

## MVC Review Questions

Write your best answers to the following questions, then discuss with your group.

1. What is the _Model_ responsible for in MVC?  What about the _Controller_? The _View_?

First and foremost, we must recognize that MVC is a pattern in software design emphasizing a separation of concerns between the software's logic and display. The _Model_ defines the data structure and is responsible for managing data. The _View_ handles the layout and display of information, the UI. The _Controller_ contains control logic and routes commands to the model and view.

2. Now that we are using JavaScript to build Single Page Applications, what changes do we need to make to the division of responsibilities in MVC? What is JavaScript responsible for? What is Rails responsible for?

Now that we are using JavaScript in addition to Ruby on Rails, we need to divide the MVC architecture among our new team. JavaScript will be responsible for the View, while Rails will be responsible for the Model and Controller.

3. What kinds of formats can Rails render? List as many as you can. When you think you've got a full list, check out [Rails Guide on Rendering](https://guides.rubyonrails.org/layouts_and_rendering.html#using-render) to see if you missed any.

`ActionController::Base#render` can render "the default view for a Rails template, or a specific template, or a file, or inline code, or nothing at all. [It] can render text, JSON, or XML. You can specify the content type or HTTP status of the rendered response as well."

4. Check out the other ways of sending data in Rails in the [ActionController::DataStreaming documentation](https://api.rubyonrails.org/v5.2.3/classes/ActionController/DataStreaming.html). Draw out how you would build a file download button.

First, we would need to definite our route, for example, in `routes.rb` we could add the line `get "forms/download_1083bz"`. Second, we would need to define our controller action.

```ruby
  def download_pdf
    send_file(
      "#{Rails.root}/public/1083bz_form.pdf",
      filename: "1083bz_form.pdf",
      type: "application/pdf"
    )
  end
```

Third, we would need to add a link in our view, which could be as simple as `<%= link_to "Download 1038BZ Form", forms_download_1083bz_url %>`.

## Exercise

Check out the rails app in the `rendering` folder. `bundle install` and `rails s` to get things running.

Open `config/routes.rb` and `app/controllers/responses_controller.rb`. Add the `render`, `send_data`, and `send_file` lines to the controller so that all the routes work. Check them all by visiting the urls in the browser.

