# Databases Pt. 1

## Agenda

1. Learning Objectives
1. Databases using Mongoose (20 Minutes)
1. Activity: Create an Events app (30 Minutes)
1. BREAK (10 Minutes)
1. Activity: Tutorial Time (50 Minutes)
1. Resources & Credits

## Learning Objectives

By the end of this class, students will be able to...

1. Use Mongoose models to represent data using a variety of types.
1. Use the `find`, `findOne`, etc. functions to query Mongoose objects.
1. Practice writing routes to return database objects.

## Databases using Mongoose (20 Minutes)

In this class, we will be using [Mongoose](https://mongoosejs.com/docs/models.html) models to represent our data.

Let's take a look at the syntax for creating models.

```js
const mongoose = require('mongoose')

var eventSchema = new mongoose.Schema({
    eventName: {type: 'string', required: true},
    dateTime: {type: 'Date', required: true},
})
var Event = mongoose.model('Event', eventSchema)
```

We can create a new Event object as follows:

```js
const myEvent = new Event({
    eventName: 'Make School Demo Night',
    dateTime: new Date(2020, 2, 6, 18, 30, 0) // March 6, 2020 at 6:30PM
})

myEvent.save() // Save to our Mongoose database
```

Filtering our models results in a `Promise` object which we will need to resolve:

```js
Event.findOne({ eventName: 'Make School Demo Night' })
.then(demoNightEvent => {
    console.log(demoNightEvent)
})
```

We can also update an existing model object:

```js
Event.findOneAndUpdate(
    { eventName: 'Make School Demo Night' }, // How to find the event
    {dateTime: new Date(2020, 6, 6, 18, 30, 0)} // What to change
)
.then(demoNightEvent => {
    console.log(demoNightEvent)
}
```

Or delete it:

```js
Event.findOneAndDelete({ eventName: 'Make School Demo Night' })
.then(result => {
    console.log('Successfully deleted.')
})
```

## BREAK (10 minutes)

## Create a Messages API (30 Minutes)

Clone the [starter code](https://github.com/tech-at-du/messages-api-starter) to get started with this activity. Follow the instructions in the repo. Feel free to use the dataset you defined in class today instead of `Message` or `User`.

## Homework

Use any remaining time to get caught up on the Reddit.js tutorial (or keep going, if you have already finished Part 3). Your instructor will come around to assist!

<!-- In the last 20 minutes, go over the tutorial Parts 1-3 as a class and discuss. -->

<!-- ## Wrap-Up -->

<!-- Fill out our [Vibe Check form](https://make.sc/bew1.3-vibe-check) with any feedback you have for the class. -->

## Resources & Credits

1. [Mongoose Models](https://mongoosejs.com/docs/models.html)
1. [Mongoose Queries](https://mongoosejs.com/docs/queries.html)
1. [Mongoose: Working with Dates](https://mongoosejs.com/docs/tutorials/dates.html)
1. [JavaScript Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
1. [Moment.js](https://momentjs.com/)
