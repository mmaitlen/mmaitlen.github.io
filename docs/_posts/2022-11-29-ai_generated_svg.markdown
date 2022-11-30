---
layout: post
title: "OpenAI can generate SVG images"
date: 2022-11-29 09:00:00 -0800
categories: openai
---
Experimenting with creating SVG images with OpenAI Playground.  Below are prompts to the AI along with the results.

generate svg smiley face radius 100 pixels

<svg width="200" height="200">
  <circle cx="100" cy="100" r="100" fill="yellow" />
  <circle cx="75" cy="75" r="10" fill="black" />
  <circle cx="125" cy="75" r="10" fill="black" />
  <path d="M75 95 q 25 25 50 0" stroke="black" stroke-width="15" fill="none" />
</svg>

draw the mouth lower on the face

<svg width="200" height="200">
  <circle cx="100" cy="100" r="100" fill="yellow" />
  <circle cx="75" cy="75" r="10" fill="black" />
  <circle cx="125" cy="75" r="10" fill="black" />
  <path d="M75 105 q 25 15 50 0" stroke="black" stroke-width="15" fill="none" />
</svg>

make the eyes a blueish green color

<svg width="200" height="200">
  <circle cx="100" cy="100" r="100" fill="yellow" />
  <circle cx="75" cy="75" r="10" fill="#009985" />
  <circle cx="125" cy="75" r="10" fill="#009985" />
  <path d="M75 105 q 25 15 50 0" stroke="black" stroke-width="15" fill="none" />
</svg>

make them smaller

<svg width="200" height="200">
  <circle cx="100" cy="100" r="100" fill="yellow" />
  <circle cx="75" cy="75" r="5" fill="#009985" />
  <circle cx="125" cy="75" r="5" fill="#009985" />
  <path d="M75 105 q 25 15 50 0" stroke="black" stroke-width="15" fill="none" />
</svg>
