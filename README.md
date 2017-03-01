# ImageProc:  Image processor program exercise

### Public classes and functions:

**CommandProcessor**

void runLoop()  
Runs the command-processor loop.  Does not return until the 'quit'
command is entered.

**RegionProcessor**

RegionProcessor(const char *fNameStr)  
Constructs processor and loads image data from given file.

bool isImageDataValid()  
Returns true if image data was successfully loaded (via constructor).

int findRegion(int x, int y, int threshVal)  
Finds a region by scanning the image starting at the given pixel
location.  Adjacent pixels with values that are within the given
threshold will be accepted (and marked in the region map).  
x:  starting pixel row value.  
y:  starting pixel column value.  
threshVal:  threshold "difference" value; higher values will yield
            more pixel matches and larger regions.  
Returns:  1 if parameter value(s) out of range; otherwise 0.

void applyFoundRegionToImage()  
Applies region map (generated via 'findRegion()') to the image.
Pixels outside the region are blacked out.

bool isImageDataModified()  
Returns true if image data has been modified by 'applyFoundRegionToImage()'.

void showImage(std::string const &win_name)  
Displays the current working image for this processor object.  
win_name:  ID string for window.

bool saveImageDataToFile(const char *fNameStr)  
Save the current inage data to a file.  
fNameStr:  name of destination file.  
Returns:  true if successful; false if error.

void printImageInfo()  
Prints image information to the console.

### Requirements:
 * OpenCV 2.X  
 * CMake > 2.8

### Building/running (with CMake and Ubuntu 16.04):
    cmake .
    make
    ./ImageProc

### Commands:

LOAD_IMAGE filename :     Load image data file  
FIND_REGION X Y Thresh :  Find region of interest (see below)  
DISPLAY_IMAGE :           Display current image data  
SAVE_IMAGE filename :     Save image data to file  
QUIT :                    Exit program  

FIND_REGION X Y Thresh:  
   Finds a region by scanning the image starting at the given pixel
   location.  Adjacent pixels with values that are within the given
   threshold will be accepted and marked.  
   X:  starting pixel row value (0-based).  
   Y:  starting pixel column value (0-based).  
   Thresh:  threshold "difference" value; higher values will yield
            more pixel matches and larger regions.  Range 0-255.

Command processing is case-insensitive.  The following command aliases may be used:

LOAD = LOAD_IMAGE  
FIND = FIND_REGION  
SHOW = DISPLAY_IMAGE  
SAVE = SAVE_IMAGE  
Q = EXIT = QUIT  

#### Example session:

    LOAD edges.png
    FIND 100 100 50
    SHOW
    FIND 50 50 50
    SHOW
    SAVE edges_out1.jpg
    QUIT

_

2017-02-28 -- Eric Thomas
