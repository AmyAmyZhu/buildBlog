title: Unity 3D Camera
date: 2018-07-31 13:44:49
categories:
- Unity
tags:
- Unity
---

I am just starting building up an interesting isometric game. As an Unity3D beginner, I want to collbrate some important components information while I am learning. This blog listed most frequent used elements in Unity3D camera.

### Objection:

- perspective: Camera will render objects with perspective intact. It will look into both visible and invisible objects in 3D.

- orthographic: Camera will render objects uniformly, with no sense of perspective. It will look into only visible objects. The camera itself is like a plane. If you want to build 2.5D game, or isometric game, you can set camera orthographic.
    

<!-- more -->

### Culling Mask:

Choose which layers of objects you want to be visible. This includes or omits layers of objects to be rendered by the Camera.

### Depth:

If Camera's depth is larger, it will be rendered karger. When there are multiple Cameras in one Scene, only the Camera with largest depth will be visible. However, if Viewport Rect of the Camera with largest depth cannot cover all screen, then the Camera with low depth still can be visible and is rendered.

### Clear Flags:

In place camera is not capaturing, it will apear blank. If the camera is moving, it is possible we will see two pictures in the same time. Therefore, we need to clear flags. We can set up blackground to avoid blank happen.

### Clipping Planes:

Only between near (close to camera) and far (far away from camera) can be rendered.
