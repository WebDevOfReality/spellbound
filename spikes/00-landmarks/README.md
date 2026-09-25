# Spike 00: webcam → hand landmarks

**Question:** does the camera → MediaPipe HandLandmarker → normalized landmarks path work in a
browser on our hardware, and how fast is it?

**What it does:**
- Draws the 21 tracked hand landmarks live, and shows the frame rate and which hand is detected.
- Lets you save labeled examples by pressing a letter key.
- Guesses the letter live by comparing the current hand to *your own* saved examples. This is
  "rung 0" from `dossier/05`.
- Saves the examples as JSON. They're useful for normalization tests, and never committed.

## Run it

The camera requires `localhost` or HTTPS. From the repo root:

```bash
npx --yes serve spikes/00-landmarks -l 5173
```

Then open http://localhost:5173 and click **Start camera**.

## Findings

_(Fill in after running.)_
- FPS on w3b-weavr (GPU delegate):
- FPS with the CPU delegate:
- Letters the nearest-neighbour guess confuses, and whether that matches the A/S/T/M/N/E group from
  dossier/02:
- Handedness label correct when mirrored?
