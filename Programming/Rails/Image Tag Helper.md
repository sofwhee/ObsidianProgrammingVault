#Rails #helper
#html_tag

## syntax
```
image_tag("icon")
# => <img src="/assets/icon" />

image_tag("icon.png")
# => <img src="/assets/icon.png" />

image_tag("icon.png", size: "16x10", alt: "Edit Entry")
# => <img src="/assets/icon.png" width="16" height="10" alt="Edit Entry" />

image_tag("/icons/icon.gif", size: "16")
# => <img src="/icons/icon.gif" width="16" height="16" />

image_tag("/icons/icon.gif", height: '32', width: '32')
# => <img height="32" src="/icons/icon.gif" width="32" />

image_tag("/icons/icon.gif", class: "menu_icon")
# => <img class="menu_icon" src="/icons/icon.gif" />

image_tag("/icons/icon.gif", data: { title: 'Rails Application' })
# => <img data-title="Rails Application" src="/icons/icon.gif" />

image_tag("icon.png", srcset: { "icon_2x.png" => "2x", "icon_4x.png" => "4x" })

# => <img src="/assets/icon.png" srcset="/assets/icon_2x.png 2x, /assets/icon_4x.png 4x">

image_tag("pic.jpg", srcset: [["pic_1024.jpg", "1024w"], ["pic_1980.jpg", "1980w"]], sizes: "100vw")

# => <img src="/assets/pic.jpg" srcset="/assets/pic_1024.jpg 1024w, /assets/pic_1980.jpg 1980w" sizes="100vw">
```