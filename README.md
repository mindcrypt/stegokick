# stegoWiper: A powerful and flexible active attack for disrupting stegomalware

Over the last 10 years, many threat groups have employed stegomalware or other steganography-based techniques to attack organizations from all sectors and in all regions of the world. Some examples are: APT15/Vixen Panda, APT23/Tropic Trooper, APT29/Cozy Bear, APT32/OceanLotus, APT34/OilRig, APT37/ScarCruft, APT38/Lazarus Group, Duqu Group, Turla, Vawtrack, Powload, Lokibot, Ursnif, IceID, etc.

Our research (see [APTs/](APTs/)) shows that most groups are employing very simple techniques (at least from an academic perspective) and known tools to circumvent perimeter defenses, although more advanced groups are also using steganography to hide C&C communication and data exfiltration. We argue that this lack of sophistication is not due to the lack of knowledge in steganography (some APTs, like Turla, have already experimented with advanced algorithms), but simply because organizations are not able to defend themselves, even against the simplest steganography techniques.

For this reason, we have created stegoWiper, a tool to blindly disrupt any image-based stegomalware, by attacking the weakest point of all steganography algorithms: their robustness. We have checked that it is capable of disrupting all steganography techniques and tools (Invoke-PSImage, F5, Steghide, openstego, ...) employed nowadays, as well as the most advanced algorithms available in the academic literature, based on matrix encryption, wet-papers, etc. (e.g. Hill, J-Uniward, Hugo). In fact, the more sophisticated a steganography technique is, the more disruption stegoWiper produces.

Moreover, our active attack allows us to disrupt any steganography payload from all the images exchanged by an organization by means of a web proxy ICAP (Internet Content Adaptation Protocol) service (see [c-icap/](c-icap/)), in real time and without having to identify whether the images contain hidden data first.


## Usage & Parameters

```
stegoWiper v0.1 - Cleans stego information from image files
                  (png, jpg, gif, bmp, svg)

Usage: ${myself} [-hvc <comment>] <input file> <output file>

Options:
  -h              Show this message and exit
  -v              Verbose mode
  -c <comment>    Add <comment> to output image file
```


## Examples - Breaking steganography

```
stegowiper.sh -c "stegoWiped" ursnif.png ursnif_clean.png
```

The [examples/](examples/) directory includes several base images that have been employed to hide secret information using different steganography algorithms, as well as the result of cleanign them with stegoWiper. 


## How it works?

stegoWiper removes all metadata comments from the input file, and also adds some imperceptible noise to the image (it doesn't matter if it really includes a hidden payload or not). If the image does contain a steganographic payload, this random noise alters it, so if you try to extract it, it will either fail or be corrupted, so steganomalware fails to execute.

We have tested several kinds (Uniform, Poisson, Laplacian, Impulsive, Multiplicative) and levels of noise, and the best one in terms of payload disruption and reducing the impact on the input image is the Gaussian one (see [tests/](tests/) for a summary of our experiments). It is also worth noting that, since the noise is random and distributed all over the image, attackers cannot know how to avoid it. This is important because other authors have proposed deterministic alterations (such as clearing the least significant bit of all pixels), so the attackers can easily bypass them (e.g. just by using the second least significaby bit).


## Author & license

This project has been developed by Dr. Alfonso Muñoz and Dr. Manuel Urueña The code is released under the GNU General Public License v3.

