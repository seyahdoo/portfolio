+++
title = "Retevis RA685 Type C Port Fix"
date = "2023-04-27"
type = "post"
+++

### Intro

So I bought this radio, with type-c port for charging, expecting it to work as normal and fine. But the type c port on Retevis RA685 does not work with type-c to type-c cables. 
So I had to diagnose the issue, learn how to fix it and buy some tools to getthe job done. Here is how I did it.

### The Problem

The problem with the port is that it is only connected to VCC and Ground. 
This means when a usb c device is connected, the host device has no way of knowing the cable orientation or if anything is plugged in at all.
So type c hosts, by default will not provide power to this device.

### The Fix

To fix the issue, we gotta configure the client port correctly, this device expects 5V on VCC to ground so, we gotta add some configuration resistors to the port for this.
The pins CC1 and CC2 can do that. If there is a 5.1k ohm resistor between CC1 and ground and 5.1k ohm resistor between CC2 and ground. Host will send 5V to VCC.
Currently there is nothing connected to CC1 and CC2 on this radio board.

### Method

I know a bit of soldering, but I never had done soldering on this small components before. So I had to learn a bit.
In the end the information that was most cerucial was this the use of enameled copper wire. I bought 0.2mm magnet wire for this process.
The type c connector pins were tiny and I used the copper wire to expose that tiny pins.
There was a lot ot big components in the board that had pins on ground so I found a big enough pad to solder the resistor directly. 
This way the resistor will not wobble around.
I see most of the other people used UV curing green solder mask to fix this wires in place. I had to cheap out somewhere, so I havent bought any :D

### The Video

I recorded the whole process from start to finish, But unfortunately my head blocked the camera a bit on some soldering parts. 
Regardless, here is the uncut video of me fixing my radio's type c problem.

{{< youtube UwgA1_lA9YI >}}


### Materials Used

- [Retevis RA685 Radio](https://amzn.to/3ADxGeF)
- [Enameled Copper Wire 0.2mm](https://amzn.to/3LAcFrv)
- [Flux](https://amzn.to/3HmfAlc)
- [TS101 Soldering Iron](https://amzn.to/425YShE)
- [Electronics Kit](https://amzn.to/3NdNNai)
- [Soldering Kit](https://amzn.to/40J6hCr)
- [Knipex Super Knips](https://amzn.to/41HRDN7)
- [Knipex Pliers](https://amzn.to/3Lddfds)
- [Magnets](https://amzn.to/3LDmTaM) (I don't recomment these, buy bigger ones, they are easier to handle)
- [Blu Tac](https://amzn.to/3Hi5y4g) (This is not the blue tac I used)
- [Hot-Air Soldering Rework SMD Station](https://amzn.to/3LAI112) (You don't need this)


