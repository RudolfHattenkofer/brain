## 2021-04-22

- Where are places in the code where we do uploading?

Storage providers:

- Amazon, Google, Filestack

Places:

- Actual listing [here](https://clients.remarkvisions.com/listings/18936/folders)or [here](https://clients.remarkvisions.com/scheduler/file_upload/new?slug=107f76eb-11da-4066-9f8e-fb4f41bccf89) -> Appears several places, but same component
   - Portfolio [here](https://clients.remarkvisions.com/scheduler/account_settings/portfolio/new)
   - Profile picture [here](https://clients.remarkvisions.com/scheduler/account_settings/photo/new)
- Old dashboard, only superadmins [here](https://clients.remarkvisions.com/listings/18936/folders)
   - Profile old [herel](https://clients.remarkvisions.com/users/edit)
   - Services picture [here](https://clients.remarkvisions.com/services/30/edit)

Two flows: Filestack and legacy

Example:

Video ID = 4622

direct_upload_url = [https://cdn.filestackcontent.com/J2mqMlwGSFWr2nNumafc](https://cdn.filestackcontent.com/J2mqMlwGSFWr2nNumafc)

Listing = [https://clients.remarkvisions.com/listings/22283/folders](https://clients.remarkvisions.com/listings/22283/folders)

Video download = [https://storage.googleapis.com/koaware-main-prod/videos/4622-original.mp4](https://storage.googleapis.com/koaware-main-prod/videos/4622-original.mp4)

\-> Everything is copied over!

Next step:

`videos` where `file_processing` is false, find all Filestack

\-> Delete

```other
source .env
rails c
> reload!;FilestackApi.get_metadata("J2mqMlwGSFWr2nNumafc")
> reload!;FilestackApi.delete_all_videos
```

## Rough outline

[File API](https://www.filestack.com/docs/api/file/)

Filestack has portoflio and “other” videos

- Step 1: Delete everything after it’s been uploaded, see File API and `VideoProcessorWorker` and `PhotoProcessorWorker`
- Step 2: Find all videos that were uploaded initially to Filestack and then copied to GCS
   - Find list of all portfolio videos
   - List all Filestack videos through API
   - → Keep portfolio, delete all others
- Step 3: Figure out what to do about Portfolio

Storage:

- Upload any type of file
- Storage cost in the future?



