## 类: TouchBarScrubber

> 创建一个scrubber (可滚动的选择程序)

进程：[主进程](../tutorial/quick-start.md#main-process)

### `new TouchBarScrubber(options)` *实验功能*

* `选项` 对象 
  * `items` [ScrubberItem[]](structures/scrubber-item.md) - An array of items to place in this scrubber.
  * `select` Function - Called when the user taps an item that was not the last tapped item. 
    * `selectedIndex` Integer - The index of the item the user selected.
  * `highlight` Function - 当用户点击某一项时调用. 
    * highlightedIndex Integer - 用户选中项排序.
  * ` selectedStyle ` String - 选中项样式. 默认为 `null`.
  * ` overlayStyle ` String - 选中遮罩项样式. 默认为 ` null `.
  * `showArrowButtons` Boolean - 默认为 `false`.
  * `mode` String -默认为` free `。
  * `continuous` Boolean - 默认为`true`。

### 实例属性

以下为 ` TouchBarScrubber ` 实例的可用属性:

#### `touchBarScrubber.items`

A `ScrubberItem[]` array representing the items in this scrubber. Updating this value immediately updates the control in the touch bar. Updating deep properties inside this array **does not update the touch bar**.

#### `touchBarScrubber.selectedStyle`

A `String` representing the style that selected items in the scrubber should have. Updating this value immediately updates the control in the touch bar. Possible values:

* `background` - Maps to `[NSScrubberSelectionStyle roundedBackgroundStyle]`.
* `outline` - Maps to `[NSScrubberSelectionStyle outlineOverlayStyle]`.
* `null` - Actually null, not a string, removes all styles.

#### `touchBarScrubber.overlayStyle`

A `String` representing the style that selected items in the scrubber should have. This style is overlayed on top of the scrubber item instead of being placed behind it. Updating this value immediately updates the control in the touch bar. 可选值

* `background` - Maps to `[NSScrubberSelectionStyle roundedBackgroundStyle]`.
* `outline` - Maps to `[NSScrubberSelectionStyle outlineOverlayStyle]`.
* `null` - Actually null, not a string, removes all styles.

#### `touchBarScrubber.showArrowButtons`

A `Boolean` representing whether to show the left / right selection arrows in this scrubber. Updating this value immediately updates the control in the touch bar.

#### `touchBarScrubber.mode`

A `String` representing the mode of this scrubber. Updating this value immediately updates the control in the touch bar. Possible values:

* `fixed` - Maps to `NSScrubberModeFixed`.
* `free` - Maps to `NSScrubberModeFree`.

#### `touchBarScrubber.continuous`

A `Boolean` representing whether this scrubber is continuous or not. Updating this value immediately updates the control in the touch bar.