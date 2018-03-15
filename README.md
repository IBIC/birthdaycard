# Overview
	
This program generates a birthday card from an individual's structural MRI. 
It takes the brain image, identifies an attractive sagittal slice, overlays a party hat image, text that states “Happy Birthday” and “We Lobe You” on this slice, and creates an output image as shown below.
		 
[Example](IBIC/birthdaycard/alexdoe.jpg)

# Program requirements 
	
Prerequisites. This program is a Bash shell script that uses programs from the FSL software suite. It has been tested in Linux but should also run on macOS.

Inputs. The program requires the full structural scan and the skullstripped structural scan.
	     
We have tested this program on subjects from multiple studies, ranging
in age from approximately 10-90 years.

# Purpose
	
This program allows us to thank participants for their contribution to
research, conveying to them that their time is important and
appreciated by using their MRI data to create an inexpensive but
unique keepsake.
	    
# How to use

## Downloading 

There are two ways to download this program. Use the first method if you do not have `git` installed, or are not comfortable with `git`. 

1. As a zip file from Github
	1. Download the zip file from [IBIC/birthdaycard](https://github.com/IBIC/birthdaycard)
	2. Extract the zip file `birthdaycard-master.zip` to the top of the main directory
	3. A new folder named `birthdaycard-master` will be created
	4. This is where the program will be ran from for all users
	

	   
2. Using Git

Type the following command at your prompt:

```
git https://github.com/IBIC/birthdaycard
```


## Running the Program

For demonstration purposes we have included two NiFTI files, a
structural (`T1.nii.gz`) and skull stripped version
(`T1_skullstripped.nii.gz`). This is subject 50777 from the publically
available [ABIDE data set](http://fcon_1000.projects.nitrc.org/indi/abide/). We have given this subject
the name "Alex Doe".

Note that the program assumes that the orientation of the NiFTI files
matches those of the standard MNI template image.

### Quick Start

To run, cd into the `birthdaycard` directory and type the following.

```
./ibic_birthdaycard -t sampledata/T1.nii.gz -s sampledata/T1_skullstripped.nii.gz -o alexdoe -n "Alex Doe"
```

You see output on the terminal that looks like this.

[screendump](IBIC/birthdaycard/screendump.jpg)

The file name of the created card will be will be "alexdoe.jpg", and the path will be displayed in the terminal. You can view it by *how to view*. It should look like the example above.

### More Detailed Usage

The program has 5 different flags. Flags -t, -s, -o, and -n are
required, and flag -d is optional.  The order does not matter.
These flags and their descriptors can be found by typing

```
./ibic_birthdaycard -h
```

The -t flag specifies the name of the full structural scan file. (Must be in standard orientation)

The -s flag specifies the name of the the skull stripped structural scan file. (Must be in the same space and overlap with the full structural scan file.)

The -o flag specifies the output image file name (a .jpg extention is automatically added)

The -n flag specifies the name displayed in the birthday card (put name in quotations to retain spaces)

The -d flag is optional and  used to determine which saggital slice to use for the card, counted in centimeters, for the best image. By default, a saggital slice 1mm to the *right or left* of the midline is selected. Use this flag to override this selection if the saggital slice selected by default is not attractive.

It is important to verify that the saggital slice chosen is an attractive full brain that isand of voids and artifacts.

[Here is a good example of a bad slice](IBIC/birthdaycard/wapostscan.jpg)
[Source](https://www.washingtonpost.com/news/to-your-health/wp/2018/03/12/doctors-find-air-pocket-where-part-of-mans-brain-should-be/)

### Output

The file name and the path to where it was saved will be shown in the terminal. In this case, it will look like this

```
~/birthdaycard/alexdoe.jpg
```

By default this output is a 4x6 image that is viewable in a browser by running a command similar to

```
firefox ~/birthdaycard/alexdoe.jpg
```

## Installing 

After you have downloaded the program as above, you will have a
directory called `birthdaycard` which contains the programs. This
directory contains the `ibic_birthdaycard`
shell script, and a `lib` directory with supporting files (e.g., the
image of the birthday hat). 

By default, if you cd into the `birthdaycard` directory and run the `ibic_birthdaycard` program, everything will work correctly.

However, if you wish, you can install the program for all users. Copy
the `lib` directory into a shared location, and edit the variable `LIB_IBIC_BIRTHDAYCARD` in the `ibic_birthdaycard` script
to be the new location of your `lib` directory.


# Assembling and Distributing the Cards

This process is entirely up to the end user, but we will share what we
have found to work best for us.

We print the images at Bartells (using a self print kiosk that can
pull files off a USB drive) and insert them into frame card
holders. This gives us a system where we can decorate frame card
holders in advance for different studies and populations.  The frame card
holders can be decorated with markers, embossing powder, stamps, etc.

The default image size is 4 inches wide by 6 inches tall, which can be
changed in the program. As of this writing, Bartells charges $0.19
cents for each 4x6" print, and Amazon charges $0.09 cents for each
print; this size is quite affordable.

The cards and envelopes can be purchased online in bulk and prepared
in advance. We also include an insert that makes it clear that the
card is made from the participant's own image, thanks the participant
for their contribution, and includes contact information for the site.
We have included an example of our insert. These can be printed 4 to a
page, cut out, and placed in the card.

We have found that it is easiest to assemble and decorate cards at the
begining of the year, organize them by birthday month, and mail cards
at the end of every month for birthdays occurring in the next month. We
have also found that Mail Merge is a good tool for creating mailing lables.

In this way, assembling and decorating the cards can be done all at
once, and gives a good excuse to get the entire office together for a
fun decorating party.

Here are some sources for frame cards that hold 4x6" photos.

[Black Frames](https://www.bagsunlimited.com/product/7955/photo-frame-card)


[Black Envelopes](http://www.bagsunlimited.com/product/7959/photo-frame-envelope)


[White Frames and Envelopes](https://www.amazon.com/Strathmore-STR-105-250-White-Photo-Frame/dp/B000KNDKBI/ref=sr_1_3?ie=UTF8&qid=1520447257&sr=8-3&keywords=strathmore+photo+frame+cards)


# Credits
This program was a team effort from conception to distribution. These are the people who helped at many steps along the way.

* Christina Caso
* An Wang
* Briana Lee
* Trevor Day
* Ji-Min Wang
* Josh Wolfe
* Tara Madhyastha
