Repo: [https://github.com/Koaware/koaware-infrastructure/tree/master/main](https://github.com/Koaware/koaware-infrastructure/tree/master/main)

Example:

[https://github.com/Koaware/koaware-infrastructure/compare/bed3e18585204b8e495fb00ee486d060b6892faf...a57d15f13982cec01fcc38131acbdddd28c069fa](https://github.com/Koaware/koaware-infrastructure/compare/bed3e18585204b8e495fb00ee486d060b6892faf...a57d15f13982cec01fcc38131acbdddd28c069fa)

Steps:

- Encode secret: `echo -n` `"secret"` `| base64`
- Find latest build number on Circle CI & manually update the ID at the end of the image parameter. Do this for each development being updated
   - In this example, `09f5303b3` is the ID: `image: us.gcr.io/koaware-prod/koaware-main:worker-09f5303b3`
- Add encoded secret to
   - `main/secret-prod.yml`
   - `main/secret-stage.yml`
- Add secret reference to necessary deployments:
   - `main/deployment-worker.yml`
   - `main/deployment-stage.yml`
   - `main/deployment-prod.yml`
- Apply changed files to relevant clusters
   - Open [https://console.cloud.google.com/kubernetes/list?project=koaware-prod](https://console.cloud.google.com/kubernetes/list?project=koaware-prod)
   - Click “Connect” for relevant cluster
   - Run provided command
   - Run for every changed file:
      - `kubectl apply -f main/changed-file.yml`

To apply the new variable, redeploy all pods



