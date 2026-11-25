# TrustFall

A systems-level policy simulation about scam vulnerability among older adults in Ontario. BET 360 (Designing Transitions and Inclusion) final product, University of Waterloo, by Xiwen (Kevin) Liu.

The player leads Ontario's new Scam Resilience Task Force from 2027 to 2031. Each year they fund measures with a tight budget (they can afford only about half of the 16 measures), public approval raises or cuts next year's budget, and scam trends arrive in a different order every game. Results show up through four intersectional personas. Shallow, popular measures (ads, workshops, a scam-detection app, tougher sentences) fade or barely work; deeper measures (trusted contacts and transfer holds, shared liability, shame-free reporting, paid peer educators, a co-design council) are slower but change the system. The debrief maps the strategy onto the iceberg model, Meadows' leverage points, a Theory of Change, the CMU Transition Design framework and an equity lens.

The model is illustrative, not a forecast. See "About this model" in the in-game debrief.

## Run it

Open `index.html` in any modern browser. It is one self-contained file with no network requests, so it works offline and can be submitted as-is.

## Deploy to Cloud Run (optional)

From this folder, with the `gcloud` CLI signed in to your project:

```bash
gcloud run deploy trustfall \
  --source . \
  --region northamerica-northeast2 \
  --allow-unauthenticated \
  --max-instances 2 \
  --memory 128Mi
```

`--source .` builds the `Dockerfile` (nginx serving `index.html` on port 8080) with Cloud Build. `northamerica-northeast2` is Toronto. Cloud Run scales to zero, so a symposium's worth of traffic should stay within the free tier, and `--max-instances 2` caps the worst case. The first deploy may ask you to enable the Cloud Run, Cloud Build and Artifact Registry APIs.

To take it down after grading:

```bash
gcloud run services delete trustfall --region northamerica-northeast2
```

## Files

- `index.html`: the game (HTML, CSS and JavaScript in one file)
- `Dockerfile`, `nginx.conf`, `.gcloudignore`: Cloud Run container
- `CONTEXT.md`: symposium thread title, context paragraph and APA references
