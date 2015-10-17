# Exam question
>For your chosen pervasive positioning system you should prepare a 5 minutes presentation at least covering the positioning concepts used, measurements techniques, system architecture choices, application classification types supported etc.

> Exam structure: **First**: What and Why, **then** How
> 1. Start with a short presentation (agenda on the whiteboard)
> 2. Tell the story (what/why/how)
> 3. Short recap/conclusion (point in the direction of new questions)

**Positioning**: Process to obtain the spatial position of a target
- *Process*: measuremetns, algorithms, infrastructure and protocols
- *Spatial position*: GPS coordinates, 'Storcenter Nord' etc.
- *Target*: a trolley, a firefighter or a department car

**Pervasive Positioning**: Positioning adequately, anytime, anywhere of anything
- *Adequately*: fitting to a use-case and its requirements
- *Anytime*: day or night
- *Anywhere*: outdorr, in buildings, in a mine or under water
- *Anything*: a cow, a fire fighter, a mobile phone or a car

# RADAR
Previously some have constructed an infered wireless network, which sole purpose was to locate users/devices. The goal of RADAR is to complement the data networking capabilities of RF wireless LANs with accurate user location tracking capabilities, thereby enchancing the value of such networks. RADAR uses signal strength to triangulate the user's coordinates. Triangulation is done using both empirically-determined and theoretically-computed signal strength information.
### Concepts
Consists of two phases:
1. Offline phase: Construct a radio map, i.e. map locations to signal strength information
	- A radio map entry _E=(x,y,z,d)_ contains the average signal strength for each access point
2. Online phase: Position of the target
	- Collect measurement(s)
	- Find the radio map entries, that best match the measurement(s)
	- Use Nearest Neighbor or k-Nearest Neighbor

### Measurements techniques
- **Simulation**: Simulate measurement (real-world assumptions). Easy to scale and to evaluate specific assumptions
- **Emulation**: Record the real-world measurements and re-play them later, i.e. it is possible to rerun emulation with new parameters
- **Experiment**: Record the positions produced by the positioning system in real-time, i.e. real-world performance

**Error distance**: Euclidian distance between estimated position and real position (or rather believe ground truth). If positioning system is used, the accuracy should be several times better than the evaluated system! If humans are employed, then one might need to interpolate between discrete known points.

### System architecture choices
Designed to work indoors. Performance can be impacted by the crowdedness, the user's body, movement and device type. Likewise with the number of AP and their placement/distribution. It requires that the Radio Map is up-to-date and the performance depends on the granularity of fingerprints and samples per fingerprint.
### Application classification types
Anything indoor, since outdoor systems do not work (as well) indoors with high accuracy. In applications where you cannot build a new infrastructure, e.g. ultrasound, infrared or ultrawideband

# GSM indoor localization
Due to higher coverage, GSm fingerprinting works in more places than 802.11 printing. Due to more stable infrastructure, 802.11 radio maps wil degrade more quickly than GSM radio maps. Due to shorter range, 802.11 fingerprinting will be more accurate than GSM fingerprinting given the same number of radio sources.
### Concepts
- Fingerprinting relies on a ''training phase''
- Localization algorithms: K-nearest neighbors technique
	- onecell: uses the reading of the single-strongest GSM cell
	- cell: uses readings of the 6-strongest GSM cells
	- chann: uses readings from up to 35 GSM channgles
- Greedy feature selection technique to select a subset of highly relevant radio sources to be used in the Euclidean distance calculation. The algorithm starts with a set that contains all available radio sources. At each step, the algorithm removes one radio source from the set. The radio source that is being removed is the radio source whose removal results in the larges increase in localization accuracy. The algorithm stops when removal of any radio source results in worse localization accuracy.

### Measurements techniques
The key idea that makes accurate GSM-based indoor localization possible is the use of wide signal-strength fingerprints. The wide fingerprint includes the 6-strongest GSM cells reading of up to 29 additional GSM channels, most of which are strong enough to be detected, but too weak to be used for efficient communication. The higher dimensionality introduced by the additional channels dramatically increases localization accuracy. According to the paper there are at least five benefits:
1. GSM coverage far exceeds the coverage of 802.11 networks
2. The wide acceptance of cellular phones makes them ideal conduits for the delivery of ubiquitous computing applications. A localization system based on cellular signals, such as GSM, leverage the phone's existing hardware and removes the need for additional radio interfaces
3. Because cellular towers are dispersed across the covered area, a cellular-based location systme would still work in situations where a building's electrical infrastructure has failed.
4. GSM, unlike 802.11 networks, operates in a licensed band, and therefore does not suffer from interferance from nearby devices transmitting on the same frequency (e.g. microvaes, cordless phones)
5. The significant expense and complexity of cellular base stations result in a network that evolves slowly and is only reconfigured infrequently.

### System architecture choices
### Application classification types
- Location indoor, where you cannot build a new infrastructure, e.g. ultrasound, infrared or ultrawideband
- Locating a person on a floor level

# Radio Beacons (Place Lab)

### Concepts
- High Coverage
- High Privacy
	- Devices should be able to position themselves based on passive monitoring of the environment.
- Low Cost
- Somewhat precise locations

### Measurements techniques
### System architecture choices
- **Radio Beacons**
Listens to wireless networking sources like 802.11 AP, fixed Bluetooth devices and GSM cell towers.
- **Beacon location**
If Place Lab knows nothing (Like John Snow?) about a beacon, being in range does not improve the location estimate. The beacon database plays the important role of serving this beacon location information to client devices. The databases come from institutions that own a large number of wireless networking beacons. This implies that the accuracy of Place Lab depends on other to be accurate when providing data.
Other location soruces comes from War-Driving, i.e. the act of driving around with amobile computer equipped with a GPS device and a radio (802.11/GSM/Bluetooth).
- **Clients**
Client functionallity is broken into three logical pieces: *spotters*, *mappers* and *trackers*.
**Spotters** are the eues and ears of the client and are responsible for the observing phenomenon in the physical world (typically one spotter per radio protocol supported by the device). 
**The mapper** provides the location of known beacons spotted by the spotter. This information always includes latitude and longitude, but may also contain other useful information like the antenna altitude, the age of the data, a learned propagation model or the power of the transmitter.
**The tracker** is the component that uses the streams of spotter observations and associated mapper data to produce estimates of the user's position. The trackers encapsulate the system's understanding of how various types of radio signal propagate and how propagation relates to distance, the physical environment and location. Trackers may use only the data provided to then by the spotter and the mapper, or may use extra data like read paths and building locations to produce more accurate estimates. It either uses a Venn diagram-like intersection of the observed beacons or a Bayesian particle filter. The filter can utilize beacon-specific range and propagation information.

### Application classification types



# Indoor Positioning Using GPS
> It has been consiredered a fact that GPS performs too poorly inside buildings to provide usable indoor positioning. We analyze results of a measurement campaign to improve the understanding of indoor GPS reception characteristics. The results show that using state-of-the-art recieves GPS availability is good in many buildings with standard material walls and roofs. The measured root mean squred 2D positioning error was below five meters in wooden buildings and below ten meters in most of the investigated brick and concrete buildings. Lower accuracies, where observed, can be linked to either low singal-to-noise ratios, multipath phenomena or bad satellite constellation geometry. We have also measured the indoor performance of embedded GPS reveivers in mobile phones which provided lower availability and accuracu than state-of-the-art ones. Finally, we consider how the GPS performance within a given building is dependent on local properties like close-by building elements and materials, number of walls, number of overlaying stories and surrounding buildings.

### Concepts
- State-of-the-art GPS revievers vs phones
- No fingerprinting or priori knowledged needed
- GPS availability is negatively impacted by: the number of overlaying stories, the roof material, as well as wall materials and the number of walls and the closeness to surrounding buildings. 

### Measurements techniques
- GPS Primer: GPS Satellites send signals modulated with a Psuedo-Random-Noise (PRN) code unique to each satellite. The receiver tries to acquire each GPS satellite's signal by correlating the signal spectrum with a local copy of the satellite's PRN code. Once a satellite's signal has been acquried, the receiver tracks it. To achieve the precise 3D positioning with a standard GPS receiver via trilateration, the positions of and distances to at least 4 satellites have to be known.
- A popular enchancement of GPS positioning is given by Assisted GPS. This uses an additional communication channel, e.g. cellular network, atmospheric corrections
- When GPS signals penetrate building materials, they are subjected to attenuation, resulting in lower signal-to-noise ratio. Furthermore, the signal is subject to multipath-phenomena: Reflection and refraction of the signal results in multiple echoes of the line-of-sight signal arriving at the receiver.
- High-Sensitivity GPS receivers are specifically designed for difficult signal conditions, i.e. to alleviate the above problems.


### System architecture choices
### Application classification types
GPS can be used as a positioning technology to provide situational awareness at a building-part granularity, especially when A-GPS is available, yielding an accuracy level of tens of meters and a time to first fix in the range from a few seconds to minutes. GPS though, does not currently provide instantly available indoor positioning accurate to the meter as might be crucial for some indoor applications, e.g. fire fighters navigating in burning buildings. Therefore, antother use of indoor GPS would be as a complementary indoor positioning technology, e.g. to help fighting the error growth over time of inertial positioning systems when available. The results are also indicative for the performance of future embedded GPS devices, as state-of-the-art receivers are being constantly miniaturized and power optimized.
# Electronic compasses and accelerometers
> This paper identifies the possibility of using electronic compasses and accelerometers in mobile phones, as a simple and scalable method of localization without war-driving. The idea is not fundamentally different from ship or air navigation systems, know for centruries. Nontheless, directly applying the idea to human-scale environments is non-trivial. Noise phone sensors and complicated human movements present pratical research challenges. We cope with these challenges by recording a person's walking patterns, and matching it against possbile path signatures generated from a local electronic map. Electronic maps enable greater coverage, while eliminating the reliance on WiFi infrastructure and expensive war-driving. Measurements on Nokia phones and evaluation with real users confirm the anticipated benefits. Results show a location accuracy of less than 11m in regions where today's localization services are unsatisfactory or unavailable.

### Concepts
- War-driving is an expensive calibration operation, but offers limited localization coverage.
- Independence from infrastructure.
- Energy consumption with GPS and WiFi pased localization pose a serious tradeoff between localization accuracy and energi.
- Uses only infrequent Assisted-GPS location, and use it as a reference for subsequent position estimation

### Measurements techniques
### System architecture choices
1. ComAcc starts by obtaining the phone's location using either GPS or A-GPS
2. The location is sent to a remote server, which returns a small map with all walking paths in that region
3. When the phone begins to move, then the accelerometer readings are used to estimate the user's displacement (using the rhythmic nature of human walking patterns)
4. Alongside the phone's compass orientations are also recorded, i.e. a time-indexed (distance, orientation)-tuple is formed

The noise that can occur with the accelerometer is handled by mathing the directional trail with possible walking paths around the phone's known location. The best matching path is declare to be the path of the user.

### Application classification types

# EnTracked
> An important feature of modern mobile device is that it can position itself. Notonly for useo n the device but also for remote applications that require tracking of the device. To be useful, such position tracking has to be energy-efficient to avoid having a major impact on the battry life of the mobile device. Furthermore, tracking has to robustly deliver position updates when faced with changing conditions such as delays due to positioning and communication, and changing positioning accuracy.
> This work propses EnTracked - a system that, based on the estimation and prediction of system conditions and mobility, schedules position updates to both minimize energy consumption and optimize robustness. The realized system tracks pedestrian targets equipped with GPS-enabled devices. The system is configurable to realize different trade-offs between energy consumption and robustness.
> We provede extensive experimental results by profiling how devices consume power, by emulation on collected data and by validation in several real-world deployments. Results from this profiling show how a device consumes power while tracking its position. Results from the emulation indicate that the system can estimate and predict system conditions and mobility. Furthermore they provide evidence for that system conditions and mobility. Furthermore they provide evidence for that the system can lower the enery consumption considerably and remain robust when faced with changing system conditions. By validation in several real-world deployments we provide evidence that the real system works as predicted by the emulation


### Concepts
- Minimizing the power consumption by ysing large intervals between position updates is a problem, since a pedestrian target can walk or run far during two to five minutes.
	- Other issuses is that GPS or the GSM transceiver have delays when initializing and powering off.
	- GPS positioning time depends on how well the GPS module knows the frequencies of visible satellites, the current satellite constellation etc
	- The accuracy of GPS positioning depends on the number of visible satellites, signal-blocking structures near the receiver and several other factors
	- Previous systems was evaulated by either simulation or emulation
- The EnTracked schedules position-updates to both minimize energy consumption and optimize robustness
	- Based on the estimation and prediction of system conditions and mobility
- It is configurable to realize different trade-offs between enery consumption and robustness

### Measurements techniques
- To make predictions it is required to have a device model that can account for the delays and power consumption of the device. If this cannout be obtained, then the system cannot make decisions that will minimize the power consumption and make position updates within the required limits.
	- One model is to use the instant model
	- They use a device specific model
	- Can be generalized with automatic paramter selection
- The power consumption is monitored
- Internal phone GPS
- Internal phone UMTS radio for sending data


### System architecture choices
- The device model
	- In both model they consider the following
		- Accelerometer
		- GPS
		- radio idle
		- radio active
		- idle (not strictly a feature, but gives a baseline)
	- **Power model**: Describes the power usage of the phone
		- To determine the power parameters for the above, they run experiments with different features enabled and disabled, then took the **average** for these measurements.
	- **Delay model**: Describes the delays when requesting a phone feature, e.g. the time it takes for the GPS to return a position
- EnTracked
	- Assumes an upper threshold on target speed (10 ms/s = 36 km/h for pedestrian)
	- The application have to provide error-limits (motivated to minimize power consumption or user will not use app)
	- The error limits might be calculated depending on application, e.g. zoom level

![Global Alignment Recursion](http://cs.au.dk/~mys/bioseq/entracked-fig4.png "Entracked flow")
![Global Alignment Recursion](http://cs.au.dk/~mys/bioseq/entracked-fig5.png "Entracked client logic")


### Application classification types
- Geo-based information applications
- Proximity and separation detection for social networking applications


# Energy-efficient Trajectory Tracking for Mobile Devices
### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# The Cricket Location-Support System
### Concepts
### Measurements techniques
### System architecture choices
### Application classification types