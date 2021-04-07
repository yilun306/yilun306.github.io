---
weight: 1
# [str] Title of the project. This is also visible when hovering over a gallery item.
title: "Stock Ticker"
# [str] Optional subtitle of the project. 
#   Functions as an additional explanation when hovering over a gallery item (comment out the following line).
# subtitle: ""
# [date] Project publication date.
#   Changes order: The newest item will be displayed first in the gallery. 
#   Just like Hugo's natural ordering, this is anti-chronological.
#   You can use 'weight' to order (primarily) for more control (sometimes it makes sense to put old items before new ones).
#   The specifics are documented here: https://gohugo.io/templates/lists/#order-content
date: "2021-03-16T19:25:59-04:00"
# [str] Gallery image file. 
#   If the specified image is found in the 'assets' directory  the image will be normalized to a specified height. 
#   If ommited AND type is 'github' (see below), will attempt to fetch from '{repo_url}/.github/logo.png'. 
image: "images/stock_ticker.png"
# [str] Alternatively, you can specify an absolute image URL (comment out the following line).
# imageUrl: ""
# [str] Alternative (image) description.
#   If ommited with type 'github', will use 'description' field from GitHub API.
alt: ""
# [css] Background color of the gallery item.
color: "#C0C0C0"
# [enum] Possible types:
#   - normal: Just as in the original Osprey theme
#   - github: Fetch repo data using GitHub API
type: "github"
# [str] Link to view the project.
linkView: ""
# [str] Link to show the project's code.
#   If ommited with type 'github', will use 'html_url' field from GitHub API.
linkCode: ""
# [map] Configure 'github'-type specific options here:
github: 
    # [str] Repo is a combination of "{user_or_org}/{repository_name}", e.g. "kdevo/osprey-delight.
    repo: "yilun306/Stock_ticker_app"
    # [bool] Show repository information such project language below the buttons.
    showInfo: true
# [map] Configure optional terminal to be displayed when opening up the gallery item:
terminal:
    lines:
    # - type: input
    #   data: docker pull yilun306/financial_portfolio_calculator:latest
    #   wait: 300
    - type: input
      data: docker run -it yilun306/financial_portfolio_calculator:latest
      wait: 300
    - type: progress
      data: 100
      wait: 1000
    - data: � Diamond Hands!
      wait: 900
    - type: input
      data: exit
      wait: 500
draft: false
---

# (Available in Docker Container)