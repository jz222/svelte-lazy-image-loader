# Svelte Lazy Image Loader

Shows a loading animation while loading an imagine.

**Without placeholder animation:**

![enter image description here](https://i.imgur.com/aUQmZTs.gif)

**With placeholder:**

![enter image description here](https://i.imgur.com/aSlEjAN.gif)

## Install

*npm*

`npm i svelte-lazy-image-loader`

*yarn*

`yarn add svelte-lazy-image-loader`

## API

|Props| Value|
|--|--|
|url|image url as string|
|alt|alt text as string|
|imageWidth|width of the image as string. Defaults to 100%.|
|imageHeight|height of the image as string|
|placeholderWidth|width of the placeholder as string. Defaults to 100%.|
|placeholderHeight|height of the placeholder as string. Defaults to 400px.|

## Examples

Default placeholder:

```javascript
<script>
	import ImageLoader from 'svelte-lazy-image-loader';
</script>

<ImageLoader
	url="https://example.com/image.png"
	alt="example image"
	imageWidth="500px"
	imageHeight="200px"
	placeholderWidth="500px"
	placeholderHeight="200px"
/>
```

Custom placeholder:

```javascript
<script>
	import ImageLoader from 'svelte-lazy-image-loader';
</script>

<ImageLoader
	url="https://example.com/image.png"
	alt="example image"
	imageHeight="200px"
	placeholderHeight="200px"
>
	<div>loading</div>
</ImageLoader>
```
