Features
===

Affordances can be tricky things to tie down, in part because they are often difficult to tie to any particular object.  The color of an apple can be tied via predication to the fruit.  In contrast, the affordance of drowning is not so easy to tie to an object - not only do you need a waterbody to drown in, but a victim to submerge.  Moreover, the waterbody needs to have a sufficient depth, and the victim has to be in a position where water intake would be an issue (you can't drown a fish).  All these factors together do not constitute a convenient object of which you'd predicate this affordance of drowning.

Anthony Chemero (2001) argues that affordances need not be considered properties that are predicated of an object.  Following Strawson's (1959) theory of feature-placing sentences, affordance sentences are thought of along the same lines as "It's raining."  Just as the environment surrounding the speaker of "It's raining." is considered to contain the feature of 'enduring rain', the watery environment around a swimmer contains the opportunity to drown.

Looking more closely at the example of drowning, we start with two entities: a kind of animal and a kind of activity:
- actor: the kind of animal that can drown
- event: drowning
The environment of the victim vis-a-vis drowning seems to be determined by combination of the actor and the event of the affordance.  If a person is treading water in the middle of a deep pond, then his environment would clearly afford the opportunity to drown.  Just as clearly, if the closest threatening waterbody is ten miles away, the actor needn't worry about his surroundings (as far as drowning is concerned).

To formally represent an environment that affords the danger of drowning to a particular kind of actor, we start by defining the affordance in terms of the actor and the danger:

```
	(def drownability (affordance Person Drown))
```

Let's say we have a person swimming in the deep end of a pool:

```
	(instance john Person)
	(swimming (actor john) (location deep-end))
```

At this point, we can place the affordance of drowning in John's environment:

```
	(def e (environment (actor john) (event Drown)))
	(has-feature e drownability)
```

The affordance of drownability is thus unlike the color of an apple, which we would have formalized as a predication:

```
	(has-property apple-3 Red)
```

The primary difference lies not in the relation used (i.e. has-feature vs. has-property), but in the signatures.  Whereas predication relates an entity to a property, feature-placement relates an environment (itself a relationship between an actor and a kind of event) and an affordance (a relationship between a kind of actor and a kind of event).

A bit of simplification can take place, as the 'kind of event' is identical in the relationships constituting feature-placement.  Essentially, a feature-placement relates an entity, a kind of entity of which it is an instance, and a kind of event:

```
	(has-feature (actor john) (actor-kind Person) (event Drown))
```

Which can be read: "As a person, John currently has the opportunity to drown."
