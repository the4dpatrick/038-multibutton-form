038 Multibutton Form
====================

Followed along with Railscast 038 Multibutton Form

[Blog Post](http://patrickperey/railscast-038-multibutton-form) @ [PatrickPerey.com](http://patrickperey.com)

```erb
<% if params[:preview_button] %>
  <div id="preview">
    <h2><%= @project.name %></h2>
    <%= textilize @project.description %>
  </div>
<% end %>
...
<%= submit_tag 'Preview', name: 'preview_button' %>
```

```ruby
def create
...
  respond_to do |format|
    if params[:preview_button] || !@project.save
      format.html { render action: 'new' }
      format.json { render json: @project.errors, status: :unprocessable_entity }
    else
      format.html { redirect_to @project, notice: 'Project was successfully created.' }
      format.json { render action: 'show', status: :created, location: @project }
    end
  end
end
```
