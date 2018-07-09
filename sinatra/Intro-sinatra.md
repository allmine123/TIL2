# Intro-sinatra

- `mkdir sinatra-test`
- `cd sinatra-test`
- `touch app.rb`
- `gem install sinatra`

- ```ruby
  require 'sinatra'
  
  get '/' do
    'Hello world!'
  end
  ```

- `ruby app.rb -o $IP` : -o ip랑 port 바인딩