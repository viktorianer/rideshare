# Rideshare

An exemplary Rails 6.0 API app, in iterations

### Iteration 7

Dockerize the application. <https://docs.docker.com/compose/rails/>

* Change the `database.yml` and set the `host: db`
* Install `yarn`

#### Docker Commands

* `docker-compose build`
* `docker-compose up`
* `docker-compose run web bundle exec rake db:create`
* `docker-compose run web bundle exec rake db:migrate`
* `docker-compose run web bundle exec rake data_generators:trips`

Now query for some data:

`curl http://localhost:3000/api/trips?start_location=New%20York&driver_name=Kasie`


### Iteration 6

Add integration and model tests for trip search. Add trip search by multiple dimensions (Driver name, rider name, location).

### Iteration 5

Generate sample Driver, Trip, Rider, and Rating data. Add basic Driver dashboard. Show driver stats.

<img src="https://i.ibb.co/KcgZTBM/driver-dashboard.png" alt="Driver dashboard"/>

### Iteration 4

UML Sequence Diagram of Rider, Driver, Trip Request, Trip, and Rating messages

```
@startuml

title "Rider, Driver, Trip Sequence Diagram"

actor Rider
boundary "TripRequest"
actor Driver
entity Trip

Rider -> Rider : Enters Start and End Location
Rider -> TripRequest : Requests Trip
Driver -> TripRequest : Accepts Trip Request
TripRequest -> Trip : Trip Starts
Trip -> Trip : Trip Ends
Rider -> Trip : Rider Rates Trip

@enduml
```

<img src="https://www.plantuml.com/plantuml/img/PP0v3i8m44NxESKeDLo00WKfT5G95nZi4RAKsC6U8ENsU4C4gBoz__tiDWXvMQOHG8oCZ4rlDFiTTjuyqtZrPiQ17mjRnTWPkdkQ6W1IuZnc66vkiPhyYasY-mG7QIfIYe1jx5zp7K2EuVvOydZ0inNs0OSaWsHrtD1uSOh4EFl1D_KnL6UXb9Px_gcJKZnNw1s1BL8J4IrlJGuX4xz7KIfyooIBlEv9k8f0orR77tq1" alt="Trips Sequence diagram">

### Iteration 3

* Trip model, when a Driver accepts a Trip Request
* Completed Trips can be rated


### Iteration 2

* Location (Geo coordinates) and Trip Request models
* API base controller
* Trip Requests index and create API endpoints


### Iteration 1

* Started with [Design Document](/docs/design_document.md)
  * Writing out use cases
  * Planning models, database tables, constraints, validations
    * Using single-table inheritance for Driver and Rider instances in a Users table
