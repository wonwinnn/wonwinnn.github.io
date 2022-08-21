---
layout: post
title: "Notes on camera models"
comments: false
description: "Notes"
keywords: "camera model"
author: wonwinnn
---

This post concerns on some general concepts in camera models. 

### Projection & unprojection functions

An intuitive way to "see" how a camera model works is to obtain an undistorted image from the original distorted one. However, the undistorted image does not reflect the relationship between 3D points and image points directly. To connect 2D and 3D,  the normalized camera plane is needed to get rid of scale ambiguity.  A projection function describes the mapping from normalized camera plane to image plane. And a unprojection function describes the inverse mapping. These two functions make up a camera model. 

### Distortion center & principal point

The principal point refers to the intersection of optical axis and image plane. In most camera models, the principal point is also considered as the distortion center. However,  Hartley et al. argued that this assumption is not safe since the distortion center could be significantly displaced from the principal point [1].  Thus using an individual distortion center might be helpful in modeling a camera especially with high distortion. By the way, an ideal optical axis for the camera lens doesn't exist due to manufacturing tolerances. Besides of principal point and distortion center, several different image centers may be needed to model a camera fully [2].

### References

[1] R. I. Hartley and Sing Bing Kang, "Parameter-free radial distortion correction with centre of distortion estimation," *Tenth IEEE International Conference on Computer Vision (ICCV'05) Volume 1*, 2005, pp. 1834-1841 Vol. 2, doi: 10.1109/ICCV.2005.184.

[2] R. C. Willson and S. A. Shafer, "What is the center of the image?," *Proceedings of IEEE Conference on Computer Vision and Pattern Recognition*, 1993, pp. 670-671, doi: 10.1109/CVPR.1993.341035.
