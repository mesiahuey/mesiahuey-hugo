## Installation
1. Clone down this repo
1. `cd` into the directory and run `chmod +x ./deploy.sh`
1. Install hugo see: [https://gohugo.io/overview/installing/](https://gohugo.io/overview/installing/)

## Important Files
- Main pages
	- /layouts/index.html
	- /content/bio.html
	- /content/contact.html
	- /content/links.html
- Layouts
	- /themes/mesiahuey/layouts/partials/header.html: Included at the top of every
		page. Has the opening `html` and `body` tags. Includes common css and javascript 
		files.
	- /themes/mesiahuey/layouts/partials/footer.html: Included at the bottom of every 
		page. Has the closing `html` and `body` tags.
	- /layouts/section/portfolio.html: Handles the main portfolio page that displays
		all of the portfolios.
	- /layouts/portfolio/single.html: Handles each individual portfolio page.
- CSS
	- /static/css/bio.css
	- /static/css/contact.css
	- /static/css/home.css
	- /static/css/links.css
	- /static/css/portfolio.css
	- /themes/mesiahuey/static/css/main.css: The common css that's included on all pages
- JavaScript
	- /static/js/protfolio.js: The JavaScript file for the individual portfolio page. 
		Has the code that allows you to switch between images.
- Images
	- /static/images/portfolios: Contains all of the portfolio images. Each set of 
		portfolio images gets its own folder (i.e. /static/images/portfolios/illustrations)
	- /themes/mesiahuey/static/images: Common images across the site, including the 
		main background image, leaves, etc.
	- /static/images/chefsamplep3.jpg: This is currently being used as the homepage 
		featured image, but it's not required to have this name. See /layouts/index.html

## Adding A Portfolio
The following are the steps to add a new portfolio. Replace `PORTFOLIO_NAME` with 
the name of the new portfolio.
1. Create a new folder: `/static/images/portfolios/PORTFOLIO_NAME`
1. Create a new file in content/portfolio by running `hugo create PORTFOLIO_NAME.html`
1. Fill out the variables described in [Portfolio Variables](#portfolio-variables)

## Portfolio Variables
The portfolio files, like `/content/portfolio/illustrations.html`, have a top section 
(the part surrounded by `+++`). It looks like this:
```
+++
date = "2016-04-24T22:09:56-06:00"
title = "Illustrations"
weight = 3
cover = "/images/portfolios/illustrations/cat.jpg"
images = [
	'/images/portfolios/illustrations/bird.jpg',
	'/images/portfolios/illustrations/cat.jpg',
	'/images/portfolios/illustrations/littlechef3.jpg',
	'/images/portfolios/illustrations/sneaky1.jpg',
	'/images/portfolios/illustrations/sneaky2.jpg',
	'/images/portfolios/illustrations/sneaky3.jpg',
	'/images/portfolios/illustrations/sneaky4.jpg'
]
+++
```
The following is a description of each one, what to set it to, and how it's used:
- `date`: The date the portfolio was created. This gets set when you run 
	`hugo create PORTFOLIO_NAME.html`. You shouldn't have to worry about it.
- `title`: The title of the portfolio. It gets displayed on the main portfolio page, 
	where it lists out each portfolio (/layouts/section/portfolio.html)
- `weight`: The weight of the portfolio. This determines what order it appears on the
	main portfolio page (the lower the number, the earlier it will appear).
- `cover`: The cover image for the portfolio. This is the image that is used on the
	main portfolio page.
- `images`: The list of images in the portfolio. This list is used to create the 
	scrollable list of images a user can cycle through. (See /layouts/portfolio/single.html)

## Testing Changes
After making changes, do the following to check them out:
1. Run `hugo serve`
1. Go to `http://localhost:1313` in your browser

## Deploying Changes
When you're all done making changes, do the following:
1. Commit and push all your changes:
	1. `git add .`
	1. `git commit -am "YOUR COMMIT MESSAGE HERE"`
1. Run `./deploy.sh`