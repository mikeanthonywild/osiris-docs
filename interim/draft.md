# Introduction

- Proliferation of digital cameras - film is niche
- Heart of camera - importance of image sensor
- Lack of modularity
- Project proposal

[Opening sentence...] cameras based on older film technologies have been confined to a diminishing list of niche uses, mainly in traditional film production and fine arts photography. At the heart of any digital camera lies the image sensor, which converts incident photons into electrical signals which can be digitised, processed and stored. 

Modern cameras – both still-motion and video – have a multitude of upgrade options: lenses, filters and other accessories are all interchangeable, allowing for a high level of control. As one of the most important components of the system, the image sensor plays a vital role in the composure of the final image. It dictates not only the output resolution, but also light sensitivity, colour representation, frame-rate and crop-factor. In spite of its significance, only a handful of expensive cinema and medium-format cameras include interchangeable sensors; even then, these components are proprietary. Upgrading the sensor in a mainstream camera requires the purchase of an entirely new system.

This paper details an FPGA-based sensor-agnostic interface which can be used to connect any image sensor to any image processor, thus providing the basis for a truly modular and upgradeable camera system.

## A brief history of camera technology

- Focus light through lens, through aperture, project onto backplane / imaging plane. The more light, the brighter the image. reference and diagram.
- First camera as we know it... based on camera-obscura
- All that's changed is the imaging plane - digital instead of analogue.
- First digital camera at Eastman Kodak 
- Increased sensor size = higher quality images - same thing for film
- Graph of notable camera system resolutions?

Modern cameras can trace their humble beginnings back to the discovery of the camera-obscura – an optical trick used by artists in the 1200s to explode an image and project it against a wall so that they may use it as a reference for painting. Surprisingly it took another [x]hundred years for it to evolve into something more closely [what's the word I'm looking for?] the cameras we know today. In [1850], [such and such] discovered that when treated with [silver chloride], exposing a piece of paper to light would cause a colour change from [white to black]. After further experimentation, [xxxx] found that the longer the paper was exposed to light, the darker it got. It only took a [few more years] until a man by the name of [blah blah blah] realised that images could be captured by focusing light onto the photosensitive paper using a lens.

[Camera diagram]
[Explain camera]

After the invention of the first transistor at Bell Laboratories in 1947[reference from cmos paper 2], electronics could be dramatically reduced in size through the use of integrated circuits, paving the way for the start of the digital era. [Talk about first digital camera]

Many different camera formats exist; one of the key differentiators being the area of the image sensor. A larger sensor can capture more light and thus the dynamic range is greatly increased, resulting in higher image quality[reference]. This is true of both digital sensors, and their film counterparts. The sensors themselves fall into one of two categories depending on technology used: Charge-coupled Devices (CCD) and Complementary Metal-Oxide Semiconductors (CMOS). [http://www.edn.com/electronics-news/4388726/CCD-vs-CMOS-image-sensors]

[Popular why? - http://www.icinsights.com/data/articles/documents/526.pdf]

## Motivations

- High-end cameras are about control

## High-speed data transmission

## 
