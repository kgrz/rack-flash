# Sinatra Flash

Simple flash hash implementation for Sinatra. My implementation has slightly
different behavior than Rails in that it doesn't delete entries until they used.
I think it's pretty rad, but I'm happy to hear thoughts to the contrary.

## Usage

    class MyApp < Sinatra::Base
      include Sinatra::Flash

      get '/' do
        flash[:greeting] || "No greeting..."
      end

      get '/greeting' do
        flash[:greeting] = params[:q]
        redirect '/'
      end

      run!
    end

Run the app. Nothing on the home page by default. Then go here:

    /greeting?q=it-works!

You'll see the flash message. Hit refresh, it'll be gone. As it should be.