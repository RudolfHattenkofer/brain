## Background

[5:57 PM](https://koaware.slack.com/archives/D3JDMSJ5P/p1576169836002200)

I may need help understanding photo uploads/processing if you’re able to sometime soon

￼

[alex](https://app.slack.com/team/U0C4N55NG) [6:02 PM](https://koaware.slack.com/archives/D3JDMSJ5P/p1576170173006300)

```swift
ActiveRecord::RecordNotFound: Couldn’t find Photo with ‘id’=659480
```

This issue^ happens a lot but I can never figure out why. 2) filestack creates a completely random filename for each picture which causes the gallery order to be completely jumbled. Most photographers shoot in the order they want the gallery to be in. Over the summer I tried to build a workaround to reset the file name (

[https://github.com/Koaware/koaware/commit/59ed948a4c0655c18cdcce23507d549e54b682ea](https://github.com/Koaware/koaware/commit/59ed948a4c0655c18cdcce23507d549e54b682ea)

) but IIRC there were some issues so we had to rollback. 3) deleting a photo only hides it from the rearrange area - when you go to the gallery the photo is still there even if it’s processing.

[alex](https://app.slack.com/team/U0C4N55NG)

[6:29 PM](https://koaware.slack.com/archives/D3JDMSJ5P/p1576171773008400)

On the listing 17855 the photographer uploaded photos last night and most processed except for the 5 that threw that error. I deleted those photos via our UI but they remained in the property website gallery and in the database. In the database, they are actually there with the filestack URL. Filestack does have the images but for some reason KoaWare failed to process them.

[https://www.dropbox.com/s/35qy5byzqtiru4k/Screenshot%202019-12-12%2009.27.22.png?dl=0](https://www.dropbox.com/s/35qy5byzqtiru4k/Screenshot%202019-12-12%2009.27.22.png?dl=0)



