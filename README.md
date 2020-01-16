# How to modify this website

The layout and content of this website is controlled by the `content.json` file that can be found in the same folder as this README. This file contains a list of website *segments*, each of which specify their own content. The order the segements are listed is the order the segments will be displayed in (vertically) on your website. The `content.json` file should look something like this:

``` javascript
[
  {
    ...
  },
  {
    ...
  },
  {
    ...
  },
]
```

Note: 
- The `...`'s indicate where segment content/configuration will go.
- The list of segments are given in a list: `[]`; and each segment are defined in an object: `{}`. 
- Each object (segment) in the list are separated by commas.

## Types of Segments

There are a number of different types of website segments that are available to you. If you want more segments, just ask nicely and I'll get around to it ASAP. Currently, there are four segments you can use: banner, spotlight, gallery, or contact.

When creating a new segment, create a new object (`{}`) in the list and use the "type" property to define what type of segment you want to create. For example, if you wanted to create a new spotlight segment, you'd add the following object to the list:

``` javascript
{
  "type": "spotlight",
  ...
}
```

Once this has been done, you can add properties specific to the segment you wish to create. Segment-specific properties are defined below:

### Banner
This segment is designed to be used once at the very top of the website (AKA the first segment in the list), but you can use it anywhere and as many times as you like. This segment displays an image next to written content/actions (on mobile the image moves above the content). The following are the properties you can set for this segment:

| Property | Type | Description |
| -------- | ---- | ----------- |
| title | Text | The title of the banner - the largest font in the banner. |
| subtitle | Text | The subtitle of the banner - the medium-sized font in the banner. |
| description | Text | The description of the banner - the smallest font in the banner. |
| image | Image object | The image filename to display in the banner. |
| actions | (optional) Actions object | The actions (buttons) to provide in the banner. |

#### Example
``` javascript
{
  "type": "banner",
  "title": "This is a title",
  "subtitle": "This is a subtitle.",
  "description": "This is a description.",
  "image": { "filename": "my-banner.jpg", "alttext": "My banner image." },
}

```

### Spotlight
This segment is designed to be used multiple times, anywhere in the website. It can be used to spotlight a specific image or story (hence the name). Much like the banner, this segment also displays an image next to some text content, however it is smaller and less in-your-face.

| Property | Type | Description |
| -------- | ---- | ----------- |
| title | Text | The title of the spotlight - the largest font in the spotlight. |
| description | Text | The description of the spotlight - the smallest font in the spotlight. |
| image | Image object | The image filename to display in the spotlight. |
| actions | (optional) Actions object | The actions (buttons) to provide in the spotlight. |
| flip | true or false | Whether or not to swap which side of the browser the image appears on. |

#### Example
``` javascript
{
  "type": "spotlight",
  "title": "My Spotlight",
  "description": "Description of my spotlight.",
  "image": { "filename": "my-spotlight.jpg", "alttext": "My spotlight image" },
  "flip": true
}
```

### Gallery
*Under construction - please don't use yet*

### Contact
The contact segment allows people visiting your site to contact you via email. It requires that you have a formspree account set up. 

| Property | Type | Description |
| -------- | ---- | ----------- |
| formspree | formspree URL | The URL to your formspree form. |
| dark | true or false | Whether or not to display the contact segment with a dark or light background. |

#### Example
``` javascript
{
  "type": "contact",
  "formspree": "https://formspree.io/abcdefgh",
  "dark": true
}
```

## Image and Action objects
Some of the segments above use Image or Action objects. How to use these objects is described below:

### Image object
An image object allows one to describe the filename and alternate text of an image. The alternate text is used in scenarios where a user cannot see the image. This object assumes the image you specified is located in the `/assets/images/` folder. To define these properties, we specify another object using `{}` brackets.

| Property | Type | Description |
| -------- | ---- | ----------- |
| filename | Text | The name of the image file you want to use in the segment. |
| alttext | (optional) Text | Alternative text to show instead of the image if the image can't be displayed (very rarely used). |

#### Example
*See Banner or Spotlight segments for an example of using an Image object.*

### Actions object
An actions object describes the actions (buttons) a user can use in that segment. These actions can be either a redirect somewhere else in your website or a redirect to another website. These actions can be listed vertically or horizontally, and individual buttons can be given more emphasis than others. To specify a segments actions, we create another object using `{}` brackets.

| Property | Type | Description |
| -------- | ---- | ----------- |
| orientation | horizontal or vertical | The orientation in which buttons are displayed. |
| buttons | List of button objects | The buttons and their corresponding actions. |

### Button object
A button object describes exactly what a button looks like and what its action does. We use *another* object to define its behaviour.

| Property | Type | Description |
| -------- | ---- | ----------- |
| text | Text | The text to display in the button. |
| link | Text | A URL that will be redirected to when the button is clicked. |
| emphasis | true or false | Whether or the not the button is to have more emphasis. |
