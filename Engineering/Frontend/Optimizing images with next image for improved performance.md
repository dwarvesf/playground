---
tags: frontend, next/image, engineering/frontend, image optimization, performance
author: Tran Khac Vy
github_id: trankhacvy
date: 2023-06-15
---

Images are incredibly valuable on the internet. They help convey information, break up text, and showcase creative work, making websites more engaging for users. However, it's important to consider the impact of images on your website's performance. Higher resolution images have larger file sizes, leading to slower loading times. This can negatively affect your site's performance, which defeats the purpose of using images to enhance the user experience or drive sales.
Next.js offers a powerful solution called `next/image` that simplifies image optimization and improves website performance. In this article, we will explore how to leverage the `next/image` component to enhance the performance of your website.

## Cumulative Layout Shift
Cumulative Layout Shift (CLS) measures the visual stability of a web page. It quantifies how much the content layout moves or shifts while assets are being loaded and the page is displayed.
The way to avoid image-based layout shifts is to always size your images. This allows the browser to reserve precisely enough space for the image before it loads. `next/image` provides three options for sizing images and preventing layout shifts:

1/ Automatic sizing: Import the image statically, and it will be automatically sized.
```javascript
<Image
  src={profilePic}
  alt="Picture of the author"
  // width={500} automatically provided
  // height={500} automatically provided
  // blurDataURL="data:..." automatically provided
  // placeholder="blur" // Optional blur-up while loading
/>
```

2/ Explicit sizing: Include the width and height properties to explicitly specify the dimensions of the image.
```javascript
<Image
  src="https://s3.amazonaws.com/my-bucket/profile.png"
  alt="Picture of the author"
  width={500}
  height={500}
/>
```

3/ Implicit sizing: Use the "fill" property, which allows the image to expand and fill its parent element.

If you don't have information about the sizes of your images, there are a few options you can consider:

1/ Use the "fill" property:
By using the "fill" prop, your image will be sized based on its parent element. You can utilize CSS to allocate space for the parent element on the page and use the `sizes` prop to match different screen sizes. Additionally, you can employ properties like `object-fit` (with options like `fill`, `contain`, or `cover`) and `object-position` to define how the image should fit within that space.

2/ Normalize your images:
If you have control over the source of your images, you can modify your image pipeline to normalize them to a specific size. This ensures consistency and helps with optimizing their display.

3/ Adjust your API calls:
If your application retrieves image URLs through an API call, such as from a content management system (CMS), you might be able to modify the API call to include the image dimensions along with the URL. This way, you can obtain the image size information and use it appropriately in your code.

## Sizes optimization
Serving the right images for the right device sizes is a vital part of image optimization on the web. Serving a huge 2160x1600 image for users with mobile devices will lead to your users downloading unnecessary bandwidth, which can slow down page loads and hurt performance metrics.
The `next/image` has a useful feature called automatic source set generation. With this feature, `next/image` can generate different sizes of an image internally and decide which version to download based on the viewport size of the user's device.
If you know the expected device widths of your users, you can specify a list of device width breakpoints using the `deviceSizes` property in `next.config.js`. These widths are used when the `next/image` component uses `sizes` prop to ensure the correct image is served for user's device.
If no configuration is provided, the default below is used.

```
module.exports = {
  images: {
    deviceSizes: [640, 750, 828, 1080, 1200, 1920, 2048, 3840],
  },
}
```

To generate image srcsets, you can also define a list of image widths in your `next.config.js` file using the `images.imageSizes` property. These widths are combined with the `deviceSizes` to create a complete array of sizes.

The reason for having two separate lists is that `imageSizes` is specifically for images that have a `sizes` prop. This prop indicates that the image is smaller than the screen's full width. Therefore, all the sizes in `imageSizes` should be smaller than the smallest size in `deviceSizes`.

If you don't provide any custom configuration, the default settings are used.
```
module.exports = {
  images: {
    imageSizes: [16, 32, 48, 64, 96, 128, 256, 384],
  },
}
```

## Formats optimization
The `next/image` has a default behavior that automatically detects the image formats supported by the user's browser based on the request's `Accept` header.

When the `Accept` header matches multiple formats from the configured options, the first format in the array is chosen. So, the order of the formats in the array is important. If there is no match or if the source image is animated, the `next/image` will use the original image's format as a fallback.
If no configuration is provided, the default below is used.

```
module.exports = {
  images: {
    formats: ['image/webp'],
  },
};
```
You can enable AVIF support with the following configuration.
```
module.exports = {
  images: {
    formats: ['image/avif', 'image/webp'],
  },
};
```

Note: AVIF generally takes 20% longer to encode but it compresses 20% smaller compared to WebP. This means that the first time an image is requested, it will typically be slower and then subsequent requests that are cached will be faster.

Note: If you self-host with a Proxy/CDN in front of Next.js, you must configure the Proxy to forward the `Accept` header.

## Limitations and pricings
While the `next/image` component is excellent, there are certain limitations to be aware of when optimizing images with Vercel:
- The maximum size for an optimized image is **10 MB**, as set out in the Cacheable Responses limits. If this limit is exceeded, a `500` status code will be returned.
- Each source image has a maximum width and height of **8192 pixels**.
- A source image must be one of the following formats to be optimized (other formats will be served as-is): `.bmp`, `.ico`, `.icns`,`.jpeg`, `.pct`, `.png`, `.tiff`, `.webp`.

Another aspect to consider is the pricing. Image Optimization pricing is dependent on your plan and how many source images you have in your project.
| Plan       | Image Optimization Limit | Price (after limit hit) |
|------------|--------------------------|-------------------------|
| Hobby      | 1000 source images       | N/A                     |
| Pro        | 5000 source images       | $5 per 1000 source images |
| Enterprise | custom                   | Contact Sales for custom pricing |

Learn more about managing costs for [Image Optimization](https://vercel.com/docs/concepts/image-optimization/managing-image-optimization-costs).

## Conclusion
In conclusion, Next.js' `next/image` component provides powerful features for optimizing images and improving website performance. By properly sizing images, preventing layout shifts, and optimizing image formats, you can enhance Cumulative Layout Shift (CLS) and reduce loading times. However, it's important to consider the limitations and pricing factors associated with image optimization on Vercel based on your plan and the number of source images in your project.

## References
- https://nextjs.org/docs/pages/api-reference/components/image
- https://vercel.com/docs/concepts/image-optimization/limits-and-pricing
- https://vercel.com/docs/concepts/image-optimization/managing-image-optimization-costs