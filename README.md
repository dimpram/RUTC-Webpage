# RUTC-Webpage [wip]
Development/testing repository for upcoming Rock Under The Clock Festival webpage

# All of the following are rough notes that will later turn into theme docs

## Theme usage
1. Setup categories in the navigation.yaml in the order you want each category to be shown.
2. Determine the presentation type of each category in the home page and import the necessary include from `_includes` to index.page
3. Setup cards and pages with proper front matter

## Site Structure
```
Home Page ~> [home]
 ├── News
 │    └── Post List
 │         └── Individual Post
 ├── Past Festivals
 │    └── Events List
 │         └── Individual Event
 ├── Past Street Events
 │    └── Events List
 │         └── Individual Event
 ├── Workshops
 │    └── Events List
 │         └── Individual Event
 ├── Volunteers
 │    └── Individual Page
 ├── Venues
 │    └── Venues List
 │         └── Individual Page
 ├── About Us
 │    └── Individual Page
 ├── Bands
 │    └── Band List
 │         └── Individual Band
 ├── Sponsors
 │    ├── Sponsor List
 │    └── Donate Button
 ├── Media
 │    ├── Videos
 │    │    └── embeded / Youtube Channel
 │    └── Photos
 │         └── Photo Gallery
 └── Contact
     └── Contact page
```

## Layout inheritance and descriptions
```
- default
   ├── home
   ├── standard
   |    ├── list
   |    └── post
   └── 404
```

### Home layout
The point of the home layout is to be a scrolling page. This means that every option on the navigation bar can also be accessed by scrolling to the corresponding heading. The home layout contains the "Splash" and the "Feed" includes by default but it can support up to 5 total categories. If there needs to be more than 5 categories, those extra categories get their own page. The "home" layout is the only layout that uses the **home.css**. All the other layouts will include at least the **default.css**.


## CSS structure
```
```

## Includes
### carousel.html
```
- Include parameters:
      position: Which item in the navigation.yml (in this case) is going to be used/represented.
```
The `carousel.html` include is a wrapper for the `card.html` include.

### card.html

```
- Include parameters:
      cover: Cover image of a card.
      title: Title of the card.
      desscription: Description of a card.
      url: Url of the page that the user will be redirected to.
```

*The title of the section that a card is being displayed should match with the `card_category` because that's
how the placement of the card is being determined, otherwise it will not work*

The `card.html` include is used for displaying cards in the `carousel.html` include. Each card represents a page that you can navigate to (only from the card). It is also automatically generated from the frontmatter variables of the page you want to redirect to. These are: [card_category, card_cover, card_title, card_description ]


## New stuff

Image galleries are handled as folders with static files. See more here: https://mademistakes.com/notes/static-files/

Added gallery include that serves the purpose of serving static file galleries and nothing else. `carousel.html` != `gallery.html`
Gallery include takes as a parameter the category front matter attribute which is the page.url and generates the gallery folder path. For example volunteers page volunteers.html will have a `/volunteers/ ` page url. So the gallery url will be `assets/img{{ pages.url }}`.