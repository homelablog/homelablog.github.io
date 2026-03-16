---
layout: post
title:  "Smart lights or smart switches? Why not both?"
categories: [ smart home, lighting ]
image: assets/images/light-vs-switch.png
tags: [ featured ]
lang: en
---

In the last years I experimented with smart lighting in my home. My setup currently includes Nanoleaf smart lights, a few Shelly 1 relays, and Home Assistant acting as the central brain of the system.

When I renovated the house I decided to adopt KNX for part of the infrastructure, but I did not initially apply it to lighting. Like many people experimenting with smart homes, I started with smart bulbs.

And they are great.

But they also come with a very obvious problem.

Because smart bulbs are great until someone presses the wall switch.

## The problem with smart bulbs

Smart bulbs enable things that traditional lighting simply cannot do.

Scenes. 
Colors. 
Dynamic lighting.
Automations.

Everything works nicely until someone presses that physical switch.

The moment power is cut, the bulb becomes just a normal light again. Even worse, it disappears from the smart home system.

No automations.
No remote control. 
No scenes.

Just a light that is off.

This is something many people discover only after installing smart bulbs around the house.

At that point the entire smart layer stops working.

## The obvious alternative: smart switches

A common reaction is to move the intelligence away from the bulb and into the switch.
I felt this and I moved this way myself.

Smart relays or smart switches control the power line and allow traditional bulbs to remain in place.

This solves one major issue: the physical switch always works.

But it also comes with a trade-off.

With traditional bulbs you lose most of the interesting capabilities of smart lighting. Those colors, scenes, and automations.

So the dilemma becomes:

- smart bulbs, but fragile when someone uses the switch;  
- smart switches, but way less capable lighting (especially after the initial investment).

For a while I seriously considered removing the smart bulbs entirely and moving to smart switches only.

Then I discovered a third option.

## Turning switches into event generators

My setup includes a few Shelly 1 relays installed behind physical switches.

After updating them, I realized they support a mode called Detached Switch.

In this mode the relay no longer cuts power to the light. Instead it simply detects the physical click.

So: the switch press becomes an event and the light remains powered all the time.

## How the system works

In my case the flow looks roughly like this:

The bulbs remain constantly powered.

To keep Home Assistant aware of the actual light status, Apple Home shortcuts send webhooks back to Home Assistant whenever the light changes state.

Home Assistant tracks the current state of the lights and decides whether the next button press should turn them on or off.

The physical switch becomes a simple input device.

## Smart bulbs and smart switches together

Let's use them together!

Yes, because: smart bulbs provide capabilities and smart switches provide reliable physical interaction.

It is then the automation system that coordinates everything.

## The downside

There is a trade-off, of course.

Home Assistant becomes an important part of the system.

If the automation system goes down, the switches still generate events but nothing processes them. The physical switch will no longer turn the light on or off.

This is something to keep in mind when designing the system, and some form of fallback logic would probably be useful.

## A note on Matter and newer devices

My current lights support **Thread but not Matter**, so the setup described here requires a few workarounds like webhooks and shortcuts.

Newer devices supporting Matter may simplify some parts of this setup.

But the core idea remains the same.

Switches should not cut power to smart lights.  
They should generate events.

## Final thought

Smart lighting often starts with a simple question: smart bulbs or smart switches?

In practice the most interesting setups combine the two.

Keep the bulbs powered.  
Use the switches as inputs.  
Let the automation system decide what should happen.