---
layout: post
title:      "Blow My Mind"
date:       2020-06-22 15:27:58 +0000
permalink:  blow_my_mind
---

My mind is blown and stretched every project and the bits and pieces of brain matter often decorate the screen of my laptop in a never-ending pursuit of knowledge in the paradigm of code. Although this project did not hold me to sleepless nights, self-induced anxiety, and several cups of Starbucks' latte macchiato, it proved challenging in a way that broadened my programming horizon -
Enter Sinatra.

Now I know what you are thinking. Sinatra? Frank Sinatra? Fortunately, this blog is about coding instead of the traditional pop that dominated much of the 20th century! But do not feel embarrassed, my mind made that same initial deduction when I heard the name 'Sinatra'. The brain synapses paved several paths in RESTful route fashion as it traveled tirelessly through the database of my mind before short circuiting amongst the glory that is the DSL web app library used in Ruby.

My project, "Phantom Clothing Store" consisted of creating a simple Sinatra web application that modeled a clothing store. Users were able to hold accounts on the site through creating a signup and login with personal information, collect and view a collection of their inventory, and create their own clothing based on their style and brand. This project helped me to develop a great sense of CRUD functionality, the precision of RESTful routes, and the usage of HTML and CSS when developing a site. I was reminded of the importance of the primordial stages of building any functionable Object model: Classes and Instances. Classes are blueprints from which objects are instantiated and each object of that class is referred to as an instance. What is interesting here is the disparity between the scope of a class and instance. Think of scope as a region of functionality germane to the span of the region’s vision; therefore, the instance of the class can only see the parameters concerning the instance itself not allowing for the scope of class which oversees it.
This was a pivotal concept I heavily relied on when building the Phantom Clothing Store since the routes and methods within the route were inextricably based on the objects of the class. This is exemplified through the following code which utilizes both classes and instance to perform the login functionality:


```
 post '/login' do
        @user = User.find_by(username: params[:username])
        if @user
            session[:user_id] = @user.id
            binding.pry
            redirect "users/#{@user.id}"
        else
            @err = "Invalid Credentials"
            erb :'users/login'
        end
    end
```


The `@user` instance variable is defined as a user object which is contingint on the class method that finds the object by username. The key note is the parameters which denote the instance or class variable on the lines that follow. What would happen if I used the code `User.id` instead of `@user.id`? Well, it would break, specifically due to a NoMethod error. The 'id' method is selfishly within the scope of an instance of the class rather than the class itself. The 'binding.pry' is a testament to my own mistake in confusing the two.

This foundational pillar of distinguishing between classes and instances in Ruby is consequential because the understood logic is necessary to the development of functionable Ruby based applications especially in the context of Sinatra where a database is involved. Iteration, hashes, and CRUD functionality stand atop the mountain that is utilizing class and instance scope. My mind is continually blown by the intricate loop of information as I go from building simple command line interfaces to structured database web applications; however, I know that I will need all my brain matter to triumph the challenging and adventurous journey of the continual learning process that lies ahead.
