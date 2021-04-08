---
# [str] Title of the project. This is also visible when hovering over a gallery item.
title: "Monocular Visual Odometry on Blimp Platform"
# [str] Optional subtitle of the project. 
#   Functions as an additional explanation when hovering over a gallery item (comment out the following line).
# subtitle: ""
# [date] Project publication date.
#   Changes order: The newest item will be displayed first in the gallery. 
#   Just like Hugo's natural ordering, this is anti-chronological.
#   You can use 'weight' to order (primarily) for more control (sometimes it makes sense to put old items before new ones).
#   The specifics are documented here: https://gohugo.io/templates/lists/#order-content
date: "2021-04-07T20:50:19-04:00"
# [str] Gallery image file. 
#   If the specified image is found in the 'assets' directory  the image will be normalized to a specified height. 
#   If ommited AND type is 'github' (see below), will attempt to fetch from '{repo_url}/.github/logo.png'. 
image: "images/Blimp.png"
# [str] Alternatively, you can specify an absolute image URL (comment out the following line).
# imageUrl: ""
# [str] Alternative (image) description.
#   If ommited with type 'github', will use 'description' field from GitHub API.
alt: ""
# [css] Background color of the gallery item.
color: "#303030"
# [enum] Possible types:
#   - normal: Just as in the original Osprey theme
#   - github: Fetch repo data using GitHub API
type: "normal"
# [str] Link to view the project.
linkView: "http://ece4012y202002.ece.gatech.edu/sd20p37/#home"
# [str] Link to show the project's code.
#   If ommited with type 'github', will use 'html_url' field from GitHub API.
linkCode: ""
# [map] Configure 'github'-type specific options here:
github: 
    # [str] Repo is a combination of "{user_or_org}/{repository_name}", e.g. "kdevo/osprey-delight.
    repo: "YOUR-GITHUB-NAME/Monocular-Visual-Odometry-on-Blimp-Platform"
    # [bool] Show repository information such project language below the buttons.
    showInfo: true
# [map] Configure optional terminal to be displayed when opening up the gallery item:
terminal:
    # lines:
    # - type: input
    #   data: ls -ltra dummy/
    #   wait: 1250
    # - type: progress
    #   data: 100
    #   wait: 200
    # - data: ls: cannot access 'dummy/' directory.
    #   wait: 75
# [bool] Draft mode will decide if file will be published to 'public/' directory.
draft: false
---
