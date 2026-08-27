---
title: "ICHL25 Conference Website"
description: "Conference Programme and digital resource platform for a multi-track, 400 participant conference."

weight: 60

project_type: Research software platform
users: academics
timeline: 2022

technologies:
  - React
  - JavaScript (ES6+)
  - HTML5
  - CSS3

github: http://github.com/RowanLS/ichl25
website:
paper:

---
## The Problem

In 2022, I co-organised the *International Conference for Historical Linguistics 25* at Oxford University. This is a major biennial conference for historical linguistics researchers from around the world. We needed a website where we could host all the information required for the conference as we planned this to be a paper free conference.

## The Solution: ICHL25 Website

I developed the web platform for the 25th International Conference on Historical Linguistics, supporting the programme and digital conference materials for a large, multi-track international academic conference.

Rather than maintaining the programme as a collection of static pages, I modelled talks, posters, workshops, sessions, rooms and authors as structured data and built the interface around that data. The React application used reusable components to generate the multi-day timetable and dynamically link programme entries to individual presentation pages, abstracts, handouts and other resources.

The site combined the public conference website with a navigable digital programme and archive. Parameterised routing allowed presentation pages to be generated from the underlying conference dataset, while conditional rendering handled the different resources available for talks, workshops and other presentation types.

## Engineering Highlights

|Purpose| Notes|
|---|---|
| Frontend Architecture | Built a component-based React single-page application with React Router. |
| Data Modelling | Designed a structured content model for a complex multi-day, multi-track conference programme. |
| Data-Driven Rendering | Generated programme views from a common dataset rather than duplicating content across pages. |
| Dynamic Routing | Connected timetable entries with presentation metadata, abstracts and handouts using dynamic routes. |
| Document Integration | Integrated and embedded conference documents, including PDF abstracts and presentation materials. |
| Production Delivery | Developed and deployed the site as a production service supporting conference organisers, speakers and attendees. |


## Learning Points

The project was built to serve a real international conference and gave me experience translating a complex academic information structure into a maintainable, data-driven interface. Looking back, I would now separate the content model more cleanly from the frontend, introduce schema validation and TypeScript, and strengthen automated and accessibility testing. The core architectural approach—structured data as the source of truth, with the interface derived from it—is one I would retain.