# Project Pulse Dashboard Plan

## Goal and Assumption

Build Project Pulse as a static dashboard that presents project status, recent activity, and priority in a clear, accessible, responsive interface. The app is assumed to live in `app/` and to be served with:

```bash
python3 -m http.server 5500
```

The server working directory is `app/`. No application backend or build step is required. The dashboard should open its entry point at `http://localhost:5500/index.html`, rather than showing a directory listing.

## Implementation Phases

1. Agree on the project data schema and the visual direction, including the status and priority vocabulary, before final markup integration.
2. Designer defines the experience and implements the stylesheet in `app/styles.css`. Coder drafts the data file and semantic HTML skeleton in parallel after the data contract is agreed.
3. Coder completes data rendering in `app/index.html`, adds the launch configuration, and integrates the Designer's visual output.
4. Coder runs the full validation sequence after all implementation files are complete, then documents assumptions and any remaining limitations.

## File Assignments

| File | Owner | Assignment |
| --- | --- | --- |
| `app/index.html` | Coder | Build semantic dashboard markup, load the project data, render project cards, and provide accessible labels, headings, landmarks, and status/priority text. |
| `app/styles.css` | Designer | Define the visual direction, information hierarchy, responsive layout, accessible contrast and focus states, and status/priority visual treatment. Include the required `.dashboard`, `border-radius`, and `box-shadow` styling. |
| `app/project-data.json` | Coder | Define and populate the agreed JSON data contract for the dashboard's projects, including fields such as `name`, `owner`, `status`, `recentActivity`, and `priority`. |
| `.vscode/launch.json` | Coder | Configure the `Run Project Pulse Dashboard` launch target to serve `app/` on port `5500` and open `http://localhost:%s/index.html`. Use strict JSON with no comments. |

## Designer Responsibilities

- Establish the visual direction and information hierarchy so the dashboard supports quick scanning of project health and activity.
- Define a responsive layout that remains usable on narrow screens, with stable project-card structure and no overlapping content.
- Specify accessible color contrast, visible keyboard focus states, readable typography, and meaningful non-color text for status and priority.
- Define consistent visual treatment for status and priority, including distinct labels or indicators that do not rely on color alone.
- Implement or specify all dashboard styling in `app/styles.css`, including `.dashboard`, `project-card`, `border-radius`, and `box-shadow` selectors or declarations required by the implementation brief.

## Coder Responsibilities

- Agree the data schema with the Designer before final markup integration, then create `app/project-data.json` with representative Project Pulse content.
- Build `app/index.html` with semantic structure, accessible headings and landmarks, and a data-rendering approach that exposes each project's `name`, `owner`, `status`, `recentActivity`, and `priority`.
- Ensure project cards use the `project-card` class and that the page includes the `.dashboard` layout hook expected by the stylesheet.
- Create `.vscode/launch.json` as strict JSON for the `Run Project Pulse Dashboard` configuration, serving from `app/` and opening `http://localhost:%s/index.html`.
- Integrate the Designer's CSS with the HTML and data, then run the validation checks and record assumptions or issues for handoff.

## Dependencies and Ordering

- The data schema and visual direction must be agreed before final markup integration so the HTML, JSON, and CSS share the same field names, labels, and state vocabulary.
- Designer may define styles while Coder drafts `app/project-data.json` and the markup skeleton once the data contract is agreed.
- The app directory and the implementation files, especially the markup and data, must exist before the launch configuration can be meaningfully tested.
- Launch configuration and final HTML/CSS integration happen after the app structure is known.
- Final integration validation is sequential and depends on all implementation files being complete.

## Parallel Work Decisions

- **Parallel:** Designer works on visual direction and `app/styles.css` while Coder drafts `app/project-data.json` and the semantic markup skeleton, after both agree on the data contract.
- **Sequential after structure:** Coder finalizes `.vscode/launch.json` and completes the HTML/CSS integration after the app directory, entry point, and data shape are known.
- **Sequential validation:** Validation runs after implementation and integration are complete, so it tests the assembled dashboard rather than incomplete parallel outputs.

## Validation Expectations

1. Parse both JSON files with a JSON parser: `app/project-data.json` and `.vscode/launch.json`.
2. Verify the data has the expected top-level project collection and required project fields, including `name`, `owner`, `status`, `recentActivity`, and `priority`.
3. Verify `app/index.html` contains the `Project Pulse` title or heading, semantic dashboard structure, and `project-card` markup or rendering hook.
4. Verify `app/styles.css` contains the `.dashboard` selector and the required `border-radius` and `box-shadow` styling, plus responsive and focus-state rules.
5. Run the `Run Project Pulse Dashboard` configuration and confirm it serves from `app/` and opens `http://localhost:%s/index.html`, not a directory listing.
6. Inspect the rendered page at desktop and narrow responsive widths. Confirm content remains readable, project cards do not overlap, status and priority are understandable without color alone, and keyboard focus is visible.
7. Document assumptions, including the static-server model, port `5500`, the `app/` working directory, and any browser or launch-extension prerequisites.
