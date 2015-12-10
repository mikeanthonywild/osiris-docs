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

- High-end cameras are about control - adds extra degree of control
- Why build?
    + Cheaper (not the case for a camera - economies of scale)
    + Tailor to your specifications
    + Freedom and power of choice of components
- Potential to foster an open ecosystem (idealistic)
- Market dominated by big players. Open specification allows smaller players to participate and serve smaller, more specialised markets which are too niche for big players.

Professional camera systems are second-to-none when it comes to image quality and usability. The camera accessories market in Western Europe and the USA was worth $1.7bn in 2006, a market which owed its existence to the modularity of modern cameras. With $270 of accessories bought per Digital Single Lens Reflex (DSLR) camera on average, customisability is clearly an important feature. [Camera Accessories Market to top Euros 1.1bn in Western Europe by 2009, Understanding and Solutions, March 2007 - https://web.archive.org/web/20070604201557/http://www.uands.com/downloadarticle.asp?id=43]. Despite this, cameras lack customisability in one key area: IO expansion. Audio, video and storage interfaces are usually a fixed function of the camera's motherboard, and therefore are not interchangeable – users must pre-empt their requirements in order to 'futureproof' their purchase. Inevitably these performance limits will be met; if a user wishes to step beyond these limits then an entirely new camera must be purchased. While some parts will undoubtedly be at the cutting edge of technology and require semi-frequent upgrades, other parts (camera bodies, audio amplifiers) [ref. limit of human auditory perception] may be technologically more mature and adhere to longer progression time-scales. Thus it seems wasteful and costly to re-purchase these parts when buying a new camera system.

It is not the intent of this paper however, to suggest that the concept of an interchangeable camera sensor is entirely original – a few high-end medium / large format cameras exist which support interchangeable 'sensor backs' designed by Hasselblad, Phase One and Mayima, however the interfaces are proprietary, thus limiting the user to a small handful of first-party options; additionally, the prohibitively high price (upwards of $10,000 at the time of writing) puts them far out of reach for the average professional photographer. Rather, the motivation of this project is to design an open standard for interchangeable sensors which can be freely implemented by anyone. In doing so, the basis for a truly modular and upgradable camera system is provided, with a broad range of applications including cinema, photography and computer vision. While idealistic, an open standard would benefit consumers by enabling new companies to gain a foothold serving smaller, more specialised markets which are too niche for established companies such as Nikon and Canon. Ultimately, this project aims to [......] by improving expandability options and fostering openness.  

## High-speed data transmission

## 
