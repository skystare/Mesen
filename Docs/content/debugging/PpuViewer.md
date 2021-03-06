---
title: PPU Viewer
weight: 15
pre: ""
chapter: false
---

The PPU Viewer is a collection of tools allowing you to view/edit the current state of various parts of the PPU's memory: nametable RAM, CHR ROM/RAM, palette RAM and OAM (sprite) RAM.

All tabs share some common settings:

* **Auto-refresh**: Enabled by default, this makes the PPU viewer refresh at a rate of 15 FPS.
* **When emulation is running, show PPU data at scanline [y] and cycle [x]**: When using the auto-refresh option, this allows you to control at which point in a frame (cycle & scanline) the data is refreshed while the emulation is running. This is useful for games that perform CHR bank switching in the middle of a frame, for example.

## Nametable Viewer ##

<div class="imgBox"><div>
	<img src="/images/NametableViewer.png" />
	<span>Nametable Viewer</span>
</div></div>

The nametable viewer displays the contents of all 4 nametables (PPU addresses $2000 to $2FFF).  
Mouve-over a tile to display that tile's information on the right.
There are also a number of display options:

* **Show PPU Scroll Overlay**: Shows a blue rectangular overlay showing the current scroll position of the screen.
* **Show Tile Grid**: Displays a 8x8 pixels <span class="red">red</span> grid.
* **Show Attribute Grid**: Displays a 16x16 pixels <span class="blue">blue</span> grid.
* **Use Grayscale Palette**: Forces the nametables to be shown in a 4-color grayscale palette.
* **Highlight Tile Updates**: Displays a 8x8 red square overlay over tiles that have changed since the last frame.
* **Highlight Attribute Updates**: Displays a 16x16 yellow square overlay over attributes that have changed since the last frame.
* **Highlight tile selected in CHR viewer**: When enabled, click on a tile in the CHR viewer to select it, all occurrences of that tile will then be marked by a <span class="red">red</span> rectangle in the nametable viewer. 

<kbd>**Double-click**</kbd> on a tile in the nametable viewer to view/edit it in the CHR Viewer.

Additionally, you can <kbd>**right-click**</kbd> on a tile to copy the tile's information to the clipboard (for use with [HD Packs](/hdpacks.html)).

## CHR Viewer/Editor ##

<div class="imgBox"><div>
	<img src="/images/ChrViewer.png" />
	<span>CHR Viewer and Editor</span>
</div></div>

The CHR Viewer tab displays up to 2 4kb banks of CHR data at once.  It can display any portion of CHR RAM/ROM, even banks that are not currently selected.  
It also doubles up as a very simple graphic editor.

You can <kbd>**right-click**</kbd> on a tile to copy the tile's information (based on the currently selected palette) to the clipboard (for use with [HD Packs](/hdpacks.html)).

### Display Options ###

* **CHR Selection**: Select which portion of CHR memory to display in the viewer - by default, the portions of CHR memory mapped to the $0000-$1FFF range in PPU memory are shown.
* **Palette Selection**: Selects which palette to use to render the tiles - the first 4 palettes are for tiles, the last 4 palettes are for sprites.  There is also a 9th palette named "Grayscale" which forces the CHR viewer to display tiles in a 4-color grayscale palette.
* **Highlight**: This option allows tiles to be highlighted/dimmed based on the CDL file's current data.  This makes it possible to highlight/dim tiles that have never been drawn by the PPU, or vice versa.  *This option is only available for CHR ROM games*.
* **Display as 16x8 sprites**: When enabled, changes the display order of the tiles to make it easier to visualize 16x8 sprites.
* **Display tiles using their last known palette**: When enabled, any tile that has appeared in nametable memory since the debugger was opened will be shown using their last known palette (this overrides the palette selection dropdown for those tiles)
* **Show single color tiles using grayscale palette**: When enabled, any tile that contains a single color will be displayed using the grayscale palette instead (this overrides the palette selection dropdown for those tiles)

### Editing Tiles ###

To edit a tile, first click on the tile you want to edit in the left-side of the window. This will select the tile and highlight it with a transparent square.  

You can select the color you want to use by clicking on the `Color Picker`. You can also press keys 1 to 4 on your keyboard to quickly switch between the four colors.

With a tile selected, move your mouse to the tile preview above the `Color Picker` and **<kbd>click+drag</kbd>** to start drawing.  **<kbd>Right-click</kbd>** can be used to draw as well -- it always draws color #0.  

{{% notice tip %}}
Any change will remain in effect until a power cycle. If you want to save your modifications to a .nes file, or as an IPS patch, you can use the **<kbd>File&rarr;Save</kbd>** or **<kbd>File&rarr;Save edits as IPS</kbd>** commands in the [debugger window](/debugging/debugger.html). Keep in mind that edits done to CHR RAM *cannot* be saved.
{{% /notice %}}

## Sprite Viewer ##

<div class="imgBox"><div>
	<img src="/images/SpriteViewer.png" />
	<span>Sprite Viewer</span>
</div></div>

The Sprite Viewer displays the contents of OAM RAM. Mouve-over a sprite to display that sprite's information on the right.  

The `Screen Preview` displays all sprites as they will be shown on the screen, based on the current OAM data.

Like the nametable viewer, <kbd>**double-click**</kbd> on a tile to view/edit it in the CHR Viewer -- this works in the `Screen Preview` as well.

Additionally, you can <kbd>**right-click**</kbd> on a tile to copy the tile's information to the clipboard (for use with [HD Packs](/hdpacks.html)).

## Palette Viewer/Editor ##

<div class="imgBox"><div>
	<img src="/images/PaletteViewer.png" />
	<span>Palette Viewer and Editor</span>
</div></div>

The Palette Viewer displays basic information about the current state of palette RAM.  
It shows which colors are configured in each of the 8 available palettes.  
You can click on any color to select another color for that slot.