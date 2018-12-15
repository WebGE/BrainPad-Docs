# Display
---
The BrainPad display is an output device. The BrainPad has commands allowing you to display numbers and text and draw simple pictures and shapes. These shapes including points, lines, circles and rectangles. All display commands use pixels (screen dots) as units.

Display commands in this section only change the memory buffer of the display and are not seen until you also call the BrainPad.Display.RefreshScreen() method.

## Display Methods
 
* `BrainPad.Display.Height` - returns the BrainPad display's height in pixels (64). 

* `BrainPad.Display.Width` - returns the BrainPad display's width in pixels (128).
 
* `BrainPad.Display.DrawSmallNumber(int x, int y, long number)` - Displays a number of type long in small text at the given x and y coordinates. [Example: `BrainPad.Display.DrawSmallNumber(10, 20, 52)`]

* `BrainPad.Display.DrawSmallNumber(int x, int y, double number)` - Displays a number of type double in small text at the given x and y coordinates.

* `BrainPad.Display.DrawNumber(int x, int y, long number)` - Displays a number of type long in large text at the given x and y coordinates.

* `BrainPad.Display.DrawNumber(int x, int y, double number)` - Displays a number of type double in large text at the given x and y coordinates. 

* `BrainPad.Display.DrawSmallText(int x, int y, string text)` - Displays a string in small text at the given x and y coordinates. [Example: `BrainPad.Display.DrawSmallText(20, 20, "Hello")`]  

* `BrainPad.Display.DrawText(int x, int y, string text)` - Displays a string in small text at the given x and y coordinates.

* `BrainPad.Display.DrawScaledText(int x, int y, string text, int HScale, int VScale)` - Displays text that can be made larger. Text size is multiplied by HScale to determing horizontal size and VScale to determine vertical size. For example setting HScale to two will print text that is twice as wide.
 
* `BrainPad.Display.CreatePicture(int width, int height, byte[] data)` - Used to store a picture for the DrawPicture commands.

* `BrainPad.Display.CreateScaledPicture(int width, int height, byte[] data, int scale)` - Used to store a picture that will be displayed larger by a factor of scale. For example setting scale to two will display the picture at twice its original size.
 
* `BrainPad.Display.DrawCircle(int x, int y, int r)` - Draws a circle of radius r with the center located at the given x and y coordinates.  

* `BrainPad.Display.DrawRectangle(int x, int y, int width, int height)` - Draws a box at the given x and y coordinates.

* `BrainPad.Display.DrawFilledRectangle(int x, int y, int width, int height)` - Draws a filled box at the given x and y coordinates.   

* `BrainPad.Display.DrawLine(int x0, int y0, int x1, int y1)` - Draws a line from (x0, y0) to (x1, y1).  

* `BrainPad.Display.DrawPoint(int x, int y)` - Turns on a single pixel at the given x and y coordinates.
 
* `BrainPad.Display.DrawPicture(int x, int y, Picture picture)` - Draws the given picture at the given x and y coordinates.

* `BrainPad.Display.DrawPictureFlippedHorizontally(int x, int y, Picture picture)` - Flips the given picture horizontally and draws it at the given x and y coordinates.

* `BrainPad.Display.DrawPictureFlippedVertically(int x, int y, Picture picture)` - Flips the given picture vertically and draws it at the given x and y coordinates. 

* `BrainPad.Display.DrawPictureRotated180Degrees(int x, int y, Picture picture)` - Rotates the given picture 180 degrees and draws it at the given x and y coordinates. 

* `BrainPad.Display.DrawPictureRotated270Degrees(int x, int y, Picture picture)` - Rotates the given picture 270 degrees clockwise and draws it at the given x and y coordinates.

* `BrainPad.Display.DrawPictureRotated90Degrees(int x, int y, Picture picture)` - Rotates the given picture 90 degrees clockwise and draws it at the given x and y coordinates.
                         
* `BrainPad.Display.ClearPartOfScreen(int x, int y, int width, int height)` - Clears a rectangular section of the display where x and y are the top left corner of a rectangle of given width and height.
 
* `BrainPad.Display.ClearPoint(int x, int y)` - Clears the pixel located at the given x and y coordinates.  

* `BrainPad.Display.ClearScreen()` - Clears the entire screen buffer. 

* `BrainPad.Display.InvertColors(bool invert)` - Inverts each pixel on the entire screen. Pixels that are on will be turned off, and pixels that are off will be turned on.

* `BrainPad.Display.RefreshScreen()` - Writes the entire display buffer to the display. Used to show what has been drawn to the screen buffer on the display.
   
## Display Sample Code
The following program draws a point, line, rectangle, circle and a picture of a heart in two sizes.

To try it, [start a C# new project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    BrainPad.Display.DrawPoint(64, 32);
    BrainPad.Display.DrawLine(0, 52, 127, 52);
    BrainPad.Display.DrawRectangle(48, 20, 32, 24);
    BrainPad.Display.DrawCircle(64, 32, 20);

    byte[] pictureData = new byte[]
    { 0, 0, 1, 0, 0 ,0, 1, 0, 0,
      0, 1, 0, 1, 0, 1, 0, 1, 0,
      1, 0, 0, 0, 1, 0, 0, 0, 1,
      1, 0, 0, 0, 1, 0, 0, 0, 1,
      1, 0, 0, 0, 0, 0, 0, 0, 1,
      0, 1, 0, 0, 0, 0, 0, 1, 0,
      0, 0, 1, 0, 0, 0, 1, 0, 0,
      0, 0, 0, 1, 0, 1, 0, 0, 0,
      0, 0, 0, 0, 1, 0, 0, 0, 0,
    };

    BrainPad.Display.DrawPicture(0, 0, BrainPad.Display.CreatePicture(9, 9, pictureData));
    BrainPad.Display.DrawPicture(10, 10, BrainPad.Display.CreateScaledPicture(9, 9, pictureData, 2));
    BrainPad.Display.RefreshScreen();
}
```
