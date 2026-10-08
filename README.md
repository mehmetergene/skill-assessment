# CX Designer Skill Matrix

This corrected version keeps the original radial chart, floating skill panel, colors, header, footer, and visible **CSV**, **Image**, **Save**, **Clear All**, and fullscreen controls. The original 22 skill names and explanations are retained.

Modified on 2 October 2026 to add validated data loading, stable skill IDs, keyboard interaction, storage-failure warnings, portable progress backups, and safer image exports. The original Apache 2.0 license is included in `LICENSE`.

## Opening the assessment

The HTML includes the default skills and eight-level rubric and is designed to open without a server or internet connection. Direct double-click opening was not verified by the automated browser tools. When served through a web server, the app loads the adjacent `cx-designer-skills.json` and falls back to the embedded defaults if that file cannot be loaded or is invalid. A previously imported configuration is restored from browser storage when available.

Editing the adjacent JSON alone does not change the embedded defaults when opening the HTML directly from disk. Use the configuration import shortcut to load that edited file.

## Assessing skills

Click a skill label to show its full name and explanation in the original panel. Click a ring from 1 through 8 to set the proficiency level. Clicking the current level again clears that rating. Clicking the page title clears the selected skill without clearing ratings.

The levels are a **suggested self-assessment rubric**, not a validated certification or hiring standard. Choose the highest description you can support with recent examples of your own work. The guide develops from awareness and guided practice through independent delivery, coaching, organizational leadership, and developing practices others adopt. Review these descriptions with your team before using them for formal decisions. The selected rating's status has a tooltip with its level description, and each ring's accessible name includes its level definition.

## Keyboard controls

Tab reaches the existing header controls and skill labels. The chart provides these controls when a skill label or ring has focus:

| Key | Action |
| --- | --- |
| Enter or Space on a label | Select that skill and show its details |
| Left or Right on a label | Move to the previous or next skill |
| Home or End on a label | Move to the first or last skill |
| Up or Down on a label | Enter that skill's ring controls |
| 1–8 | Set the focused skill's rating directly |
| Delete or Backspace | Clear the focused skill's rating |
| Escape | Clear the selection without clearing ratings |
| Arrow keys on a ring | Move to an adjacent level and set that rating |
| Home or End on a ring | Set level 1 or level 8 |
| Enter or Space on a ring | Set that level, or clear it if already selected |

Focus is restored after the chart updates. A hidden live status announces changes and the existing panel displays errors when storage or imports fail.

## Backups, imports, and exports

The original visible controls also provide these shortcuts:

| Shortcut | Action |
| --- | --- |
| Shift-click **Save**, or Shift+Enter with Save focused | Download a JSON progress backup |
| Shift-click **Image**, or Shift+Enter with Image focused | Download the chart as SVG |
| Alt+O | Choose a skills configuration JSON file |
| Alt+R | Choose a JSON progress backup to restore |

Ordinary **Save** stores progress in the current browser. Ratings also save automatically as they change. Ordinary **Image** exports a PNG, and **CSV** exports all skill names, categories, ratings, and complete descriptions. **Clear All** requests confirmation before clearing all ratings.

Importing progress merges valid ratings for matching skill IDs into the current assessment. Imported values overwrite ratings for those IDs; other current ratings remain. Invalid values and unknown IDs are skipped. A progress backup contains ratings, not skill definitions. For a customized assessment on another device or browser, first import the matching skills configuration with Alt+O, then restore progress with Alt+R. Keep both files.

Progress and imported configurations are stored locally in the current browser when storage is available; they are not uploaded or synchronized. Different browsers, profiles, addresses, or copies of the HTML may have separate saved data. Clearing site data or using private browsing can remove progress. If saving fails, keep the page open and use Shift+Save to download a backup before leaving. An image, SVG, or CSV is not a restorable progress backup.

## Large content and remaining limits

The chart stays radial with larger datasets. Above 32 skills, it expands into a scrollable canvas. An assessment with 200 skills requires panning rather than shrinking every segment into the original desktop footprint. Narrow screens also allow chart panning, and the skill panel can scroll through long descriptions.

Very long chart labels use an ellipsis to keep the radial layout usable. Select the skill to read its complete name and description in the panel, or use CSV for the complete text. PNG exports can be reduced in scale for extremely large charts; SVG keeps the chart sharp when zoomed, but preserves the chart's abbreviated labels.

The original palette remains unchanged. Some faint labels and tag text retain low contrast. Keyboard support and content handling have improved, but this version does not claim full accessibility conformance.

## Editing the configuration

`cx-designer-skills.json` contains:

- `settings.title` and `settings.subtitle` for the heading.
- `skills.core` and `skills.supporting` arrays for the categories.
- A unique `id`, `name`, and `explanation` for each skill.
- Eight `levels` objects, each with `level`, `title`, and `description`, numbered 1 through 8.

Keep an existing skill's ID unchanged when editing its name or explanation. Assign a unique ID to each new skill. Older configurations without IDs receive generated IDs, but explicit IDs are preferable for preserving progress as content changes. Skill imports validate the configuration before applying it and keep ratings for matching IDs; back up progress first because ratings for skills absent from the new configuration are removed from the current assessment.

Valid original name-keyed ratings from `cxDesignerMarked` are mapped to current skill IDs when no version 2 assessment is saved. New progress uses `cxDesignerAssessment.v2`; imported configurations use `cxDesignerSkills.v2`. Malformed saved data does not prevent opening the assessment.

Keep the HTML, editable configuration, README, and license together when sharing the project.
