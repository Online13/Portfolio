---
title: Chess in React
slug: chess-in-react
description: Showcasing my chess game implementation in React.
date: 2026-06-23T04:06:50.471Z
---

When I started this project, my goal was not just to build a chess board that works. I wanted to create something **clean**, **reusable**, and **easy to grow over time**. Chess is a good exercise for that kind of architecture: the UI needs to stay simple, but the game logic can quickly become complex.

This project is my attempt to build a chess game in React and TypeScript with a structure that stays understandable as the codebase grows. In this article, I want to share how I approached the component structure, how I organized the game logic, and the ideas behind the architecture choices.

## Why I built it this way

I did not want everything mixed together in one place. A chess app can easily become difficult to maintain if the board rendering, interaction logic, game rules, and UI state are all tightly coupled.

So from the beginning, I tried to separate responsibilities as much as possible:

- the `presentation` layer should only focus on displaying and interacting with the board
- the `domain` layer should contain the rules of the game
- the `application` layer should orchestrate actions like selecting a piece or choosing a target square
- the state layer should store the current game state in a predictable way

That separation made the project easier to reason about, and it also made it easier to imagine supporting other chess variants later.

## How I think about interaction in React

For me, the best way to understand the interface was to start from the player’s point of view.

The interaction is very simple:

- The player clicks on a piece.
- The possible paths appear.
- The player clicks on one of those paths.
- The selected piece moves to that square.

Once I looked at the app this way, the structure became much clearer. I realized the board could be split into three visual layers:

- a layer that lists the squares, only as the background of the board
- a layer that lists the pieces, which are clickable
- a layer that shows the possible paths, which only appears after a piece is selected and can also be clicked
This way of thinking helped me avoid mixing everything into a single component. Each layer has a different role, and each role maps to a different part of the interaction.
