# AdvenBook

Turn your outdoor adventures into a printed photo book: hikes, treks, trail runs, races, bike rides and bikepacking trips. Each outing gets a map of its route, an elevation profile, its stats, your photos and a short story. Books are A4 landscape, in hardcover, softcover or spiral notebook, printed and shipped for free.

## Use it

Ask the assistant something like:

- "Make a photo book of my Tour du Mont-Blanc with my Strava activities"
- "Turn my trail race season into a hardcover book"
- "How much does an AdvenBook cost?"

The assistant helps you pick the activities (from Strava, GPX files, race results or a list you type), asks once for photos and a few words about each outing, writes the stories with you, then creates a draft book. You get a private link to browse and edit the book, and you order it on advenbook.com when you're happy with it.

## What's inside

- **Skill `create-adventure-book`**: the workflow the assistant follows to build a good book.
- **AdvenBook connector**: `https://www.advenbook.com/api/mcp`, with the tools `connect_strava`, `list_strava_activities`, `get_book_price` and `create_adventure_book`.

## Data

To create a book, the assistant sends AdvenBook the activities you chose: titles, dates, distances, elevation, GPS tracks, photo links and stories. Connecting Strava is optional and happens on advenbook.com. Nothing is ordered or paid until you order on the website.

- Privacy policy: https://www.advenbook.com/en/privacy-policy
- Terms: https://www.advenbook.com/en/terms-of-service
- Contact: contact@advenbook.com
