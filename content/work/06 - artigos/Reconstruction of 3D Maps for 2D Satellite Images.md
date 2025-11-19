---
article: "[[Reconstruction_of_3D_Maps_for_2D_Satellite_Images.pdf]]"
tags:
  - "#article_review"
---
# Article Review

The paper proposes a **new and feasible approach** for constructing **virtual 3D digital maps** from 2D satellite images, using a combination of **OpenCV** technology for image analysis and **OpenGL** technology for 3D generation and rendering. Virtual 3D maps are favored over real 3D maps for their smaller data size, friendly interface, and lower construction cost, making them suitable for city visualization and urban planning.

### Core Procedure

1. **Data Collection:** A 2D satellite map (e.g., from Google Earth, PNG format) is used as input. Pictures of landscapes and landmarks are also collected for use as textures.
2. **Boundary Extraction:** **OpenCV** technology is employed to automatically identify the contours (boundaries) of map elements like buildings, roads, and lawns by finding obvious contours in zoomed satellite images.
3. **Data Setting:** Because automatic extraction can be imprecise (e.g., connected contours), manual correction is required. Users manually correct the results and input detailed information (type, height, texture, location) for each element, setting contours as rectangles for construction ease. This data is saved to a file (e.g., TXT).
4. **3D Generation:** The saved data is read by the **OpenGL** rendering program, which automatically draws the resolved elements one by one to establish the virtual 3D scenes. Elements are generated as simple regular 3D models (like cubes, cones, and cylinders).

### User Features and Uniqueness

The resulting 3D map system is enhanced with specialized features:

- **Roaming:** The system supports browsing via keyboard input and **data gloves based roaming**, which uses pressure transducers to recognize predefined gestures for changing 3D scenes. Initial attempts at camera-based gesture recognition using OpenCV were abandoned due to poor user experience.
- **Synchronization:** The 3D terminal and **Android clients** communicate using the **UDP protocol** to identify and synchronize a user’s location within the 3D scenes. This synchronization and the data gloves-based roaming are key distinctions from related works.
![[Pasted image 20251002080932.png]]
![[Pasted image 20251002080950.png]]
### Performance Note

System evaluation showed that the response time for initializing scenes and refreshing data increases **approximately linearly** with the number of models (up to 500). Performance declines rapidly around 600 models, primarily due to OpenGL rendering models one by one and limitations in computer hardware (CPU/memory).
