---
name: create-adventure-book
description: Turn someone's outdoor adventures into a printed AdvenBook photo book. Use when the user wants a book, album, keepsake or gift of their hikes, treks, trail runs, races, bike rides or bikepacking trips (from Strava, a GPS watch, GPX files, race results or a typed list), or asks what an AdvenBook book costs.
---

# Create an AdvenBook adventure book

AdvenBook prints an A4 landscape book of a person's adventures: a route map and elevation profile for each outing, stats, photos and a short story, shipped free. The AdvenBook connector does the layout. Your job is to gather the right material, write the stories with the user, and hand over the link.

## 1. Find the story of the book

If it isn't clear yet, ask what the book is about: one trip (Tour du Mont-Blanc, GR20, Camino, a bikepacking route), a season (a summer of hikes, a year of trail races) or the road to a big race. A good book tells one adventure the person is proud of, so suggest gathering every stage or outing of it, not a single activity.

## 2. Get the activities

- **Strava** (best: maps and photos come in automatically). Call `connect_strava` and give the user the link. Wait until they say they are connected, then call `list_strava_activities` with the `connection_id`. Help them pick the activities (races are marked `is_race`). Keep each title, date, distance, elevation and duration exactly as Strava gives them, unless the user asks to change them.
- **Another Strava connector already in the conversation**: list the activities with their polyline, pass each polyline unchanged as `gps_polyline` and the activity id as `strava_activity_id`.
- **No Strava**: a typed list, race results, a GPS watch summary or GPX files all work. The user can upload GPX files and photos later on the book link.

Never invent a distance, time, ranking, date or place. Ask, or leave the field empty. A book takes 1 to 50 activities; with more than about 30, help the user keep the most memorable ones.

## 3. Photos and stories: ask once

In one short message, ask for photos (public https links; otherwise they add them on the book link) and a few words about each outing: who they were with, a highlight, the weather, how they felt. Then write each story yourself: 2 to 4 sentences, first person, in the user's language, using only what they told you. For a race, put the official result in `race_result` and suggest adding a photo of the bib.

If they have nothing more to give, don't block: create the book with what you have.

## 4. Format and price

Leave `format` empty unless the user chooses; AdvenBook then picks the right one. If they ask:

- Spiral notebook (`carnet`): 4 to 48 pages, for a weekend or a short trip.
- Softcover (`softcover`): 32 to 250 pages.
- Hardcover (`premium`): 24 to 400 pages, the keepsake.

For any price, call `get_book_price`. Never quote a price from memory or from a web page.

## 5. Create the book and hand it over

Call `create_adventure_book` with a short, personal title (for example "Tour du Mont-Blanc, September 2026"), `language` set to the user's language, `data_source`, `strava_connection_id` if they connected Strava, and one activity per stage or outing, in date order.

Give the user the `claimUrl`. It opens the book right away: they can browse it, change photos, cover and layout, add GPX files, and order it on advenbook.com. Tell them the final price is confirmed at checkout from the exact page count. Never say the book is ordered or paid: it stays a draft until they order it on the website.

If they ask for something you can't do from the conversation (moving photos, map style, cover design), say so and point them to the book link.
