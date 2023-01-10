Instruction for adding graphics file in Code::Blocks
***************************************************************************************************

1) Copy "graphics.h" and "winbgim.h" files to "include" folder of C drive then Program Files (x86) then, Dev-Cpp and MinGW64 then include and paste it.
Or simply press windows + R and paste "C:\Program Files (x86)\Dev-Cpp\MinGW64\include" and paste "graphics.h" and "winbgim.h" files there.

2) Copy "libbgi.a" to file to "lib" folder.
Or simply, 
Press windows + R and paste "C:\Program Files (x86)\Dev-Cpp\MinGW64\lib" and paste "libbgi.a" files there.

3) Then, open Dev-C++ and find the dropdown menu with the tile of "TDM-GCC 4.9.2 64-bit Release" then, select "TDM-GCC 4.9.2 32-bit Release".

4) Go to "Tools" tab, and tap on "Complier Options", then make sure that the option with the title "Add the following commands when calling the linker:" is checked. 

5) paste "-lbgi -lgdi32 -lcomdlg32 -luuid -loleaut32 -lole32" inside that input Box. 

6) Click "Ok" 

Done...

NOTE:
1) The graphics.h will work only in the program saved in ".cpp" format.

To check the graphics.h is working or not
*****************************************************************************************************
Create a new console application in ".cpp" format and copy the codes given below, paste it in the
file you created and click "Build and Run" button or click "F9" key from your keyboard..

#include <stdio.h>
#include <graphics.h>
#include <math.h>
#include <conio.h>
#include <DOS.h>
#define ROUND(a) ((int)(a + 0.5))
void lne(int x1, int x2, int y1, int y2, char clr);

int main()
{
    int i, j, k = 0, f = 0, cnt, x1, y1, x2, y2;
    int gd = DETECT, gm;
    initgraph(&gd, &gm, "");
    cnt = getmaxx() / 2;
    for (i = 200; i <= cnt - 30;)
    {
        cleardevice();
        i += 10;
        lne(0, 250, getmaxx(), 250, GREEN);
        lne(cnt - 50, 250, cnt - 50, 180, WHITE);
        lne(cnt + 50, 250, cnt + 50, 180, WHITE);
        lne(cnt - 50, 180, cnt + 50, 180, WHITE);
        lne(cnt, 205, cnt, 235, WHITE);
        lne(cnt - 7, 250, cnt, 235, WHITE);
        lne(cnt + 7, 250, cnt, 235, WHITE);
        lne(cnt - 10, 205, cnt, 215, WHITE);
        lne(cnt + 10, 205, cnt, 215, WHITE);
        circle(cnt, 200, 5);
        circle(cnt - 25, 295, 5);
        lne(i, 255, i, 285, WHITE);
        circle(i, 250, 5);
        if (f == 0)
        {
            lne(i - 5, 300, i, 285, WHITE);
            lne(i + 7, 300, i, 285, WHITE);
            lne(i - 10, 275, i, 265, WHITE);
            lne(i + 7, 275, i, 265, WHITE);
            f = 1;
        }
        else if (f == 1)
        {
            lne(i + 5, 300, i, 285, WHITE);
            lne(i - 7, 300, i, 285, WHITE);
            lne(i + 10, 275, i, 265, WHITE);
            lne(i - 7, 275, i, 265, WHITE);
            f = 0;
        }

        delay(500);
    }
    j = 295;
    for (i = cnt - 25; i >= cnt - 40; i--)
    {
        cleardevice();
        lne(0, 250, getmaxx(), 250, GREEN);
        lne(cnt - 50, 250, cnt - 50, 180, WHITE);
        lne(cnt + 50, 250, cnt + 50, 180, WHITE);
        lne(cnt - 50, 180, cnt + 50, 180, WHITE);

        lne(cnt - k, 205, cnt - k, 235, WHITE);
        lne(cnt - 7 - k, 250, cnt - k, 235, WHITE);
        lne(cnt + 7 - k, 250, cnt - k, 235, WHITE);
        lne(cnt - 10 - k, 205, cnt - k, 215, WHITE);
        lne(cnt + 10 - k, 205, cnt - k, 215, WHITE);
        circle(cnt - k, 200, 5);
        k += 2;

        lne(cnt - 25, 255, cnt - 25, 285, WHITE);
        circle(cnt - 25, 250, 5);
        lne(cnt - 20, 300, cnt - 25, 285, WHITE);
        lne(cnt - 32, 300, cnt - 25, 285, WHITE);
        lne(cnt - 20, 275, cnt - 25, 265, WHITE);
        lne(cnt - 32, 275, cnt - 25, 265, WHITE);

        circle(i, j, 5);
        j -= 4;
        delay(100);
    }
    getch();
}

void lne(int x1, int y1, int x2, int y2, char clr)
{
    int dx = x2 - x1, dy = y2 - y1, k, steps;
    float xIncrement, yIncrement, x = x1, y = y1;
    if (abs(dx) > abs(dy))
        steps = abs(dx);
    else
        steps = abs(dy);
    xIncrement = dx / (float)steps;
    yIncrement = dy / (float)steps;
    putpixel(ROUND(x), ROUND(y), clr);
    for (k = 0; k < steps; k++)
    {
        x += xIncrement;
        y += yIncrement;
        putpixel(ROUND(x), ROUND(y), clr);
    }
}
// Enjoy...! :-)
// By Purna Shrestha.
