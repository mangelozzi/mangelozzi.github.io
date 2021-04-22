# Blender Usage

## HOTKEYS

- Can see/edit the hotkeys by going to the main menu `EDIT` &rarr; `Preferences` &rarr; select the left heading `Keymap` &rarr; scoll down to `Sequencer` etc.


## HOTKEYS

### Sequencer

```
Selecting:
- LMB                   Select strip
- SHIFT + LMB           Select multiple strips
- LMB drag              Select box
- A                     Select all
- AA or ALT + A         De-select all

Navigating:
- LEFT                  Prev frame
- RIGHT                 Next frame
- SHIFT + LEFT          Prev frame x 10
- SHIFT + RIGHT         Next frame x 10
- CTRL + SHIFT + LEFT   Prev Marker
- CTRL + SHIFT + RIGHT  Next Marker
- PAGE UP               Jump to strip start
- PAGE DOWN             Jump to strip end
- Numpad 0              Center playhead on view
- ALT + Mouse wheel     Scroll playhead

Zooming:
- Numpad . (DEL)        Zoom to selection
- SHIFT + B then LMB    Box Zoom
- Mouse wheel           Scroll sequencer horizontal zoom
- HOME                  Zoom to fit specified video length
- Numpad +              Zoom in
- Numpad -              Zoom out

Editing:
- SHIFT + S             Snap strips to playhead
- K                     Cut
- SHIFT + K             Hold (hard) Cut
- G                     Grab
- SHIFT + G             Precision Grab (Frame by frame)
- G then number         Move by that number of frames (neg moves towards the start)
- X                     Contrain to X axis
- Y                     Contrain to Y axis
- Select strip middle then G  Move strip
- Select strip start  then G  Move start offset
- Select strip end    then G  Move end offset
- CTRL + Z              Undo
- CTRL + SHIFT + Z      Redo

Misc:
- SPACE                 Play
- N                     Options (toggle sequencer sidebar)
- CTL+HOME              Set start frame
- CTL+END               Set end frame
- M                     Set marker
```

### Preview

```
- HOME                  Fit frame to available space
- Mouse wheel           Zoom in/out
```

### Graph Editor

```
- G                     Drag nodes
- X                     Constrain drag node to X axis
- Y                     Constrain drag node to Y axis
```

### Dope sheet

```
- G                     Drag nodes
```

## 1. SETUP OPTIONS

<https://www.youtube.com/watch?v=qDOGFxMJoxw&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N>

1. Top bar delete all `workspace tabs`, add the same tabs as if you has selected `video editing`, i.e. `Video editing` and `Renderring`
2. `Properties` -> `Render properties` (looks like a camera backpanel), scroll to the bottom and expand `color management` and set `View transform`, set to `Standard`
3. `Properties` -> `Output properties` (looks like a printer)
    1. Next to dimensions click 3 dots with lines next to them, and select `HDTV 1080p`, then move mouse away to see its applied.
    2. Set default end frame to something high, e.g. 10mins = 10 * 60 * 25 = 15000
    3. Set the frame rate, e.g. `25` for South Africa (50 Hz power to prevent light flicker).
    4. Then set the default output dir
    5. `Output` set to `FFmpeg video` then select.
        1. Expand `Encoding`, select preset next to `Encoding` `h264 in MP4`
            1. `Output quality` set to `high quality`.
            2. `Encoding speed` set to `good`.
            3. Set `Keyframe interval` to half the frame rate, e.g. 12
            4. Set `Max B-frame` to `2`.
        2. Expand `Audio`
            1. Set `Audio Codec` to `AAC`
            2. Set `Bitrate` to `192`

4. Goto top program menu, `Edit` -> `Preferences`
    1. `Interface`
        1. Resolution Scaling
        2. Can set `Line width` to `Thick` (makes it easier to resize windows)
        3. Untick show splash screen.
        4. Expand `Temporary Windows` and set `Render in` to `Keep user interface`
    2. `System`
        1. Set GPU if you have
        2. Expand `Video sequencer` and set `Memory cache limit` to 0.8 of RAM, i.e. 0.8*16*1000 = 12800
5. Goto the bottom left of the screen, in the `Video sequencer`, click on `playback`
    1. Under `Audio`
        1. Change `No sync` to `AV sync`
        2. Check `Scrubbing`
    2. Under `Playback` check `Follow current frame`
6. Save changes permanently by going to `File` -> `Defaults` -> `Save startup file`

## 2. INTERACTING WITH AND ALTERING THE LAYOUT

<https://www.youtube.com/watch?v=n2m2uN9pH-w&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=2>

- Each panel is a `Editor Type`. Can change any panel to a different panel type.
    - Not there are two types of `Video sequencers`, `Sequencer` and `Preview`.
- Can make a copy of a panel by going to top left of the panel, should get a
  cross hair, then left click and drag. To reverse the process drag outward into
  another space to take that space (shows a carret).
- Global hotkeys apply to the panel the mouse is currently over.
- Hence be aware of where the cursor is when trying to use shortcuts.

## 3.  IMPORTING

https://www.youtube.com/watch?v=zslAZxC29rk&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=3

- There are three ways to import media:
    1. From the OS drag and drop into the sequencer, will be placed at the playhead (blue line).
    2. Using the built in importer.
        - Has a filter to filter the types of files.
        - Can select the display type, e.g. list or thumbnails.
        - Big advantage is that is has a `Recursion` option, e.g. show `3 levels` deep.
        - Click and drag from the center of the image/icon.
        - Only uses the framerate from the first import, then ignores every
          subsequent movie's frame rate that is added.
    3. At the top of sequencer, click `Add` then select `Movie/Sound/Image`
        1. Top right gear allows us to set default import settings.
        2. Can only add multiple movie via this method.
        3. When importing multiple movies, places them one after each other.

## 3. IMPORTING ISSUES

<https://www.youtube.com/watch?v=n7qeKekS10E&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=4>

- Goto `Help` -> `Manual`, on left nav click on `Files & Data System` -> `Media Formats`
- Blender can't support variable framefrate movies. Use `Handbrake` to convert the movie before importing it into blender. Can install it with `scoop install handbrake`.
- Encoders add an extra audio frame to their output. Can remove this frame:
    1. Select the audio strip
    2. Goto it's properties and expand `Time`, and set `Hold offset end`, and click right arrow to set it to one.

## Video Sequence

<https://www.youtube.com/watch?v=S6Ti9-eM5mw&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=5>

- Can toggle sidebar options with "N"
- Higher layers sit ontop, but layer 0 is special, and is the topmost layer.
- Can select a video strip, then in the sequencer options change the blend/opacity.
- If you select an audio strip, and check `Display waveform`.
- Can move the playhead by clicking/dragging on the Time area (time + framerate bar at the top of the sequencer)
- The orange knotches below the scrub area show the part of the video which are cached.
- If right click on a video strip, can see it's meta data by going to the sidebar, expanding `Source`, and look at e.g. dimensions.
    - If you wish to change the projects resolution to match the strips resolution, RMB on the video strip, and select `Movie Strip` -> `Set render size`.
- If goto preview, presss `n`, then select the `View` tab, then expand `View Settings`, the `channel` number shows from that number down. E.g. if you set it to 3, will show channels 3 down to 0.

## CUTS & MOVING STRIPS

<https://www.youtube.com/watch?v=qNrt0RFQCYY&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=6>

- 3 Ways to cut
    1. Top tabs of video sequencer `Strip` -> `Cut/Hold Cut`
    2. `K` or `SHIFT + K`
    3. `RMB` to bring up the context menu and select `Cut`
- Hold cut called so since it just keeps the frame the same. That's how one does a freeze frame in blender.

## PRECISION CUTTING

<https://www.youtube.com/watch?v=eA4c8ZChmPo&list=PLjyuVPBuorqJb1AwUu-wh61cLWMBVWS3N&index=7>

## KEYFRAMES

- Hover over the property to animate, and right click and select `insert keyframe`, or press `i` for "insert".
- `ALT+i` to delete keyframe.

## PREVIEW

- To show a preview, in the new window area select `Video Sequencer`
- Then in the top dropdown select `Preview`

## GRAPH EDITOR
- `g` to drag, `x`/`y` to constrain movement.
- Box select 2 nodes, click on `KEY` at the bottom, and select `Interpolation Mode` to choose preset graph.

## DOPESHEET
- Can shrink or expand length of transition by mousing over and pressing `g` and dragging it.
    - <https://www.youtube.com/watch?v=C1CjP2M7ZkE&t=8m37s>

