---
title: Blog Posts Gadget v2
description: Blog Posts gadget v2.
edit: https://github.com/wrapblogger/wrapblogger.github.io/blob/master/_blogger-snippets/gadget-blog-v2.md
toc: true
---

> Blog Posts gadget `v2`.

## Author name

Name of the profile of the post author.

`data:posts[i].author`

### Default

```xml
<!-- Author name -->
<b:if cond='data:post.author'>
  <span><data:post.author.name/></span>
</b:if>
```

#### Default with fallback

```xml
<!-- Author name -->
<b:if cond='data:post.author'>
  <span><data:post.author.name/></span>
<b:else/><!-- fallback -->
  <span>Anonymous</span>
</b:if>
```

### Anchors

```xml
<!-- Author name -->
<b:if cond='data:post.author'>
  <b:if cond='data:post.author.profileUrl'>
    <a expr:href='data:post.author.profileUrl' expr:title='data:messages.visitProfile'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:post.author.name/>
    </a>
  <b:else/><!-- no profileUrl -->
    <span><data:post.author.name/></span>
  </b:if>
</b:if>
```

#### Anchors with fallback

```xml
<!-- Author name -->
<b:if cond='data:post.author'>
  <b:if cond='data:post.author.profileUrl'>
    <a expr:href='data:post.author.profileUrl' expr:title='data:messages.visitProfile'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:post.author.name/>
    </a>
  <b:else/><!-- no profileUrl -->
    <span><data:post.author.name/></span>
  </b:if>
<b:else/><!-- fallback -->
  <span>Anonymous</span>
</b:if>
```

## Author photo

Photo of the profile of the post author.

`data:posts[i].author.authorPhoto`

**img src options**

- `128` is size
- `1:1` is aspect ratio
- calculation
  - width = size
    - width = `128`
  - height = (size * ratio height) / ratio width
    - height = (`128` * `1`) / `1` = `128`

### Default

```xml
<!-- Author photo -->
<b:if cond='data:post.author and data:post.author.authorPhoto'>
  <img>
    <!-- class --><b:class name='class-name'/>
    <!-- src --><b:attr expr:value='data:post.author.authorPhoto.image.isResizable ? resizeImage(data:post.author.authorPhoto.image, 128, "1:1") : data:post.author.authorPhoto.image' name='src'/>
    <!-- alt --><b:attr expr:value='data:post.author.name' name='alt'/>
    <b:attr name='b:whitespace' value='remove'/>
  </img>
</b:if>
```

#### Default with fallback

```xml
<!-- Author photo -->
<b:if cond='data:post.author and data:post.author.authorPhoto'>
  <img>
    <!-- class --><b:class name='class-name'/>
    <!-- src --><b:attr expr:value='data:post.author.authorPhoto.image.isResizable ? resizeImage(data:post.author.authorPhoto.image, 128, "1:1") : data:post.author.authorPhoto.image' name='src'/>
    <!-- alt --><b:attr expr:value='data:post.author.name' name='alt'/>
    <b:attr name='b:whitespace' value='remove'/>
  </img>
<b:else/><!-- fallback -->
  <img>
    <!-- class --><b:class name='class-name'/>
    <!-- src --><b:attr name='src' value='https://via.placeholder.com/128x128/777/eee?text=No+Image'/>
    <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
    <b:attr name='b:whitespace' value='remove'/>
  </img>
</b:if>
```

### Anchors

```xml
<!-- Author photo -->
<b:if cond='data:post.author and data:post.author.authorPhoto'>
  <b:tag cond='data:post.author.profileUrl' expr:href='data:post.author.profileUrl' name='a'>
    <b:attr cond='data:post.author.profileUrl' name='b:whitespace' value='remove'/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.author.authorPhoto.image.isResizable ? resizeImage(data:post.author.authorPhoto.image, 128, "1:1") : data:post.author.authorPhoto.image' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.author.name' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:tag>
</b:if>
```

#### Anchors with fallback

```xml
<!-- Author photo -->
<b:if cond='data:post.author and data:post.author.authorPhoto'>
  <b:tag cond='data:post.author.profileUrl' expr:href='data:post.author.profileUrl' name='a'>
    <b:attr cond='data:post.author.profileUrl' name='b:whitespace' value='remove'/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.author.authorPhoto.image.isResizable ? resizeImage(data:post.author.authorPhoto.image, 128, "1:1") : data:post.author.authorPhoto.image' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.author.name' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:tag>
<b:else/><!-- fallback -->
  <b:tag cond='data:post.author.profileUrl' expr:href='data:post.author.profileUrl' name='a'>
    <b:attr cond='data:post.author.profileUrl' name='b:whitespace' value='remove'/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr name='src' value='https://via.placeholder.com/128x128/777/eee?text=No+Image'/>
      <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:tag>
</b:if>
```

## Body

The content of the post.

`data:posts[i].body`

```xml
<!-- Body -->
<data:post.body/>
```

## Comments link

Link to the comments on the post.

`data:posts[i].commentsUrl`

### Default

```xml
<!-- Comments link -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:messages.comments/>
  </a>
</b:if>
```

#### Default with fallback

```xml
<!-- Comments link -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:messages.comments/>
  </a>
<b:else/><!-- fallback -->
  <span>Comments are disabled</span>
</b:if>
```

### Number of comments

Only working if using Blogger's default comments system.

```xml
<!-- Comments link -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <b:message name='messages.numberOfComments'>
      <b:param expr:value='data:post.numberOfComments' name='numComments'/>
    </b:message>
  </a>
</b:if>
```

#### Number of comments with fallback

```xml
<!-- Comments link -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <b:message name='messages.numberOfComments'>
      <b:param expr:value='data:post.numberOfComments' name='numComments'/>
    </b:message>
  </a>
<b:else/><!-- fallback -->
  <span>Comments are disabled</span>
</b:if>
```

## Date

Date of the post.

`data:posts[i].date`

### Default (published)

```xml
<!-- Date (published) -->
<time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
  <data:post.date/>
</time>
```

#### With custom format

```xml
<!-- Date (published) -->
<time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
  <b:eval expr='format(data:post.date, "dd/MM/YYYY")'/>
</time>
```

### Last updated

```xml
<!-- Date (updated) -->
<time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
  <data:post.lastUpdated/>
</time>
```

#### With custom format

```xml
<!-- Date (updated) -->
<time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
  <b:eval expr='format(data:post.lastUpdated, "dd/MM/YYYY")'/>
</time>
```

### Custom format

<table>
  <thead>
    <tr>
      <th>Period</th>
      <th>Symbol</th>
      <th>Example output</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">Year</td>
      <td><code>YY</code></td>
      <td><code>17</code></td>
      <td>Year, 2 digits</td>
    </tr>
    <tr>
      <td><code>YYYY</code></td>
      <td><code>2017</code></td>
      <td>Year, 4 digits</td>
    </tr>
    <tr>
      <td rowspan="5">Month</td>
      <td><code>M</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Month, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>MM</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Month, 2 digits</td>
    </tr>
    <tr>
      <td><code>MMM</code></td>
      <td><code>Jan</code>, <code>Nov</code></td>
      <td>Month, 3 Letters</td>
    </tr>
    <tr>
      <td><code>MMMM</code></td>
      <td><code>January</code>, <code>November</code></td>
      <td>Month, full name</td>
    </tr>
    <tr>
      <td><code>MMMMM</code></td>
      <td><code>J</code>, <code>N</code></td>
      <td>Month, 1st letter</td>
    </tr>
    <tr>
      <td rowspan="3">Week</td>
      <td><code>w</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Week of the year, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>ww</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Week of the year, 2 digits</td>
    </tr>
    <tr>
      <td><code>W</code></td>
      <td><code>4</code></td>
      <td>Week of the month, 1 digit</td>
    </tr>
    <tr>
      <td rowspan="10">Day</td>
      <td><code>d</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Day of the month, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>dd</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Day of the month, 2 digits</td>
    </tr>
    <tr>
      <td><code>D</code></td>
      <td><code>1</code>, <code>55</code>, <code>362</code></td>
      <td>Day of the year, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>DD</code></td>
      <td><code>01</code>, <code>55</code>, <code>362</code></td>
      <td>Day of the year, minimum 2 digits</td>
    </tr>
    <tr>
      <td><code>DDD</code></td>
      <td><code>001</code>, <code>055</code>, <code>362</code></td>
      <td>Day of the year, minimum 3 digits</td>
    </tr>
    <tr>
      <td><code>F</code></td>
      <td><code>3</code></td>
      <td>Xth day of the month. Example, the 3rd Tuesday of the month.</td>
    </tr>
    <tr>
      <td><code>E</code></td>
      <td><code>M</code>, <code>T</code></td>
      <td>Name of the day of the week. 1 letter</td>
    </tr>
    <tr>
      <td><code>EE</code></td>
      <td><code>Mo</code>, <code>Tu</code></td>
      <td>Name of the day of the week. 2 letters</td>
    </tr>
    <tr>
      <td><code>EEE</code></td>
      <td><code>Mon</code>, <code>Tue</code></td>
      <td>Name of the day of the week. 3 letters</td>
    </tr>
    <tr>
      <td><code>EEEE</code></td>
      <td><code>Monday</code>, <code>Tuesday</code></td>
      <td>Full name of the day of the week.</td>
    </tr>
    <tr>
      <td rowspan="3">Time of day</td>
      <td><code>aaaa</code></td>
      <td><code>AM</code>, <code>PM</code></td>
      <td rowspan="3">Names may vary depending on the region.</td>
    </tr>
    <tr>
      <td><code>bbbb</code></td>
      <td rowspan="2"><code>Morning</code>, <code>Afternoon</code>, <code>Evening</code></td>
    </tr>
    <tr>
      <td><code>BBBB</code></td>
    </tr>
    <tr>
      <td rowspan="4">Hour</td>
      <td><code>h</code></td>
      <td><code>1</code>, <code>11</code></td>
      <td>Time [1-12], minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>hh</code></td>
      <td><code>01</code>, <code>11</code></td>
      <td>Time [1-12], 2 digits</td>
    </tr>
    <tr>
      <td><code>H</code></td>
      <td><code>1</code>, <code>21</code></td>
      <td>Time [0-23], minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>HH</code></td>
      <td><code>01</code>, <code>21</code></td>
      <td>Time [0-23], 2 digits</td>
    </tr>
    <tr>
      <td rowspan="2">Minute</td>
      <td><code>m</code></td>
      <td><code>1</code>, <code>59</code></td>
      <td>Minute, minimum 1 digit</td>
    </tr>
    <tr>
      <td><code>mm</code></td>
      <td><code>01</code>, <code>59</code></td>
      <td>Minute, 2 digits</td>
    </tr>
  </tbody>
</table>

## Featured image

The featured image for the post.

`data:posts[i].featuredImage`

**img src options**

- `800` is size
- `16:9` is aspect ratio
- calculation
  - width = size
    - width = `800`
  - height = (size * ratio height) / ratio width
    - height = (`800` * `9`) / `16` = `450`

### Default

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  <b:else/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:if>
</b:if>
```

#### Default with fallback

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  <b:else/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:if>
<b:else/><!-- fallback -->
  <img>
    <!-- class --><b:class name='class-name'/>
    <!-- src --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", 800, "16:9")' name='src'/>
    <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
    <b:attr name='b:whitespace' value='remove'/>
  </img>
</b:if>
```

### Responsive images

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
      <!-- srcset --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, [200,400,800,1200,1600], "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='srcset'/>
      <!-- sizes --><b:attr name='sizes' value='100vw'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  <b:else/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
      <!-- srcset --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, [200,400,800,1200,1600], "16:9") : data:post.featuredImage' name='srcset'/>
      <!-- sizes --><b:attr name='sizes' value='100vw'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:if>
</b:if>
```

#### Responsive images with fallback

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
      <!-- srcset --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, [200,400,800,1200,1600], "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='srcset'/>
      <!-- sizes --><b:attr name='sizes' value='100vw'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  <b:else/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
      <!-- srcset --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, [200,400,800,1200,1600], "16:9") : data:post.featuredImage' name='srcset'/>
      <!-- sizes --><b:attr name='sizes' value='100vw'/>
      <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </b:if>
<b:else/><!-- fallback -->
  <img>
    <!-- class --><b:class name='class-name'/>
    <!-- src --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", 800, "16:9")' name='src'/>
    <!-- srcset --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", [200,400,800,1200,1600], "16:9")' name='srcset'/>
    <!-- sizes --><b:attr name='sizes' value='100vw'/>
    <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
    <b:attr name='b:whitespace' value='remove'/>
  </img>
</b:if>
```

### Anchors

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  <b:else/>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  </b:if>
</b:if>
```

#### Anchors with fallback

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  <b:else/>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  </b:if>
<b:else/><!-- fallback -->
  <a expr:href='data:post.link ?: data:post.url'>
    <b:attr name='b:whitespace' value='remove'/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", 800, "16:9")' name='src'/>
      <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </a>
</b:if>
```

#### Anchors with responsive images

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
        <!-- srcset --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, [200,400,800,1200,1600], "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='srcset'/>
        <!-- sizes --><b:attr name='sizes' value='100vw'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  <b:else/>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
        <!-- srcset --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, [200,400,800,1200,1600], "16:9") : data:post.featuredImage' name='srcset'/>
        <!-- sizes --><b:attr name='sizes' value='100vw'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  </b:if>
</b:if>
```

#### Anchors with responsive images and fallback

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <b:if cond='data:post.featuredImage.isYoutube'>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='src'/>
        <!-- srcset --><b:attr expr:value='data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, [200,400,800,1200,1600], "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl' name='srcset'/>
        <!-- sizes --><b:attr name='sizes' value='100vw'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  <b:else/>
    <a expr:href='data:post.link ?: data:post.url'>
      <b:attr name='b:whitespace' value='remove'/>
      <img>
        <!-- class --><b:class name='class-name'/>
        <!-- src --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage' name='src'/>
        <!-- srcset --><b:attr expr:value='data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, [200,400,800,1200,1600], "16:9") : data:post.featuredImage' name='srcset'/>
        <!-- sizes --><b:attr name='sizes' value='100vw'/>
        <!-- alt --><b:attr expr:value='data:post.title ? data:post.title : data:messages.image' name='alt'/>
        <b:attr name='b:whitespace' value='remove'/>
      </img>
    </a>
  </b:if>
<b:else/><!-- fallback -->
  <a expr:href='data:post.link ?: data:post.url'>
    <b:attr name='b:whitespace' value='remove'/>
    <img>
      <!-- class --><b:class name='class-name'/>
      <!-- src --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", 800, "16:9")' name='src'/>
      <!-- srcset --><b:attr expr:value='resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", [200,400,800,1200,1600], "16:9")' name='srcset'/>
      <!-- sizes --><b:attr name='sizes' value='100vw'/>
      <!-- alt --><b:attr expr:value='data:messages.image' name='alt'/>
      <b:attr name='b:whitespace' value='remove'/>
    </img>
  </a>
</b:if>
```

### CSS background-image

```xml
<!-- Featured image -->
<b:if cond='data:post.featuredImage'>
  <div class='class-name'><!-- target -->
    <b:if cond='data:post.featuredImage.isYoutube'>
      <!-- style --><b:attr expr:value='"background-image: url(" + (data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl) + ");"' name='style'/>
    <b:else/>
      <!-- style --><b:attr expr:value='"background-image: url(" + (data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage) + ");"' name='style'/>
    </b:if>
  </div><!-- /target -->
</b:if>
```

#### CSS background-image with fallback

```xml
<!-- Featured image -->
<div class='class-name'><!-- target -->
  <b:if cond='data:post.featuredImage'>
    <b:if cond='data:post.featuredImage.isYoutube'>
      <!-- style --><b:attr expr:value='"background-image: url(" + (data:post.featuredImage.youtubeMaxResDefaultUrl.isResizable ? resizeImage(data:post.featuredImage.youtubeMaxResDefaultUrl, 800, "16:9") : data:post.featuredImage.youtubeMaxResDefaultUrl) + ");"' name='style'/>
    <b:else/>
      <!-- style --><b:attr expr:value='"background-image: url(" + (data:post.featuredImage.isResizable ? resizeImage(data:post.featuredImage, 800, "16:9") : data:post.featuredImage) + ");"' name='style'/>
    </b:if>
  <b:else/><!-- fallback -->
    <!-- style --><b:attr expr:value='"background-image: url(" + resizeImage("https://lh3.googleusercontent.com/kBzrgG0CUVwpWe8oT8iPxL8HhKQdNVj1AX5BR2Y0Q_zoSpxHGPRtcysgTJsb8ZEsYmbWoNm-nEOyjBc03w=w1920-h1080-rw-no", 800, "16:9") + ");"' name='style'/>
  </b:if>
</div><!-- /target -->
```

## Labels

Labels of the post.

`data:posts[i].labels`

**Link options**

- `12` is maximum number of posts in label page

### Default

```xml
<!-- Labels -->
<b:if cond='data:post.labels'>
  <b:loop index='i' values='data:post.labels' var='label'>
    <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:label.name/>
    </a>
  </b:loop>
</b:if>
```

#### Default with fallback

```xml
<!-- Labels -->
<b:if cond='data:post.labels'>
  <b:loop index='i' values='data:post.labels' var='label'>
    <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:label.name/>
    </a>
  </b:loop>
<b:else/><!-- fallback -->
  <span>Unlabelled</span>
</b:if>
```

### Comma

```xml
<!-- Labels -->
<b:if cond='data:post.labels'>
  <b:loop index='i' values='data:post.labels' var='label'>
    <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:label.name/>
    </a><b:if cond='data:i != (data:post.labels.size - 1)'>,</b:if>
  </b:loop>
</b:if>
```

#### Comma with fallback

```xml
<!-- Labels -->
<b:if cond='data:post.labels'>
  <b:loop index='i' values='data:post.labels' var='label'>
    <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
      <b:attr name='b:whitespace' value='remove'/>
      <data:label.name/>
    </a><b:if cond='data:i != (data:post.labels.size - 1)'>,</b:if>
  </b:loop>
<b:else/><!-- fallback -->
  <span>Unlabelled</span>
</b:if>
```

## Read more

Link to the full post.

### Default

```xml
<!-- Read more -->
<b:if cond='data:post.hasJumpLink'>
  <a expr:href='fragment(data:post.url, "more")' role='button'>
    <b:attr expr:value='data:post.title ? data:post.title : ""' name='title'/>
    <b:attr name='b:whitespace' value='remove'/>
    <data:blog.jumpLinkMessage/>
  </a>
<b:else/>
  <b:if cond='data:post.snippets'>
    <a expr:href='data:post.url' role='button'>
      <b:attr expr:value='data:post.title ? data:post.title : ""' name='title'/>
      <b:attr name='b:whitespace' value='remove'/>
      <data:messages.keepReading/>
    </a>
  </b:if>
</b:if>
```

## Sharing

The share buttons for the post.

`data:posts[i].shareUrl`

### Default

```xml
<!-- Sharing -->
<a expr:href='params(data:post.shareUrl, { target: "twitter" })' target='_blank'>
  <b:attr name='b:whitespace' value='remove'/>
  Twitter
</a>
<a expr:href='params(data:post.shareUrl, { target: "facebook" })' target='_blank'>
  <b:attr name='b:whitespace' value='remove'/>
  Facebook
</a>
<a expr:href='params(data:post.shareUrl, { target: "pinterest" })' target='_blank'>
  <b:attr name='b:whitespace' value='remove'/>
  Pinterest
</a>
<a expr:href='params(data:post.shareUrl, { target: "email" })' target='_blank'>
  <b:attr name='b:whitespace' value='remove'/>
  Email
</a>
<a expr:href='params(data:post.shareUrl, { target: "blog" })' target='_blank'>
  <b:attr name='b:whitespace' value='remove'/>
  BlogThis!
</a>
```

### Dropdown example

```xml
<!-- Sharing -->
<div class='dropdown'>
  <a aria-expanded='false' aria-haspopup='true' class='dropdown-toggle' data-toggle='dropdown' expr:title='data:messages.share' href='#'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:messages.share/>
  </a>
  <div class='dropdown-menu'>
    <a class='dropdown-item' expr:href='params(data:post.shareUrl, { target: "twitter" })' target='_blank'>
      <b:attr name='b:whitespace' value='remove'/>
      Twitter
    </a>
    <a class='dropdown-item' expr:href='params(data:post.shareUrl, { target: "facebook" })' target='_blank'>
      <b:attr name='b:whitespace' value='remove'/>
      Facebook
    </a>
    <a class='dropdown-item' expr:href='params(data:post.shareUrl, { target: "pinterest" })' target='_blank'>
      <b:attr name='b:whitespace' value='remove'/>
      Pinterest
    </a>
    <a class='dropdown-item' expr:href='params(data:post.shareUrl, { target: "email" })' target='_blank'>
      <b:attr name='b:whitespace' value='remove'/>
      Email
    </a>
    <a class='dropdown-item' expr:href='params(data:post.shareUrl, { target: "blog" })' target='_blank'>
      <b:attr name='b:whitespace' value='remove'/>
      BlogThis!
    </a>
  </div>
</div>
```

## Snippet

Snippet of the post's content.

`data:posts[i].snippets`

### Short

```xml
<!-- Snippet -->
<data:post.snippets.short/>
```

Support for *jump break*:

```xml
<!-- Snippet -->
<b:if cond='data:post.hasJumpLink'>
  <data:post.body/>
<b:else/>
  <data:post.snippets.short/>
</b:if>
```

### Long

```xml
<!-- Snippet -->
<data:post.snippets.long/>
```

Support for *jump break*:

```xml
<!-- Snippet -->
<b:if cond='data:post.hasJumpLink'>
  <data:post.body/>
<b:else/>
  <data:post.snippets.long/>
</b:if>
```

### Custom

```xml
<!-- Snippet -->
<b:eval expr='snippet(data:post.snippets.long, { length: 150, links: false, linebreaks: false, ellipsis: true })'/>
```

Support for *jump break*:

```xml
<!-- Snippet -->
<b:if cond='data:post.hasJumpLink'>
  <data:post.body/>
<b:else/>
  <b:eval expr='snippet(data:post.snippets.long, { length: 150, links: false, linebreaks: false, ellipsis: true })'/>
</b:if>
```

## Title

Title of the post.

`data:posts[i].title`

### Default

```xml
<!-- Title -->
<b:if cond='data:post.title'>
  <data:post.title/>
</b:if>
```

#### Default with fallback

```xml
<!-- Title -->
<b:if cond='data:post.title'>
  <data:post.title/>
<b:else/><!-- fallback -->
  <data:messages.noTitle/>
</b:if>
```

### Anchors

```xml
<!-- Title -->
<b:if cond='data:post.title'>
  <a expr:href='data:post.link ?: data:post.url'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:post.title/>
  </a>
</b:if>
```

#### Anchors with fallback

```xml
<!-- Title -->
<b:if cond='data:post.title'>
  <a expr:href='data:post.link ?: data:post.url'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:post.title/>
  </a>
<b:else/><!-- fallback -->
  <a expr:href='data:post.link ?: data:post.url'>
    <b:attr name='b:whitespace' value='remove'/>
    <data:messages.noTitle/>
  </a>
</b:if>
```
