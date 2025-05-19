#include <iostream>
#include<math.h>
#include <windows.h>
#include <GL/glut.h>

void star(double x, double y, double s){

        double x1 = s*4.9 +x, y1 = y;
        double x2 = s*10+x, y2 = s*15.3+y;
        double x3 = s*12+x, y3 = s*9.4+y;
        double x4 = s*18.1+x, y4 = s*9.4+y;
        double x5 = s*15.1+x, y5 = y;
        double x6 = s*1.9+x, y6 = s*9.4+y;
        double x7 = s*12+x, y7 = s*9.4+y;

    /// Half triangle for a star
    {
        glColor3ub(115, 194, 251);
        glBegin(GL_POLYGON);
        glVertex2f(x1,y1);
        glVertex2f(x2,y2);
        glVertex2f(x3,y3);
        glVertex2f(x4,y4);
        glEnd();
    }
    /// Second Half of the star triangle
    {
        glColor3ub(115, 194, 251);
        glBegin(GL_POLYGON);
        glVertex2f(x5,y5);
        glVertex2f(x6,y6);
        glVertex2f(x7,y7);
        glEnd();
    }

}

void flag()
{
    glClear(GL_COLOR_BUFFER_BIT);

    ///For bottom Blue
    {
        glColor3ub(115, 194, 251);
        glBegin(GL_POLYGON);
        glVertex2f(0,0);
        glVertex2f(1440,0);
        glVertex2f(1440,240);
        glVertex2f(0,240);
        glEnd();
    }

     ///For middle White
    {
        glColor3ub(255, 255, 255);
        glBegin(GL_POLYGON);
        glVertex2f(0,240);
        glVertex2f(1440,240);
        glVertex2f(1440,480);
        glVertex2f(0,480);
        glEnd();
    }

    ///For top Blue
    {
        glColor3ub(115, 194, 251);
        glBegin(GL_POLYGON);
        glVertex2f(0,480);
        glVertex2f(1440,480);
        glVertex2f(1440,720);
        glVertex2f(0,720);
        glEnd();
    }

    ///for 4 stars
    double a[2]={480, 880}, b[2]={20*(14.5+(9/13)), 20*(20.5+(9/13))};
    for (int i=0; i<2; i++)
        for (int j=0; j<2; j++)
            star(a[i], b[j], 2);
    ///for mid star
    star((a[0]+a[1])/2, (b[0]+b[1])/2, 2);

    glFlush();
}

int main(int argc, char *argv[])
{
    glutInit(&argc, argv);
    double w=1440, h=720;
    glutInitWindowSize(w,h);
    glutInitWindowPosition(0,0);
    glutInitDisplayMode(GLUT_RGBA | GLUT_SINGLE);

    glutCreateWindow("Flag of Honduras");
    glOrtho(0,w,0,h,-1,1);
    glutDisplayFunc(flag);
    glutMainLoop();

    return EXIT_SUCCESS;
}
