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

Many different camera formats exist; one of the key differentiators being the area of the image sensor. A larger sensor can capture more light and thus the dynamic range is greatly increased, resulting in higher image quality[reference]. This is true of both digital sensors, and their film counterparts. 

## Motivation

- High-end cameras are about control - adds extra degree of control
- Potential to foster an open ecosystem (idealistic)
- Market dominated by big players. Open specification allows smaller players to participate and serve smaller, more specialised markets which are too niche for big players.

Professional camera systems are second-to-none when it comes to image quality and usability. The camera accessories market in Western Europe and the USA was worth $1.7bn in 2006, a market which owed its existence to the modularity of modern cameras. With $270 of accessories bought per Digital Single Lens Reflex (DSLR) camera on average, customisability is clearly an important feature. [Camera Accessories Market to top Euros 1.1bn in Western Europe by 2009, Understanding and Solutions, March 2007 - https://web.archive.org/web/20070604201557/http://www.uands.com/downloadarticle.asp?id=43]. Despite this, cameras lack customisability in one key area: IO expansion. Audio, video and storage interfaces are usually a fixed function of the camera's motherboard, and therefore are not interchangeable – users must pre-empt their requirements in order to 'futureproof' their purchase. Inevitably these performance limits will be met; if a user wishes to step beyond these limits then an entirely new camera must be purchased. While some parts will undoubtedly be at the cutting edge of technology and require semi-frequent upgrades, other parts (camera bodies, audio amplifiers) [ref. limit of human auditory perception] may be technologically more mature and adhere to longer progression time-scales. Thus it seems wasteful and costly to re-purchase these parts when buying a new camera system.

It is not the intent of this paper however, to suggest that the concept of an interchangeable camera sensor is entirely original – a few high-end medium / large format cameras exist which support interchangeable 'sensor backs' designed by Hasselblad, Phase One and Mayima, however the interfaces are proprietary, thus limiting the user to a small handful of first-party options; additionally, the prohibitively high price (upwards of $10,000 at the time of writing) puts them far out of reach for the average professional photographer. Rather, the motivation of this project is to design an open standard for interchangeable sensors which can be freely implemented by anyone. In doing so, the basis for a truly modular and upgradable camera system is provided, with a broad range of applications including cinema, photography and computer vision. While idealistic, an open standard would benefit consumers by enabling new companies to gain a foothold serving smaller, more specialised markets which are too niche for established companies such as Nikon and Canon. Ultimately, this project aims to [......] in the future by improving expandability options and fostering openness.

## Pre-requisite concepts

### CCD and CMOS sensor technologies

- How are CCD and CMOS sensors different - how do they work?
- **If they measure light intensity, how do we get colour images?**

The sensors themselves fall into one of two categories depending on technology used: Charge-coupled Devices (CCD) and Complementary Metal-Oxide Semiconductors (CMOS). While both use an array of photosites to collect charge from incident photons during an exposure time, the readout and analogue-to-digital conversion process differs for each. During readout time, CCDs sequentially shift the accumulated charges into horizontal and vertical readout registers where they are transferred to a chip-level output amplifier and analogue-to-digital converter where the binary bitstream is generated. CCD image sensors can are capable of very low noise and high sensitivity due to the use optimised photosites; this made them a very popular choice for high-quality cameras.

Unlike CCDs, which rely on a very specialised fabrication process, CMOS sensors can be manufactured using traditional CMOS processes, benefiting greatly from the associated economies of scale. Active Pixel Sensors (APS), the most common form of CMOS sensor, differ from CCDs in that each photosite contains a dedicated amplifier, meaning that the light-induced voltages can be driven directly to the row and column decoders for digitisation. Because of the CMOS fabrication process, other camera functions can also be integrated onto the same chip, cutting both the cost and size of the device. [Ge, X., 2012. The design of a global shutter CMOS image sensor in 110nm technology (Doctoral dissertation, TU Delft, Delft University of Technology).]  This level of integration, and the faster speeds of parallel readout processing have meant that CMOS sensors have seen a recent surge in popularity, and are forecast to account for 85% of the total image sensor market in 2017. [http://www.icinsights.com/data/articles/documents/526.pdf]

Photosites can only measure light intensity, not wavelength, resulting in greyscale images. By placing a coloured filter in front of each photosite, it is possible to only let light of a certain colour through [http://www.google.co.uk/patents/US3971065]. Given the fixed pattern of the colour filter array (CFA), it is possible to generate a full-colour image using a demosaicing algorithm, the simplest of which is bilinear interpolation [http://research.microsoft.com/pubs/102068/Demosaicing_ICASSP04.pdf], to calculate the red, green and blue intensities for each pixel. One such CFA, the Bayer filter, contains twice as many green elements as red and blue to mimic the physiology of the human eye, as illustrated in [figure x].

![Bayer filter](https://upload.wikimedia.org/wikipedia/commons/3/37/Bayer_pattern_on_sensor.svg)

### High-speed data transmission

- Video is resource-intensive
- Current market demands high definition content by default
- 1080p bitrate calculation
- Signal integrity issues
    + Transmission line effects + impedance mismatch
    + Length matching
    + Crosstalk

- Existing interfaces (USB, GigE Vision, Cameralink, MIPI, HDMI?). Table 2 shows...

While sensors can capture both still images and video, this project mainly concerns the latter due to its resource-intensive nature. A recent study found that 75% of households in the United States had a high-definition television [http://www.leichtmanresearch.com/press/020813release.pdf]. The popularity of HD content makes it important to consider how bandwidth requirements increase with larger resolutions. An uncompressed 24-bit colour 1080p video at 24fps has a bitrate of almost 1.2 Gbps, as calculated in [equation x], well within the range where signal integrity becomes important.

When transmitting a high-frequency signal between two devices, careful attention must be applied to many aspects of the design to ensure that the signal integrity is preserved. The basic premise of signal integrity is covered here, however [section x] will cover the issue in greater depth. With low-frequency signals, a wire or PCB trace can be modelled as an ideal circuit, in that it has no resistance, capacitance or inductance. As the frequency increases however, so-called transmission line effects are prominent and the AC characteristics of the wire become very important. If there is a mismatch between the source, line and receiver impedances then the transmitted signal will not be fully absorbed at the receiver, resulting in any excess energy rebounding between source and receiver repeatedly until it has been fully absorbed. Due to superposition, the reflected waves will cause ringing and other signal integrity issues that will result in reduced signal quality. If the issue is severe enough, the receiver cannot correctly interpret the signal and bit errors will occur. Parallel wires can also cause mutual inductance problems whereby the magnetic field generated by current travelling through one wire, will induce a current in the adjacent wire. Similarly, mutual capacitance is caused by the coupling of the two electric fields. These issues can be mitigated by taking care to ensure that impedance is properly controlled and PCB traces are placed with care when designing circuits. [https://www.altera.com/content/dam/altera-www/global/en_US/pdfs/literature/wp/wp_sgnlntgry.pdf]

[Table x] shows a list of existing protocols / interfaces for transmitting image data. 

Name            Parent      Family      Bandwidth   Scheme      Complexity 
USB3 Vision     USB 3       USB         2.8 Gbps    Serial      High
GigE Vision     IP/UDP      Ethernet    800 Mbps    Serial      Medium    
Camera Link     N/A         Camera Link 6.8 Gbps    Serial      Medium
MIPI CSI-3      M-PHY       MIPI        23.2 Gbsps  Serial      Medium
HDMI 2.0        N/A         HDMI        18 Gbps     Serial      Low / Medium 

[http://www.controlvision.co.nz/newsletters/2013/08/Basler_Interface_Comparsion.pdf http://www.arrowdevices.com/blog/mipi-csi-3-a-game-changer-for-future-camera-technology/ http://www.hdmi.org/manufacturer/hdmi_2_0/hdmi_2_0_faq.aspx]


