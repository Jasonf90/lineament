# How Lineament rates a scan

**Published:** 30 October 2026 · **Applies to:** Lineament for iPhone, version 1, rubric 3.0.0

Lineament gives you an **appearance rating**: a Lineament estimate of how one scan lines up with Lineament's own internal rubric. It's based on this scan only. Results can vary with lighting, angle, expression, camera distance and grooming.

It is **not** a population percentile, a ranking against other people, a medical or dermatology assessment, a measure of anyone's worth, or a universal standard of attractiveness.

## What you get

| Output | Range | What it means |
|---|---|---|
| Overall Look Score | 1–100, with a likely range | A weighted average of the categories that could be rated. A scan at every typical value reads 55 |
| Structure | Words: "Typical" or "Distinctive" | The relatively stable categories: proportions, symmetry, eyes and brows, midface, jaw and chin. Described, not ranked |
| Presentation Score | 1–100 | The categories you can influence: skin presentation, hair and grooming, expression and posture |
| Eight categories | Presentation: 1–100. Structure: words. Or **Not enough signal** | A category is never given a stand-in value when the scan can't support it |
| Within your control | Points | What skin, grooming and brow measurements could still add. Shown only when it's at least 3 points |
| Photo setup | Good, or what to adjust | Light, framing, head angle, background and camera distance. Never part of the score |
| Scan quality | 1–100 | Whether the photo can be analyzed. It is reported separately |
| Confidence | Low, Medium or High | How much the scan supports the result, overall and per category |

The score stays hidden until you choose to reveal it, and low scores are never shown in red.

## The eight categories

| Category | Weight | Group | Measured from |
|---|---|---|---|
| Proportions & balance | 15 percent | Structural | Middle-to-lower face ratio, width to height, horizontal fifths, feature centering, mouth placement |
| Bilateral symmetry | 5 percent | Structural | Left/right comparisons of eyes, brows, mouth corners, nose, jaw contour and the facial midline, after correcting for head tilt |
| Eye & brow area | 10 percent | Structural | Pupil spacing relative to face width, eye openness and brow balance |
| Midface & nose harmony | 8 percent | Structural | How nose, mouth and face widths relate to each other |
| Jaw, chin & lower face | 12 percent | Structural | Jaw-to-cheek width, chin width, chin centering and how visible the jaw contour is |
| Skin presentation | 20 percent | Presentation | Evenness of tone, redness variation, texture, shine, under-eye contrast and small spots. A cosmetic estimate only |
| Hair, facial hair & grooming | 15 percent | Presentation | Hair framing and coverage, and facial-hair symmetry and edges when facial hair is present |
| Expression & posture | 15 percent | Presentation | Mouth openness and shoulder level |

Optional left and right profile scans add a few side-view measurements (chin and nose projection). They're experimental in v1 and count with reduced confidence.

## How a scan becomes a score

1. **Landmarks.** Apple's Vision framework finds points around the eyes, brows, nose, mouth and jaw on your iPhone. Lineament corrects for head tilt using the facial midline.
2. **Measurements.** Every measurement is a ratio or an angle, so it doesn't depend on how far the face is from the camera. Skin, lighting and background use plain image statistics (color variation, texture, clipping, edges) inside regions built from the landmarks.
3. **A typical range, not a single ideal.** Each measurement has a broad typical range with a typical value in it. The typical value earns the middle of the scale. Moving away from it lowers the contribution gently inside the range, then more outside it, down to a floor, so one unusual measurement can't sink a category.
   - **Structure can't score above typical.** There's little evidence that "better than typical" bone structure looks better, and rewarding things you can't change isn't useful. Structure is described in words instead of a number.
   - **Skin, grooming and brows can.** They have a clear direction (more even skin tone, crisper facial-hair edges, more balanced brows) and they respond to what you do.
4. **Confidence weighting.** Each measurement counts according to how reliable it is in this scan (landmark precision, head angle, resolution). Confidence changes how much a measurement counts, never its value, so uncertainty alone can't lower a score.
5. **The scale.** A scan at every typical value scores 55, and the shaded "typical range" on the ruler runs from 45 to 65. The best skin, grooming and brow readings the rubric can see, with typical structure, give about 67. Scores in the 80s and 90s aren't reachable. The score is shown with a likely range ("Likely 53–60") that reflects scan-to-scan variation; lower confidence widens the range but never moves the score.
6. **The Overall Look Score** appears only when enough of the rubric could be rated: at least 60 percent of the category weight, including Proportions & balance and at least one presentation category, from a scan whose quality is at least 40. Otherwise you see the categories that could be rated and a suggestion for a better scan.

The same scan always gives the same result. Nothing in the rating is random, and Lineament doesn't use a trained attractiveness model.

## Scan quality and confidence

- Scan quality decides whether a photo can be analyzed (one face, large enough, facing the camera, sharp enough, reasonably lit). A poor photo is blocked or gets lower confidence, with one specific suggestion to fix it.
- Blur, compression, resolution and things covering the face never lower any appearance score.
- Lighting, framing, head angle, background and camera distance are checked separately as **Photo setup**, with one plain fix for each. They never count toward the score.
- Skin and hair & grooming are capped at Medium confidence in v1, until they've been evaluated across skin tones and hair types.

## When a category says "Not enough signal"

- **Hair & grooming** needs the hair mask that some iPhone front cameras provide with the photo. When there isn't one (often the case, and always for imported photos), Lineament doesn't guess.
- **Skin** is skipped when the light is very uneven, the photo is too soft or small, there's a strong color cast, or a smoothing filter seems to be applied.
- Measurements that don't apply to you (for example, facial-hair measures when you have no facial hair) are left out rather than counted against you.

## Strengths, opportunities and your plan

- **Strengths** are your two highest-rated categories with at least Medium confidence.
- **Opportunities** favour what you can actually change: skin, grooming and brows. Structural categories don't lead, because routines don't change bone structure.
- **Within your control** shows how many points those changeable measurements could still add if they reached the rubric's reachable level. It's a calculation you can check, not a forecast: it promises no date and never shows an altered face.
- "No action needed" and "Personal preference" are real outcomes, not gaps to fill.
- Routines stick to basic, low-risk practices with evidence labels. They never include surgery, injectables, prescriptions, supplements, restrictive dieting or jaw devices. Skin items point you to a pharmacist or dermatologist for anything persistent.

## Comparing scans over time

- A rescan is compared with your first scan and your previous one only when the two photos are comparable: similar distance, angle, lighting, expression, camera and rubric version.
- Changes smaller than the minimum detectable change (currently a placeholder of 3 points overall and 5 per category) are shown as "No meaningful change".
- Structural changes over short periods are labelled as likely photo variation.
- Every rating stores the rubric, measurement-code and model versions used, and every measurement. Trend lines don't connect scores from different rubric versions.
- When rubric 3.0.0 arrived, the app rescored every earlier scan from its stored measurements, so your history stays one comparable series. The earlier scores are kept with each scan, and the app tells you once that scores were rescaled.

## What Lineament never does

- Infer ethnicity, health, mood, tiredness or personality.
- Compare you with other people or estimate a percentile.
- Show a score before you choose to see it.
- Send your photos or analysis anywhere. Your face photos and analysis stay on this iPhone in version 1.

## What hasn't been tested yet

Every target range, tolerance and typical value in rubric v3 is **provisional**. They come from broad classical proportion conventions and published literature, not from Lineament data. Lineament hasn't yet been evaluated on a consented, diverse set of real people, so we make no claim about how accurate, consistent or even-handed the ratings are across skin tones, hair types, face shapes, ages or gender presentations. The tools to run that evaluation exist; the results will be published here when there are any, and any change to the bands will come as a new rubric version.

Rubric 3.0.0 changed the scale itself: typical readings moved from near the top of the scale to the middle, photo setup left the score, and the eye-line angle stopped being rated. Its typical values were set from the rubric's own ranges, not from rating people, so the new scale is still an estimate and isn't calibrated against human judgement.

Rubric 2.0.0 made two earlier changes. It stopped rating eye spacing against eye width, brow height and brow arch, because their ranges assumed anatomical points that the face landmarks don't capture. And it relaxed head alignment to match the scan guide.

---

*Lineament v1 · rubric 3.0.0 · published 30 October 2026 · Questions: [jfdevios@gmail.com](mailto:jfdevios@gmail.com) · [Privacy Policy](privacy) · [Terms of Use](terms) · [Support](support)*
