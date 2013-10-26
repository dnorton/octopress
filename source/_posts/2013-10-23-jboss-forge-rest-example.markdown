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

* `forge`
* `new-project --named workout-api --topLevelPackage org.dnorton.workouts`
* `forge install-plugin arquillian`
* `arquillian setup --containerType EMBEDDED --containerName JBOSS_AS_EMBEDDED_6.X`

(this is where I'm stuck for now)

[1]: http://forge.jboss.org/# "JBoss Forge"