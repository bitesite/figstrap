# FigStrap

A front-end framework that helps bridge the gap between designers who use Figma and developers.

## Installation

At this time, FigStrap is only supported by applications that use [Sass](https://sass-lang.com/). To install, simply copy the files in the scss folder to your application.

(If you happen to be using Ruby on Rails, we have a [gem](https://github.com/bitesite/figstrap_rails) for that.)

## Features

### Auto-layout

The basic concept of auto-layout is that you have 1 frame, and inside that frame you have a bunch of items. You can also think of the frame as being the parent, and the items being the children.

In auto-layout, you specify if the items will be laid out in on top of each other (vertical) or if they will be laid out side by side (horizontal). You also specify what the gap / margin is between each item.

#### Usage

To use auto-layout, the easiest way is the look at your Figma design. On the left panel, you'll see a breakdown of all the frames and elements. What you want to look for are the frames. For every frame that uses auto-layout, you'll want to create a `div` with a class of `fgs-al`. Then, within that `div`, you'll create item/children `div`s with a class of `fgs-ali`. Then you can configure the parent by adding other classes.

##### Auto-Layout Frame

###### `fgs-al` (FigStrap Auto-layout)

To create an auto-layout frame, add the class `fgs-al` to your `div`.

###### `fgs-al-v` (FigStrap Auto-layout Vertical)

If you want the items in your frame to be laid out vertically, also add `fgs-al-v` to your `div`.

###### `fgs-al-h` (FigStrap Auto-layout Horizontal)

If you want the items in your frame to be laid out horizontally, also add `fgs-al-h` to your `div`.

###### `fgs-al-p-#` (FigStrap Auto-layout Padding)

To specify the padding all around your items, add the class `fgs-al-p-#` where # is the number of pixels you want the padding to be. Note, this is padding around all the items as a whole - not each individual item. This library is constantly changing, but at the moment, we support 10, 20, and 60 padding. e.g `fgs-al-p-20`

###### `fgs-al-g-#` (FigStrap Auto-layout Gap)

To specify the gap between your items, add the class `fgs-al-g-#` where # is the number of pixels you want the gap to be. This library is constantly changing, but at the moment, we support 6, 10, 16, 20, 30, 40, and 60 gaps. e.g `fgs-al-g-20`

###### FlexBox Helpers

FigStrap's auto-layout is based on using FlexBox and thus has all the benefits of using FlexBox. If you want to use `justify-content` or `align-items` from FlexBox, you can use the FigStrap FlexBox helper classes.

For `justify-content`, you can use:

- `fgs-al-justify-content-flex-start`
- `fgs-al-justify-content-flex-end`
- `fgs-al-justify-content-flex-center`
- `fgs-al-justify-content-flex-space-between`
- `fgs-al-justify-content-flex-space-around`
- `fgs-al-justify-content-flex-space-evenly`

And for `align-items`, you can use:

- `fgs-al-align-items-flex-start`
- `fgs-al-align-items-flex-end`
- `fgs-al-align-items-flex-center`
- `fgs-al-align-items-flex-stretch`
- `fgs-al-align-items-flex-baseline`

##### Auto-layout Item

###### `fgs-ali` (FigStrap Auto-layout Item)

To create an auto-layout item, add `div`s under your auto-layout container and add the class `fgs-ali` to each `div`. **Note: Auto-layout items themselves can also be frames.**

#### Simple Example

Here is a very basic example. Let's say you want a few images all stacked on top of each other, with 10 pixels between each one.

```
<div class='fgs-al fgs-al-v fgs-al-g-10'>
  <div class='fgs-ali'>
    <img src='my_image.png'>
  </div>
  <div class='fgs-ali'>
    <img src='my_image_2.png'>
  </div>
  <div class='fgs-ali'>
    <img src='my_image_3.png'>
  </div>
  <div class='fgs-ali'>
    <img src='my_image_4.png'>
  </div>
</div>
```

#### More complex example

One of the best things about auto-layout is that you can nest frames (ie. children can themselves be parents). So you might end up with something like this:

```
<div class='fgs-al fgs-al-v fgs-al-g-40'>
  <div class='fgs-ali fgs-al fgs-al-v fgs-al-g-10 fgs-al-align-items-center'>
    <div class='fgs-ali'>
      Welcome to our website!
    <div class='fgs-ali'>
    </div>
      <img src='my_image.png'>
    </div>
  </div>
  <div class='fgs-ali fgs-al fgs-al-h fgs-al-g-20'>
    <div class='fgs-ali'>
      <img src='feature_1.png'>
    </div>
    <div class='fgs-ali'>
      <img src='feature_2.png'>
    </div>
    <div class='fgs-ali'>
      <img src='feature_3.png'>
    </div>
  </div>
  <div class='fgs-ali'>
    <a href='/more'>Click here for more information</a>
  </div>
</div>
```

## Usage Rights

At this point, we're keeping this open source. Feel free to use it however you want, but note that we don't take any responsibility for anything that might happen if you use it and we reserve the right to modify this at any time.