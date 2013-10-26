---
layout: post
title: "JBoss Forge REST Example"
date: 2013-10-23 21:06
comments: true
categories: 
---
JBoss Forge REST Sample
-----------------------

This is an ongoing blog post. I'm going to attempt to build a sample REST API after setting up the project using [JBoss Forge][1]

The app will simply expose a REST API to post workout data. It will use Hibernate to talk to an in-memory database.

Entities:
	User
	Workout

## Steps (so far)

These steps are modified from [the JBoss Forge Samples](http://forge.jboss.org/docs/using/samples.html).

Start the New Project

* `forge`
* `new-project --named workout-api --topLevelPackage org.dnorton.workouts`

Set up [Arquillian][2] tests

* `forge install-plugin arquillian`
* `arquillian setup --containerType EMBEDDED --containerName JBOSS_AS_EMBEDDED_6.X`

Determine the JPA persistence framework

* `persistence setup --provider HIBERNATE --container JBOSS_AS7`

Next, we need to decide what we want in the entities. I'm not implementing authentication just yet, so lets create a dead simple `User`.

* `entity --named User`
* `field string --name name`

The Workout is slightly more complex. We need to record a title, distance, time, description, and type. Plus, we need to create a relationship with User (a Workout belongs to a single User.)

* `entity --named Workout`
* `field string --named title`
* `field long --named distance`
* `field long --named duration`
* `field string --named description`

Since the `manyToOne` relationship is User -> * Workouts, we need to switch back to `User` and add the relationship.

* `entity --name User`
* `field manyToOne --named workouts --fieldType com.coachcaleb.model.Workout.java --inverseFieldName user`



(this is where I'm stuck for now)

[1]: http://forge.jboss.org/# "JBoss Forge"
[2]: http://arquillian.org/ "Arquillian"