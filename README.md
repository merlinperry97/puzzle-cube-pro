# Puzzle Cube Pro 2 (v7.2.0)

> **This repository holds the documentation and the bug tracker for Puzzle Cube Pro 2.**
> The add-on itself is available on [Gumroad](https://merlin3d.gumroad.com/l/PuzzleCubePro).
> Found a problem? Use **Report a Bug** at the bottom of the Puzzle Cube Pro tab in Blender,
> or [open a bug report here](https://github.com/merlinperry97/puzzle-cube-pro/issues/new?template=bug_report.yml).


Animate twisty puzzles in Blender with real notation, then perform them like
characters: squash, stretch, spread and rock the puzzle on top of exact,
notation-driven turns.

By Merlin Perry, www.merlinperry.com, mp@merlinperry.com

Requires Blender 5.1 or newer.


## Editions

**Free** ships the complete add-on (notation, animation styles, Humanize,
solvers, Squash & Stretch Rig, Cube Manager) with the **3x3 Classic** rig.
Every other puzzle is shown in the library with a padlock so you can see what
the full package includes.

**Full** adds the whole library: 2x2 / 3x3 / 4x4 / 5x5 / 10x10 cubes plus
themed 3x3 variants, Skewb (3 styles), Pyraminx, Megaminx and the Speed Stack
timer prop. Get it at https://merlin3d.gumroad.com/l/PuzzleCubePro

Upgrading from Free to Full: install the Full zip over the top (same add-on,
same name). Your scenes keep working.


## Install

1. In Blender: Edit > Preferences > Add-ons > Install from Disk…
2. Pick the `PuzzleCubePro2_v7.2.0_*.zip` you downloaded and enable **Puzzle Cube Pro 2**.
3. Done. The presets file is bundled with the add-on.

If you keep the presets blend somewhere else (network drive, asset server),
point "Presets File" in the add-on preferences at your copy of
`presets.blend`.

If you have an older Puzzle Cube Pro (v6 or a .py file) installed, disable and
remove it first. Two versions cannot run at the same time.


## Quick start

1. Open the sidebar in the 3D viewport (press N) and find the **Puzzle Cube Pro** tab.
2. In **Rigs**, click the thumbnail, pick a puzzle, click **Add to Scene**.
   The puzzle lands ready to animate, no setup needed. Padlocked thumbnails
   are part of the full package.
3. Type or generate a sequence and press **Run Sequence**. The playhead ends
   after the last move, so you can keep stacking moves or run another sequence.

The **Cube Manager** lists every puzzle in the scene; click a row to make it
the active puzzle.


## Notation

Cubes (2x2–10x10) use standard WCA notation:

- Faces: `U D L R F B`, with `'` for counter-clockwise and `2` for a double turn (`R`, `R'`, `R2`).
- Wide moves: `Uw` / lowercase `u`, plus numeric depth on big cubes: `3Rw` turns the outer three layers.
- Slices: `M E S` (middle slices; on even cubes these turn the center pair).
- Whole-cube rotations: `x y z`.
- Slice pairs (big even cubes): `M[k]`, `E[k]`, `S[k]` turn the pair of slices k
  steps out from the center. Add `^` to counter-rotate the pair (`M[2]^`), and
  `'` / `2` as usual.

Skewb: `R U L B` with optional `'` (no double turns on a Skewb).

Pyraminx: faces `U L R B`, tips `u l r b`, with optional `'`.

Megaminx: `U D F B R L UR UL BR BL DR DL` with `'`, `2`, `2'`.

Smart quotes from pasted scrambles (’) are handled automatically. If a token
isn't understood, the add-on tells you which one it ignored.


## Animation controls

**Frames / Turn** sets the speed. **Gap frames** adds a pause between moves.
**2x for Double Turn** makes 180° turns take twice as long.

**Interpolation tiles**: select one or more of Linear, Ease In, Ease Out, Ramp,
Jam, Magnetic. With several tiles selected, each move randomly picks
one — great for a hand-solved feel. Ease In + Ease Out together = smooth in-out.

**Scramble** generates a legal random scramble (no move repeats its axis).
**Scramble to Solve** appends the exact inverse so the puzzle returns to solved —
run it, then play the timeline backwards from the midpoint for a "solving" shot.


## Tips

- Keys are baked frame-by-frame so the easing is exact. To retime a move,
  select its key block in the dope sheet and scale/slide it.
- The Megaminx face mapping is computed automatically on adopt. If your rig is
  oriented unusually, open **Face Mapping (advanced)** and fix or re-auto-map.
- Multiple rigs in one scene: click the rig you want, then **Re-Adopt** — the
  active object wins.
- The 3x3 Pumpkin uses large UDIM textures; it takes a moment to append.


## The presets file

`assets/presets.blend` is the asset library the add-on reads from. Opening it
directly shows an empty scene on purpose: the puzzles are stored in the file,
not laid out in it. Always add puzzles from the **Rigs** panel, which brings in
everything a rig needs and sets it up ready to animate.


## Squash & Stretch Rig (3x3 Classic)

The 3x3 Classic is a character rig as well as a puzzle. The **Squash & Stretch
Rig** panel (shown when the 3x3 Classic is selected) mirrors its controls:

- **Shape Dials**: squash spread, counter push, spread rotate, corner tuck,
  lattice deform, pull rotate.
- **Face / Corner Pulls**: 14 SPREAD controllers that pull the puzzle apart.
- **Rock**: tips the whole cube onto a bottom edge and rocks it back, pivoting
  on the real edge. Grab the puck above the cube, or use the Rock X / Rock Y
  fields.
- **Key Pose** keys every pull, the rock and the dials at the current frame.

The **Master** control moves, rotates and animates the whole puzzle; every turn
still bakes correctly against it. **Reset Pose** puts the master, root, rock
and dials back to default. **Reset** returns the puzzle to solved and leaves
your staging alone.


## Changelog

v7.2.0
- New: Rock control on the 3x3 Classic. A puck above the cube tips it onto
  any bottom edge and rocks it back, pivoting on the real edge rather than
  the centre. The whole rock setup follows the Master control, so you can
  move and rock at the same time.
- New: Root control on the 3x3 Classic (top of the hierarchy) for placing
  the whole rig in a shot.
- New: Free edition. The free download includes the full add-on with the
  3x3 Classic rig; the rest of the library shows as locked thumbnails with a
  link to the full package.
- Improved: Reset to Solved leaves Root and Rock alone (staging, like the
  Master); Reset Pose now returns them to default too.
- Fixed: Clear Keyframes no longer snaps a rocked or moved 3x3 Classic back
  to the origin.

v7.1.0
- New: Master control on every preset. Move, rotate or animate the whole
  puzzle and every turn still bakes correctly against it.
- New: optimal solvers for the 2x2 (11 moves or fewer) and the Skewb
  (11 or fewer); Pro Solve for the 3x3.
- New: Squash & Stretch Rig panel for the 3x3 Classic.
- New: Reset Pose button.
- Improved: control bones ship in XYZ Euler for readable curves; Pyraminx,
  Megaminx and Skewb Ultimate sit flat by default; 3x3 Classic pieces sit
  exactly on their bones.
- Panels reordered: Rigs, Settings, Manual Moves, Animation, Squash &
  Stretch Rig.

v7.0.0 — Puzzle Cube Pro 2
- New: Corner Cutting now works on the Skewb, Pyraminx and Megaminx too —
  when consecutive moves touch different pieces, the next one starts early
  for a fluid, hand-solved look. (Cubes keep the richer compound-rotation
  cutting for moves that share pieces.)
- New: Pro Solve (3x3) — an extended search that keeps refining for a few
  seconds and usually lands 18-20 move solutions (vs ~21 for Speed Solve).
- Changed: solve methods are now Reverse to Solve, Speed Solve and Pro
  Solve; the old ~150-move Human Solve has been retired.
- Improved: one consistent panel style throughout — left-aligned section
  headings, full-width fields, and the same spacing on every panel.
- Improved: each puzzle in presets.blend is now one single collection (no
  more Parts/Internals sub-collections) — a cleaner outliner when appending,
  with rig helpers still hidden via their object flags.
- Improved: legacy colour materials (Black, Purple, Blue.001, Orange.001,
  White.002 and friends) consolidated onto the canonical MAT_* family, so
  every puzzle shares one set of colour materials.
- New: presets.blend — the puzzle library is now a single editable presets
  file with an embedded manifest (`pcp_presets.json`). The panel is built
  from the manifest, presets can carry their own default animation/scramble
  settings, and content updates no longer require touching the add-on code.
- New: updated Skewb meshes (higher-detail centers and corners).
- Fixed: appending a puzzle no longer drags along unused authoring helpers
  from the presets file; anything unreferenced is discarded on add.
- Fixed: the Pumpkin's material referenced an entire spare armature for its
  texture space, pulling a second rig into every Pumpkin append. It now uses
  a lightweight empty at the same transform (renders identically).
- Fixed: a Skewb move could crash with "Context object has no attribute
  selected_objects" when run outside a 3D viewport context (Text Editor,
  background renders).
- Fixed: Skewb runs slowed down quadratically with sequence length — the
  per-move keyframe pass walked the whole action. 24-move Skewb runs went
  from minutes to under half a second.
- Fixed: adopting after append is deterministic (object scan order was
  previously unstable, which could adopt the wrong armature).
- Fixed: a version-mismatched or edited presets/library file now reports a
  clear error instead of a cryptic "not found in library file".
- Fixed: duplicate identical materials merged; Megaminx thumbnail no longer
  a copy of the Pyraminx one.

v6.7.5
- The bundled thumbnails now match the current library art. Note: Blender
  caches thumbnails for the session, so after re-rendering or editing artwork
  the surest way to refresh the Library panel is to restart Blender (the
  Refresh button next to Add to Scene also tries, but the cache can be stubborn
  within a session).

v6.7.4
- Added a Refresh button next to Add to Scene: reloads the puzzle thumbnails
  from disk, so after you re-render or edit the library artwork the Library
  panel updates without restarting Blender.

v6.7.3
- Adding the same puzzle more than once no longer creates duplicate materials
  or textures — new copies collapse back onto the originals already in the
  scene, so everything stays shared.
- Removing a puzzle or the timer now purges its unused meshes, materials and
  textures so deleting things keeps the file lean.

v6.7.2
- The library file now opens with every puzzle laid out and visible so it can
  be edited directly (open it, tweak meshes/materials, save). Add to Scene
  re-centers each puzzle to the world origin on spawn, so the editing layout
  doesn't affect where puzzles appear.

v6.7.1
- UI harmonised: every label/value sits on the same aligned two-column grid,
  section names come from the panel headers (no more label-as-title rows),
  boxes-in-boxes removed. Scramble and Animation are now two clean sibling
  panels. Interpolation tiles form a tidy 3-column grid; Corner Cutting and
  Timing Jitter sit under a single Humanize heading.

v6.7.0
- UI redesigned around Blender-native conventions and pared to three panels:
  "Puzzle Cube Pro" (library + a Cube Manager sub-panel), "Settings" (the
  contextual per-item controls, with a Manual Moves sub-panel), and
  "Scramble & Animation" (always shown for a selected cube). Aligned
  property rows, grouped headings and proper sliders throughout.
- Scramble and Animation are now always visible for a selected cube (only
  the Settings panel changes when the timer is selected).
- Vaulted the Megaminx Face Mapping controls from the interface (auto-mapping
  on adopt still runs behind the scenes).

v6.6.0
- UI clean sweep: the interface is now seven focused, collapsible panels —
  Puzzle Library, Cube Manager, Timer, Style & Timing, Manual Moves,
  Scramble, and Animation. Panels appear contextually: cube panels show for
  the selected cube, the Timer panel only when the timer is selected.
- Animation panel (formerly Run) now holds the sequence field, Run, Solve,
  Reset to Solved and Clear Keyframes together.
- Manual Moves is its own collapsed-by-default panel (no more inner
  fold-outs); Slice Pairs and Cube Rotations live inside it.

v6.5.0
- New: Solve button (3x3) — reads the cube exactly as it stands at the
  current frame (after manual moves, runs, anything) and animates a solution
  from there. Works with Human Solve or Speed Solve; the solution lands in
  the sequence field so you can inspect or reuse it. If a turn is
  mid-motion it asks you to move the playhead instead of guessing.
- Improved: the interface is now three separate collapsible panels —
  Puzzle Library, Cube Manager, and Settings — so each can be folded away
  independently.

v6.4.0
- New: Cube Manager — every puzzle in the scene (and the timer) in one list.
  Click a row to make it the active puzzle: the whole panel becomes
  contextual and follows your selection (timer rows show timer settings).
  Per-row controls: hide in viewport, hide in render, solo, and delete.
  The old Adopt/Change buttons are gone — selection does it all.
- Improved: the library thumbnail popup now fills a clean 7x3 grid.

v6.3.2
- Whole-cube rotations (x y z) never receive Jam or Magnetic easing when
  randomized styles are active — they always turn smoothly.
- Bounce easing removed.

v6.3.1
- Corner cutting rebuilt as true compound rotation: pieces shared between
  two overlapping turns smoothly finish the first arc while the second ramps
  in — mathematically continuous, no snap in any case (verified: per-frame
  motion with cutting on matches the smoothness of cutting off).
- The Flow strength slider is gone; Corner Cutting is now a simple on/off
  toggle with a tuned 40% overlap.

v6.3.0
- New: Speed Solve — a Kociemba two-phase solver producing near-optimal
  solutions (about 21 moves, 19-24 range) in under a second. Pick it in the
  Scramble-to-Solve Method dropdown next to Human Solve and Reverse.
  Pruning tables are bundled (7 MB); validated piece-for-piece against the
  facelet engine and hundreds of random scrambles.
- New: animation Style presets — Speedcuber, Smooth, Snappy, Robotic and
  Playful configure easing, Flow and jitter in one click; Custom exposes the
  full interpolation tile mix as before.
- Improved: Flow overlap restored to true corner cutting (moves genuinely
  overlap again) with the shared-piece flick capped at ~12 degrees so it
  reads as speed rather than a glitch.
- Housekeeping: obsolete v5-era scripts are moved out of the Blender addons
  folder into _obsolete_addons_backup in the product folder.

v6.2.0
- New: Reset to Solved and Clear Keyframes buttons in the panel header.
  Reset returns the puzzle to solved and removes its keyframes (adds none);
  Clear Keyframes strips the animation while keeping the current pose.
- Improved: Flow (corner cutting) no longer snaps — when the next move
  borrows pieces from the previous one, the previous move accelerates to
  finish exactly at the handoff instead of jumping the leftover arc.
- Improved: solver solutions are ~8% shorter (cancellation across commuting
  opposite-face moves, and corner twists always take the short direction).
  Re-validated against 1,500 random scrambles.

v6.1.0
- New: Real Solve (3x3) — "Scramble to Solve" can now compute a genuine
  beginner-method solution (cross, corners, second layer, last layer) instead
  of playing the scramble backwards. Pick "Real Solve (3x3)" as the Method.
  Validated against 3,500+ random scrambles.
- New: Humanize — Timing Jitter varies each move's speed; Flow (corner
  cutting) starts each move while the previous one is still settling, the way
  fast solvers actually turn.
- New: Speed Stack Timer sync — append the timer from the library and a Timer
  panel appears: drive its display over any frame range (or the last run) and
  it counts in real time, in the viewport and in renders.
- Fixed: notation now matches WCA everywhere. Previously M turned the wrong
  way (it followed R), whole-cube x was inverted, and numeric wide moves had
  R/L swapped (3Rw turned the left side). Rig moves and solver verified
  piece-by-piece for all 28 token types.
- Fixed: puzzles now land at the world origin with zeroed location/rotation
  (the library was rebuilt normalized; some rigs used to arrive rotated).
- Fixed: Megaminx slices now pivot correctly wherever the rig is placed —
  face axes are stored in rig space instead of world space.
- Improved: cleaner outliner — each puzzle appends as exactly three rows:
  the "<name>_RIG" armature, a flat "Parts" group with the visible pieces,
  and (where needed) a hidden "Internals" group for lattices and helpers.
  All legacy nesting removed; Internals never renders.
- Fixed: running a sequence could scramble slice moves — layer membership
  was being read at a stale frame. Sequences (including scramble + real
  solve, with or without Humanize) now verified to return the cube exactly
  to its starting pose.
- Improved: Change button now releases the rig, clears the selection, and
  reopens the library.

v6.0.0
- New: Puzzle Library — thumbnail browser that appends ready-to-animate puzzles
  from the bundled library file (drops at the 3D cursor, auto-adopts, frames view).
- New: 10x10 cube support (numeric wide moves and slice pairs work at any depth).
- New: Bounce easing tile; Megaminx face-mapping editor; Change Puzzle button;
  adopted rig name shown in the panel.
- Fixed: slice-pair `^` (counter-rotate) did nothing — `M[k]^` now turns the two
  slices in opposite directions, and scrambles that include it animate correctly.
- Fixed: Skewb moves were ~12x slower than necessary.
- Fixed: Pyraminx moves could report success without animating (missing/hidden
  rig pieces now abort with a clear message).
- Fixed: Adopt no longer silently switches puzzle type based on the selection;
  your dropdown choice always wins, and ambiguous scenes get a warning.
- Improved: unknown tokens in a sequence are reported instead of silently
  dropped; runs show a progress cursor; the playhead and scene end frame behave
  consistently across all puzzles.

v5.x — single-file add-on (2x2–5x5, Skewb, Pyraminx, Megaminx).


## License

GPL-3.0-or-later. The puzzle models and textures in
presets.blend are (c) Merlin Perry and licensed for use in your renders
and animations; redistribution of the library file itself is not permitted.
