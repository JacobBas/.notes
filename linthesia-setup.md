# Setting Up and Running Linthesia

Over the past few days I've had the urge to play more piano and to give myself a little motivation
I wanted to gamify the process a bit. One of the coolest (and probably most contentious) tools 
for learning the piano is Synthesia. The only problem for me is that I run a Linux machine and 
Synthesia is a Windows and MacOS only program.

After searching far and wide, I was able to find a Linux only fork of this program called
Linthesia. While an awesome program, there is not much documentation out there on how to 
setup the program on your machine hence why I'm writing this arcticle.

This article does assume a bit of coding/programming knowledge which I think is okay given the 
reader is a Linux user.

## Installing and Building Linthesia

The first thing that must be done is installing and building Linthesia. I spent way to much trying 
to figure this out since it wasn't working as expected from the repos `README.md` file. 

1. Clone the git repository with `git clone <github-adress>`
2. Setup a python virtual environment with `python3 -m venv venv`
3. Activate this environment with `source venv/bin/activate`
4. Install the two build dependencies `pip install meson && pip install ninja`
5. Initialize the build folder with `meson build`
6. Build the dependencies with `ninja -C build`
7. Set your root directory to the build folder with `cd build`
8. Finalize the build with `python3 /usr/bin/local/meson install`

## Installing and Setting up your MIDI controller

In order to actually hear sounds, you need to install those onto your machine. We are specifically
looking for `*.sf2` files.

Once these are installed we also need a synthesizer to play them. I chose to use FluidSynth which
is downloadable with the following command: `sudo apt-get install fluidsynth`.

Once this is installed you can run FluidSynth from the command line with
`fluidsynth -a alas /path/to/file.sf2` which will setup the audio and driver used to hear 
the sounds. From the Linthesia gui you should then be able to access the output by scrolling 
until you find something like `Synth Input port (XXXXX:0)`.
