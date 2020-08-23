---
layout: post
title:      "Models are kind of like Superheroes"
date:       2020-08-23 23:04:58 +0000
permalink:  models_are_kind_of_like_superheroes
---


When I first started Rails, I was super excited! This is the place I wanted to be; carried by the wings of Sinatra and landing softly into the dynamic environment that thrives on Rails magic. The ‘convention over configuration’ aspect left me in complete awe more times than I could count. But project week was upon me and I gathered my necessary materials for success: my laptop with a ubuntu terminal and google tab open, an open table top surface, a bag of cheese-flavored Ritz-Bitz, and ‘RY X & Brussels Philharmonic Soloists Live at AB’ playing on YouTube. 

The purpose of my rails project was to create a CRUD application where users can create and log different types of bikes and trail locations that they have visited. The name of the application is ‘SkyLine Bikes’ and the process wasn’t a beautiful orange horizon where the skyline met the edge of the earth in beautiful harmony; it was more like dark, gray clouds that rolled over with thunderous cries that preceded incessant flash messages of lightning bolts. However, all dark clouds have a silver lining and my silver lining happened to be Models. I know what your thinking, “Models, really?”. Models can be generally eclipsed by the overwhelming might and prevalence of the Controllers and Views in the MVC architectural pattern, but it plays a consequential role to ensure the smooth operation of an application. 

SkyLine Bikes has 3 Models:
•	User
•	Bike
•	Trail

The Model sustains relationships between the object and the database which in simpler terms denotes that the Model is responsible for maintaining the communication between the Controller and the database. Each model symbolizes a database table and is equipped with functions to edit, save, and procure, and delete data from that database through ActiveRecord. ActiveRecord is designed to handle the business logic and the catalyst for performing applications tasks that interact with the database. Consequently, ActiveRecord helps us to build relationships with our objects.
Object relationships can be defined in diverse ways; main types of database association are:
•	one-to-one associations
•	one-to-many associations
•	many-to-many associations

Skyline Bikes relationships are defined by the following:
```
class User < ApplicationRecord
    has_many :bikes
    has_many :trails
    has_many :completed_trails, through: :trails, source: :bike
    has_secure_password

    validates :username, :email, presence: true
    validates :username, :email, uniqueness: true
end
```

```
class Bike < ApplicationRecord
  belongs_to :user
  has_many :trails
  has_many :users, through: :trails
  validates :name, :type, presence: true

end
```

```
class Trail < ApplicationRecord
  belongs_to :user
  belongs_to :bike
  validates :location, presence: true
end

```

Associations are utilized using macros, so that developers can conveniently add methods to their models. For instance, by stating that Bikes belong to users, Rails adds a Primary Key-Foreign Key relationship between the two models with methods that display their relational dynamic.

A belongs_to association sets up a one-to-one connection with another model.
A has_many association conveys a one-to-many connection with another model. This association is coupled with 'belongs_to' by logical discernment. If a bike belongs to a user, a user has one or more bikes.
A has_many :through association is often used to set up a many-to-many connection with another model.

Setting up my associations was relatively easy, I’m just thinking through the logic of the relationship and typing it into my Model, right? Absolutely! The part where I failed at was utilizing the associations in the right manner and then applying those associations syntactically correct in the other areas of my MVC. It was like getting a hammer for Christmas on my 12th birthday and after nailing my hand-drawn portrait of Superman on the wall, going outside to build a house! After failing and failing, I decided to do things the right way and jumped into my rails console to fully grasp the depth of utilizing the relationship.

After practicing and understanding the concept, I could then utilize the logic in my Controllers and Views to produce a result that is pleasing to developers and consumers alike.
```
2.6.1 :001 > User.first.bikes.name
   (0.2ms)  begin transaction
  User Load (0.6ms)  SELECT "users".* FROM "users" ORDER BY "users"."id" ASC LIMIT ?  [["LIMIT", 1]]
 => "Bike"
2.6.1 :002 > Bike.first.trails
  Bike Load (0.3ms)  SELECT "bikes".* FROM "bikes" ORDER BY "bikes"."id" ASC LIMIT ?  [["LIMIT", 1]]
  Trail Load (0.7ms)  SELECT "trails".* FROM "trails" WHERE "trails"."bike_id" = ? LIMIT ?  [["bike_id", 1], ["LIMIT", 11]]
 => #<ActiveRecord::Associations::CollectionProxy [#<Trail id: 1, location: "Chokoleskee Bike Trail", length: 4, rating: 7, user_id: 1, bike_id: 1, created_at: "2020-08-23 00:19:36", updated_at: "2020-08-23 00:19:36">, #<Trail id: 2, location: "Oleta River State Park", length: 12, rating: 9, user_id: 1, bike_id: 1, created_at: "2020-08-23 02:51:37", updated_at: "2020-08-23 02:51:37">]>
```

results:
```
def new
    if params[:user_id] && @user = User.find_by_id(params[:user_id])
      @bike = @user.bikes.build
    else
      @bike = Bike.new
    end
    @bike.build_user
  end
```

Models are awesome and personally my favorite part of the MVC architectural design because they also add validations and authentication through a macro called `has_secure_password` to prevent invalid data from entering the database.
Earlier, I mentioned my twelve-year old portrait of Superman but as I continue to write this blog, I realize something: Models are kind of like Superheroes. They are a fortress from data that threatens to corrupt and a mediator that keeps the peace between Controllers and Views. Though they can be silently working in the background: sustaining object relationships, validating our forms and in many ways, they can masquerade as a journalist for the Daily Planet, while silently and valiantly defending our data! 

Thanks for reading,
Allen Pottinger

