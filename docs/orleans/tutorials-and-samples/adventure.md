---
title: Adventure game sample project
description: Explore the Adventure sample project written with .NET Orleans.
ms.date: 02/04/2022
---

# Adventure game sample project

This sample is a simple multiplayer text adventure game inspired by old-fashioned, text-based adventure games.

## Instructions

1. Open [_OrleansAdventure.sln_](https://github.com/dotnet/samples/tree/main/orleans/Adventure) in Visual Studio.
2. Start the 'AdventureSetup' project.
3. Once AdventureSetup is running, start the 'AdventureClient' project.
4. You will then be prompted to enter your name on the command line. Enter it and begin the game.

## Overview

The AdventureSetup program reads a game description ("map") from AdventureConfig.txt.

It sets up a series of "rooms" such as a forest, beach, caves, a clearing, and so on. These locations are connected to other rooms to model the places and layout of the game. The sample configuration describes only a handful of locations.

Rooms can contain "things" such as keys, swords, and so on.

The AdventureClient program sets up your player and provides a simple text-based user interface to allow you to play the game.

You can move around rooms and interact with things using a simple command language, saying things such as "go north" or "take brass key".

## Why Orleans?

Orleans allows the game to be described via very simple C# code while allowing it to scale to a massively multiplayer game. For this motivation to be meaningful, the labyrinth of rooms needs to be very large and needs to support a large number of simultaneous players. One value of Orleans is that the service can be designed for growth, the overhead of running it at a small scale is not significant, and you can remain confident that it will scale if the need arises.

## How is it modeled?

Player and Rooms are modeled as grains. These grains allow us to distribute the game with each grain modeling state and functionality.

Things such as keys are modeled as plain old objects&mdash;they are just simple immutable data structures that move around rooms and among players; they don't need to be grains.

## Possible improvements

1. Make the map much, much, bigger
2. Make the brass key unlock something
3. Allow players to message each other
4. Make eating food and drinking water possible and meaningful
