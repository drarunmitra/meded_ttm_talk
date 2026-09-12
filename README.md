# TTM talk — two columns, dimmed bullets, swapping right panel

    quarto render ttm-talk.qmd

## Four files

- `ttm-talk.qmd`   your text, unchanged, inside column divs
- `custom.scss`    the dimming and the stacked panel
- `ttm-pair.html`  the auto-pairing script (write once, never touch)
- `images/`        18 placeholders

## Editing

Plain markdown. No fragment syntax anywhere.

To add a bullet: add the bullet, add an image below it in the right
column. The script numbers them in order and pairs the nth bullet with
the nth image. If the counts do not match it warns in the browser console
and the later ones fall out of step.

Three classes are all the markup there is:

- `{.ttm}` on the slide heading — marks a slide for pairing
- `.ttm-bullets` on the left column
- `.ttm-panel` on the right column

A slide without `{.ttm}` behaves normally.

## Behaviour

Reveal marks every revealed fragment `.visible` but only the one just
revealed `.current-fragment`. So dimmed grey is the default state for a
revealed bullet and the current one overrides back to navy. Panels are
`.current-visible`, so exactly one shows at a time, absolutely positioned
so swapping never reflows the slide.

The slide number does not advance — fragments are not slides.

## Verified

Headless Chromium, Reveal 5.1: bullets auto-tagged, dim/current states
correct at each step, one panel visible per step, slide number stable.

## PDF

Fragments flatten on print. Use `?print-pdf` in the URL, which expands
each step onto its own page.
