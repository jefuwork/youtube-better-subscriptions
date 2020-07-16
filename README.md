## Difference between v0.13.1.1 (latest [original](https://github.com/OsaSoft/youtube-better-subscriptions)) and v0.14 (this fork).

---

<details>
  <summary>You can expand me to see :framed_picture:</summary>
  down below
</details>

---

## Bugs fixed:

- <details>
    <summary>History for the first loaded videos was incorrect: UI was rendered before we get history from storage (so you won't see any "watched" videos at the beginning)</summary>

  ```
  old
  ```

  ![](https://i.imgur.com/57uLW7d.gif)

  ```
  new
  ```

  ![](https://i.imgur.com/eB2GWcP.gif)
  </details>

  Reason - loading from storage is an async function, so I wrapped it under a Promise object.

- <details>
    <summary>Videos loaded after you scroll down won't be marked as "watched"</summary>
  
  ```
  old
  ```

  ![](https://i.imgur.com/PPQF2hJ.gif)

  ```
  new
  ```

  ![](https://i.imgur.com/5eh4HZ9.gif)
  </details>

  Long story short (if I remember it correctly) the reason for this is that it's trying to change "not watched" button to "watched" one (when you load new videos in "hide watched" mode and then switch the toggle to "show watched" mode) - but "watched" videos weren't given any buttons on initialization.

  _Rebuild logic a bit for it to build UI only when history storage was loaded and create all buttons at the beginning._

  _**Resolves**_: https://github.com/OsaSoft/youtube-better-subscriptions/issues/65

### Minor fixes:

- <details>
    <summary>Fixed .subs-btn-settings SVG repeat (it appears when you hide any label or resize the window)</summary>

  ![](https://i.imgur.com/YZ98fTM.png)
  ![](https://i.imgur.com/SgpCsJ2.png)
  </details>

- <details>
    <summary>SVG icon fix</summary>

  ```
  old
  ```

  ![](https://i.imgur.com/rSwvtbf.png)

  ```
  new
  ```

  ![](https://i.imgur.com/QujXike.png)
  </details>

- <details>
    <summary>Open settings on a new page so you can see confirm dialog for storage clearing. (problem in Chrome)</summary>
  
  ![](https://i.imgur.com/I6LIL6O.gif)
  </details>

  _Personally, I would add this in chrome version and ignore it in firefox._

## What's new:

- <details>
    <summary>Added support for channel videos page, added settings option to enable / disable it</summary>
  
  ![](https://i.imgur.com/eEUbhQG.png)
  </details>

  _**Resolves**_: https://github.com/OsaSoft/youtube-better-subscriptions/issues/59

- Made watched videos semitransparent and show "Mark as Watched" button on video hover only
  _for better visual clarity_
- Deleted hiding videos marked as watched by YouTube, cause I find it kind of unreliable
  _(will add in future if needed)._

### Settings:

- Enable / disable support for channel videos page (channel/\*/vids page). 
- Added option to keep the state of "Hide Watched" checkbox (while you are not reloading the page).
  _It allows you to go on video / channel / sub / etc pages and save the state of "Hide Watched" checkbox despite the default value (it will be applied on reload)._

- Added option to set video watched when you click on it.
- Added option to show / hide Mark all as watched label.
- <details>
    <summary>Added option to stick UI to the right menu.</summary>
  
  ![](https://i.imgur.com/98JibHa.png)
  </details>

  _If you like minimalism or want to make ui more compact._

- <details>
    <summary>Minor page UI improvements.</summary>
  
  ![](https://i.imgur.com/h1V4UNX.png)
  </details>

###### Need to mention that:

- Old layout wasn't tested
- Currently new buttons will be created in "Hide watched" mode
  _Like it was before_

---

# Youtube better subscriptions
This plugin aims to make navigating YouTube's subscription grid easier by allowing users to hide watched videos.
This plugin is in early development and will often change and (hopefully) include new features.

Available for Firefox: https://addons.mozilla.org/cs/firefox/addon/youtube-better-subscriptions/

Available for Chrome: https://chrome.google.com/webstore/detail/better-subscriptions-for/fkchdogohkjpnhfkganifkbbjcjofbjf


The icon for the marked watched Button is based on: https://commons.wikimedia.org/wiki/File:OOjs_UI_icon_eye.svg published under the CC-BY-SA-3.0, the modified version is licensed under CC-BY-SA-4.0

The icon for the settings Button is taken based on: https://commons.wikimedia.org/wiki/File:OOjs_UI_icon_settings.svg published under the MIT licence, , the modified version is licensed under MIT

The addon as a whole is still licensed under the GPLv3
