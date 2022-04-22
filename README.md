# stegoWiper: A powerful and flexible active attack for disrupting stegomalware

Over the last 10 years, many threat groups have employed stegomalware or other steganography-based techniques to attack organizations from all sectors and in all regions of the world. Some examples are: APT15/Vixen Panda, APT23/Tropic Trooper, APT29/Cozy Bear, APT32/OceanLotus, APT34/OilRig, APT37/ScarCruft, APT38/Lazarus Group, Duqu Group, Turla, Vawtrack, Powload, Lokibot, Ursnif, IceID, etc.

Our research shows that most groups are employing very simple techniques (at least from an academic perspective) and known tools to circumvent perimeter defenses, although more advanced groups are also using steganography to hide C&C communication and data exfiltration. We argue that this lack of sophistication is not due to the lack of knowledge in steganography (some APTs have already experimented with advanced algorithms) but simply because organizations are not able to defend themselves, even against the simplest steganography techniques.

For this reason, we have created stegoWiper, a tool to blindly disrupt any image-based stegomalware, attacking the weakest point of all steganography algorithms: their robustness. We’ll show that it is capable of disrupting all steganography techniques and tools (Invoke-PSImage, F5, Steghide, openstego, ...) employed nowadays, as well as the most advanced algorithms available in the academic literature, based on matrix encryption, wet-papers, etc. (e.g. Hill, J-Uniward, Hugo). In fact, the more sophisticated a steganography technique is, the more disruption stegoWiper produces.

Moreover, our active attack allows us to disrupt any steganography payload from all the images exchanged by an organization by means of a web proxy ICAP (Internet Content Adaptation Protocol) service, in real time and without having to identify which images contain hidden data first.

# Usage & Parameters

```
examples
```

# Examples - Breaking steganography

```
examples
```

# Future work. Doing
- We are working to support the ICAP protocol. Stegokick using ICAP could connect to other systems to block stegomalware in real traffic.


# Author & license

This project has been developed by Dr. Alfonso Muñoz and Dr. Manuel Urueña The code is released under the GNU General Public License v3.
