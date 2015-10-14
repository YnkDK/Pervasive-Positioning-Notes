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

### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# Radio Beacons (Place Lab)

### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# A-GPS

### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# Indoor Positioning Using GPS
### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# Electronic compasses and accelerometers
### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

# EnTracked
### Concepts
### Measurements techniques
### System architecture choices
### Application classification types

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