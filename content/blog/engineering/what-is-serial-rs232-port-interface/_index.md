---
title: "What is serial (RS232) port interface"
date: 2015-09-14T12:52:56+00:00
description: "What is serial (RS232) port interface - PBXDom"
darkHeader: true
draft: false
layout: "single"
featured_image: "/wp-content/uploads/2015/09/RS232-or-DB9-female-connector_0.jpeg"
imageAlt: ""
type: "post"
customCss: ["/css/post-230.css"]
categories: "engineering"
readTime: "  3  min read"
tags: 
- "avaya smdr"
- "cisco cdr"
- "panasonic smdr"
- "pbx smdr"
- "smdr pbx"
- "smdr rs232"
- "smdr serial"
authors: 
- "rezamousavi"
linkedTo: 

relatedTo: 
- "/academy/video-tutorials/video-tutorials-how-to-create-cisco-call-manager-dashboard-in-10-minutes"
- "/blog/engineering/how-to-export-cisco-cdr-cmr-records"
- "/blog/engineering/how-to-create-avaya-ip-office-500-dashboard-in-10-minutes-v"

'og:locale': "en_US"
'og:type': "article"
'og:title': "What is serial (RS232) port interface - PBXDom"
'og:description': "What is serial (RS232) port interface - PBXDom"
'og:url': "https://www.pbxdom.com/blog/engineering/what-is-serial-rs232-port-interface"
'og:site_name': "PBXDom"
'article:publisher': "https://www.facebook.com/pbxdom"
'article:published_time': "2015-09-14T12:52:56+00:00"
'article:modified_time': "2021-04-25T15:59:25+00:00"
'og:image': "https://www.pbxdom.com/wp-content/uploads/2015/09/RS232-or-DB9-female-connector_0.jpeg"
'og:image:width': "650"
'og:image:height': "480"
'twitter:card': "summary_large_image"
'twitter:creator': "@pbxdom"
'twitter:site': "@pbxdom"
'twitter:label1': "Written by"
'twitter:data1': "Reza Mousavi"
'twitter:label2': "Est. reading time"
'twitter:data2': "4 minutes"
'msapplication-TileImage': "https://www.pbxdom.com/wp-content/uploads/2020/06/pbxdom000-300x300.png"
             

thumb:  
  srcset: "/wp-content/uploads/2015/09/RS232-or-DB9-female-connector_0.jpeg 650w, /wp-content/uploads/2015/09/RS232-or-DB9-female-connector_0-300x222.jpeg 300w"
  sizes: "(max-width: 650px) 100vw, 650px"
  width: "650"
  height: "480"
---
The serial port is an I/O (Input/Output) device. An I/O device is just a way to get data into and out of a computer. There are many types of I/O devices such as serial ports, parallel ports, disk drive controllers, ethernet boards, universal serial buses, etc. Most PC’s have one or two **serial ports**. Each has a 9-pin connector (sometimes 25-pin) (pic.1) on the back of the computer. Computer programs can send data (bytes) to the transmit pin (output) and receive bytes from the receive pin (input). The other pins are for control purposes and ground.

The **serial port** is much more than just a connector. It converts the data from parallel to serial and changes the electrical representation of the data. Inside the computer, data bits flow in parallel (using many wires at the same time). Serial flow is a stream of bits over a single wire (such as on the transmit or receive pin of the serial connector). For the serial port to create such a flow, it must convert data from parallel (inside the computer) to serial on the transmit pin (and conversely).

Most of the electronics of the serial port is found in a computer chip (or a part of a chip) known as a **UART**.

## Pins and Wires

Old PC’s used 25 pin connectors but only about 9 pins were actually used so today most connectors are only 9-pin. Each of the 9 pins usually connects to a wire. Besides the two wires used for transmitting and receiving data, another pin (wire) is signal ground. The voltage on any wire is measured with respect to this ground. Thus the minimum number of wires to use for 2-way transmission of data is 3\. Except that it has been known to work with no signal ground wire but with degraded performance and sometimes with errors.

There are still more wires which are for control purposes (signalling) only and not for sending bytes. All of these signals could have been shared on a single wire, but instead, there is a separate dedicated wire for every type of signal. Some (or all) of these control wires are called “modem control lines”. Modem control wires are either in the asserted state (on) of +12 volts or in the negated state (off) of -12 volts. One of these wires is to signal the computer to stop sending bytes out the serial port cable. Conversely, another wire signals the device attached to the serial port to stop sending bytes to the computer. If the attached device is a modem, other wires may tell the modem to hang up the telephone line or tell the computer that a connection has been made or that the telephone line is ringing (someone is attempting to call in).

   
## RS-232 or EIA-232, etc.

The **serial port** (not the USB) is usually a **RS-232-C**, **EIA-232-D**, or **EIA-232-E**. These three are almost the same thing. The original RS (Recommended Standard) prefix became EIA (Electronics Industries Association) and later EIA/TIA after EIA merged with TIA (Telecommunications Industries Association). The EIA-232 spec provides also for synchronous (sync) communication but the hardware to support sync is almost always missing on PC’s. The RS designation is obsolete but is still widely used. EIA will be used in this howto. Some documents use the full EIA/TIA designation.

 ## Data Flow (Speeds)

Data (bytes representing letters, pictures, etc.) flows into and out of your serial port. Flow rates (such as 56k (56000) bits/sec) are (incorrectly) called “speed”. But almost everyone says “speed” instead of “flow rate”.

It’s important to understand that the average speed is often less than the specified speed. Waits (or idle time) result in a lower average speed. These waits may include long waits of perhaps a second due to Flow Control. At the other extreme there may be very short waits (idle time) of several micro-seconds between bytes. If the device on the serial port (such as a modem) can’t accept the full serial port speed, then the average speed must be reduced.

## Flow Control

**Flow control** means the ability to slow down the flow of bytes in a wire. For **serial ports** this means the ability to stop and then restart the flow without any loss of bytes. Flow control is needed for modems to allow a jump in instantaneous flow rates.