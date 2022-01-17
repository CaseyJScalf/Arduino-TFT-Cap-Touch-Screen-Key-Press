//This example implements a simple sliding On/Off button. The example
// demonstrates drawing and touch operations.
//
//Thanks to Adafruit forums member Asteroid for the original sketch!
//
#include <Adafruit_GFX.h>
#include <SPI.h>
#include <Wire.h>
#include <Adafruit_ILI9341.h>
#include <Adafruit_FT6206.h>

// Key Stuff
#include "Keyboard.h"
int buttonStateA = 0;
char specialKeyLeft = KEY_LEFT_ARROW;
char specialKeyRight = KEY_RIGHT_ARROW;
#define keyPressDelay 120

// The FT6206 uses hardware I2C (SCL/SDA)
Adafruit_FT6206 ts = Adafruit_FT6206();

#define TFT_CS 10
#define TFT_DC 9
Adafruit_ILI9341 tft = Adafruit_ILI9341(TFT_CS, TFT_DC);

#define WIDTH 320
#define HEIGHT 240

#define FRAME_W 70
#define FRAME_H 70

#define button_1_X 10
#define button_1_Y 10
#define button_1_W FRAME_W
#define button_1_H FRAME_H

#define button_2_X 90
#define button_2_Y 10
#define button_2_W FRAME_W
#define button_2_H FRAME_H

#define button_3_X 170
#define button_3_Y 10
#define button_3_W FRAME_W
#define button_3_H FRAME_H

#define button_4_X 250
#define button_4_Y 10
#define button_4_W FRAME_W
#define button_4_H FRAME_H

#define button_5_X 70
#define button_5_Y 120
#define button_5_W 90
#define button_5_H 60

#define button_6_X 170
#define button_6_Y 120
#define button_6_W 90
#define button_6_H 60

void button_1()
{
  tft.fillRect(button_1_X, button_1_Y, button_1_W , button_1_H, ILI9341_BLUE);

  tft.setCursor(button_1_X + (button_1_W/2.2) , button_1_Y + (button_1_H / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println('G');
}

void button_2()
{
  tft.fillRect(button_2_X, button_2_Y, button_2_W , button_2_W, ILI9341_BLUE);

  tft.setCursor(button_2_X + (button_2_W/2.2) , button_2_Y + (button_2_W / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println('A');
}

void button_3()
{
  tft.fillRect(button_3_X, button_3_Y, button_3_W , button_3_W, ILI9341_BLUE);

  tft.setCursor(button_3_X + (button_3_W/2.2) , button_3_Y + (button_3_W / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println('T');
}

void button_4()
{
  tft.fillRect(button_4_X, button_4_Y, button_4_W , button_4_W, ILI9341_BLUE);

  tft.setCursor(button_4_X + (button_4_W/2.2) , button_4_Y + (button_4_W / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println('C');
}

void button_5()
{
  tft.fillRect(button_5_X, button_5_Y, button_5_W , button_5_W, ILI9341_BLUE);

  tft.setCursor(button_5_X + (button_5_W/2.2) , button_5_Y + (button_5_W / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println("<<<");
}

void button_6()
{
  tft.fillRect(button_6_X, button_6_Y, button_6_W , button_6_W, ILI9341_BLUE);

  tft.setCursor(button_6_X + (button_6_W/4.5) , button_6_Y + (button_6_W / 2.2));
  tft.setTextColor(ILI9341_WHITE);
  tft.setTextSize(2);
  tft.println(">>>");
}

////////////////////////////////////////////////////////////////////////////////////////////////////

void setup(void)
{
  Serial.begin(9600);
  tft.begin();

  if (!ts.begin(40)) {
    //    Serial.println("Unable to start touchscreen.");
  }
  else {
    //    Serial.println("Touchscreen started.");
  }

  // Set background color
  tft.fillScreen(ILI9341_BLACK);
  tft.setCursor(0, 0);

  // origin = left,top landscape (USB left upper)
  tft.setRotation(1);

  // Run once to set rect on screen initially
  button_1();
  button_2();
  button_3();
  button_4();
  button_5();
  button_6();

}

////////////////////////////////////////////////////////////////////////////////////////////////////

void loop()
{
  // See if there's any  touch data for us
  if (ts.touched())
  {
    // Retrieve a point
    TS_Point p = ts.getPoint();

    // rotate coordinate system
    // flip it around to match the screen.
    p.x = map(p.x, 0, 240, 240, 0);
    p.y = map(p.y, 0, 320, 320, 0);
    int y = tft.height() - p.x;
    int x = p.y;

    // button_1
    if ((x > button_1_X) && (x < (button_1_X + button_1_W))) {
      if ((y > button_1_Y) && (y <= (button_1_Y + button_1_H))) {
        button_1();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press('G');
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }

    // button_2
    if ((x > button_2_X) && (x < (button_2_X + button_2_W))) {
      if ((y > button_2_Y) && (y <= (button_2_Y + button_2_H))) {
        button_2();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press('A');
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }

    // button_3
    if ((x > button_3_X) && (x < (button_3_X + button_3_W))) {
      if ((y > button_3_Y) && (y <= (button_3_Y + button_3_H))) {
        button_4();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press('T');
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }

    // button_4
    if ((x > button_4_X) && (x < (button_4_X + button_4_W))) {
      if ((y > button_4_Y) && (y <= (button_4_Y + button_4_H))) {
        button_4();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press('C');
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }

    // button_5
    if ((x > button_5_X) && (x < (button_5_X + button_5_W))) {
      if ((y > button_5_Y) && (y <= (button_5_Y + button_5_H))) {
        button_5();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press(specialKeyLeft);
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }

    // button_6
    if ((x > button_6_X) && (x < (button_6_X + button_6_W))) {
      if ((y > button_6_Y) && (y <= (button_6_Y + button_6_H))) {
        button_6();
        Keyboard.begin();
        // What 'key' should the button send?
        Keyboard.press(specialKeyRight);
        delay(keyPressDelay);
        Keyboard.releaseAll();
        Keyboard.end();
      }
    }


  } // End if touched

} // End Loop
