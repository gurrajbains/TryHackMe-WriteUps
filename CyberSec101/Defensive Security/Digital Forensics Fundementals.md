# Introduction to Digital Forensics

Forensics is the application of methods and procedures used to investigate and solve crimes. The branch of forensics that investigates cybercrimes is referred to as digital forensics.

Cybercrime refers to any criminal activity conducted using digital devices. This can include staging an attack, stealing data, or using a device to carry out another illegal activity. To track down cybercriminals, investigators use many techniques and tools to identify the people responsible.

Any time a digital device is found at a crime scene, it may be handed over to a digital forensics team. The team will usually have its own laboratory equipped with specialized forensic tools. From there, investigators can uncover information left on the device by its user.

### Question

Which team was handed the case by law enforcement?

**Answer:** Digital Forensics

# Digital Forensics Methodology

The National Institute of Standards and Technology (NIST) defines a general process for handling digital forensic investigations.

## Collection

The first phase is collection. Investigators collect data from devices and other items that may provide essential evidence. This can include laptops, cameras, USB drives, and other personal devices found at a crime scene. Investigators must also ensure that none of the collected data is altered or tampered with.

## Examination

The second phase is examination. During this stage, the collected data is filtered and information of interest is extracted.

Think about how many photos, messages, and files you may have on your phone or stored in the cloud. Investigators may need to examine large amounts of information to find anything that could be useful or relevant to the case.

## Analysis

The third phase is analysis. This is a critical phase because investigators must identify connections between multiple pieces of data and use them to form conclusions. Every piece of evidence must also fit into a clear and accurate timeline.

## Reporting

The final phase is reporting. A report contains the investigation's methodology, explains how the investigation was conducted, and presents the findings from the collected evidence to the relevant authorities.

Even within digital forensics, there are several specialized fields, such as computer forensics, mobile forensics, and network forensics. Each field focuses on a specific type of digital evidence.

# Evidence Acquisition

Digital forensic teams must obtain authorization from the relevant authorities before collecting data. Evidence collected without proper authorization may be considered inadmissible in court, meaning it cannot be used during legal proceedings.

Digital forensic evidence can contain private and sensitive information belonging to individuals, which is another reason proper authorization and procedures are required.

The chain of custody records where the evidence has been, who collected it, and who handled it at every point during the investigation. This ensures that there are no unexplained periods where the evidence may have been altered or accessed without authorization.

The use of write blockers is another method used to protect evidence. Write blockers prevent changes from being made to a storage device while investigators are collecting or examining its data.

# Windows Forensics

One of the most common types of digital forensics is performed on desktop computers and laptops because a large amount of criminal activity involves personal computer systems.

Part of this process involves creating images of the operating system. In this context, an image is not a normal picture. It is a bit-by-bit copy of the data stored on a system.

There are two main types of forensic images:

* Disk images
* Memory images

A disk image contains the data stored on a storage device. This data remains available even after the system has been restarted or shut down.

Tools commonly used for disk imaging and analysis include FTK Imager and Autopsy.

Memory images are bit-by-bit copies of a system's Random Access Memory (RAM). RAM contains volatile data, meaning the information is lost when the system shuts down and usually cannot be restored afterward.

Tools such as DumpIt can be used to capture memory images, while Volatility can be used to analyze them.
