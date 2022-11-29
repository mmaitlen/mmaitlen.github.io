---
layout: post
title: "Amazed by output from OpenAI"
date: 2022-11-29 08:00:00 -0800
categories: openai
---
Today I played around with OpenAI for the first time and was blown away with the results.  Not only was I able to generate stats for monsters in a D&D 5e encounter and a supporting storyline, I also generated a joke about a giraffe and a penguin in a church.  But I have to admit I was most impressed with it's current ability to generate code.  My software dev job isn't at risk yet...but I can see a time, very soon, where I won't be doing so much coding...mostly prompting and nudging, pretty exciting, thrilling, and since I'm an optimist, kinda scary...not mostly scary...just kinda...that could change.

Below I included the prompts and output from OpenAI using their Playground.  I kept it raw text to showcase all the AI "goodness".

give me a palette to paint a forest in hex codes in a json doc

[
{
"name": "Forest",
"hex_codes": [
"#006400",
"#556B2F",
"#8FBC8F",
"#2F4F4F",
"#00FF00",
"#228B22",
"#00FA9A",
"#98FB98",
"#A9A9A9",
"#ADFF2F"
]
}
]

display the colors in a flutter widget

ListView.builder(
itemCount: palette.length,
itemBuilder: (context, index) {
return Container(
color: Color(int.parse(palette[index]['hex_codes'], radix: 16)),
height: 50,
);
},
);

write a jekyll blog post with this palette

---

layout: post
title: Forest Palette

---

Today I'm going to share with you a beautiful palette inspired by the colors of a forest. This palette is perfect for creating nature-inspired websites or designs. The colors range from vibrant greens to dark and mysterious shades. Here's the palette in hex codes:

- #006400
- #556B2F
- #8FBC8F
- #2F4F4F
- #00FF00
- #228B22
- #00FA9A
- #98FB98
- #A9A9A9
- #ADFF2F

These colors can be used to create a natural feel with a hint of mystery. Whether it's a website, a design project, or a painting, these colors can bring the beauty of a forest into your work. I hope this palette has inspired you to create something beautiful!
