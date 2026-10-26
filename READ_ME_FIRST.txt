PARADISE TUNES V7 — FINAL ISOLATED ANALYZER EXPERIMENT
=====================================================
STATUS: PACKAGE PREPARED ONLY. NOT DEPLOYED. NOT LIVE-TESTED.

CAPTAIN: FIRST, only extract this ZIP into its own new folder and send
Charlie a screenshot of the folder contents. Do NOT upload or deploy yet.

WHAT THIS DOES
- Uses the same SHOUTcast audio feed and same 24 V1 frequency-band mapping.
- Derives FFT from 1024-sample windows, moving 512 samples at a time
  (46.44 ms nominal hop, ~21.53 FFT outputs per second IF stream flows).
- Exposes an incrementing FFT frame sequence ID and generation timestamp.
- Reports observed actual FFT generation rate, inter-frame gap, and stream
  connection ID, as well as original raw and faster-smoothed 24-band values.
- The test page displays raw and smoothed results side by side.
- Does NOT connect to the listener's audio element; separate cloud audio
  connections can have different latency and playback buffering.

ARCHITECTURE & SAFETY
- Isolated NEW GitHub repository and NEW Render web service only.
- NEVER push to, redeploy, rename, or overwrite the working V1 service or repo.
- No Bluehost, production Toshiba, backup Toshiba, or website changes.
- ONE Gunicorn worker only (more workers create extra stream connections).
- Render free-tier allowances and capacity must be checked before creating
  a second service; don't assume it will remain free or always-on.
- Deploy requires a server capable of running FFmpeg and Python dependencies.
- This ZIP is source code, not a Windows double-click HTML-only experiment.
- Standalone index.html expects /api/vu on its own V7 server.

AFTER APPROVAL, SEPARATE DEPLOYMENT CHECKLIST (NOT YET AUTHORIZED)
1. Create a NEW repository (suggested: paradise-tunes-v7-isolated-analyzer).
2. Upload app.py, index.html, Dockerfile, requirements.txt, .dockerignore;
   optionally this instruction file. Do not modify V1 repository.
3. On Render, create a NEW Docker Web Service sourced from that NEW repo.
4. Use ONE instance, free tier only if available without billing impact;
   otherwise stop and check with Captain before continuing.
5. Set health check path to /health and automatic deploys OFF.
6. Once live, check /health and /api/vu for consecutive seq increments.
7. Open the V7 root page, collect diagnostic screenshot after 35 seconds.
8. Compare V7 raw and smoothed bars to previous saved V6 captures.

DECISION CRITERIA
- More FFT frames plus smoother response: cloud approach might be viable
  for a visualizer, but audio synchronization remains unproven.
- Fast frames yet unsynchronized with playback: STOP cloud sync effort;
  evaluate listener-playback pipeline or openly decorative alternative.
- Poor delivery or poor analyzer timing: do not endlessly optimize.

NOTES
Sample generation timestamps use server Unix time; comparing them directly
with a phone clock requires clock synchronization. seq counts FFT frames,
not unique musical content. Near-empty music can yield identical bands.
Nominal block rate is a formula, not an observed production guarantee.
