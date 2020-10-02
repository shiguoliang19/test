## 相机模型

相机模型：在真实世界里，所有的物体都是三维的。但是，这些三维物体在计算机世界中却必须以二维平面物体的形式表现出来。

 　1. 将相机置于三角架上，让它对准三维景物（视点变换，Viewing Transformation）。
 　2. 将三维物体放在适当的位置（模型变换，Modeling Transformation）。
 　3. 选择相机镜头并调焦，使三维物体投影在二维胶片上（投影变换，Projection Transformation）。
 　4. 
     决定二维像片的大小（视口变换，Viewport Transformation）。


![4b46937bgc483608f9cec&690](C:\Users\shiguoliang\Desktop\assets\4b46937bgc483608f9cec&690.jpg)

## 三维图形显示流程

1. 视点变换。视点变换是在视点坐标系中进行的。相当于放置相机的位置。
   对应MatrixManipulator类

2. 模型变换。模型变换是在世界坐标系中进行的。相当于布景。在这个坐标系中，
   可以对物体实施平移glTranslatef()、旋转glRotatef()和放大缩小glScalef()。
   对应PositionAttitudeTransform类 和 MatrixTransform类。

3. 投影变换。投影变换类似于选择相机的镜头。本例中调用了一个透视投影函数glFrustum()，
   在调用它之前先要用glMatrixMode()说明当前矩阵方式是投影GL_PROJECTION。

   3.1正射投影

   ```c++
   void glOrtho(GLdouble left,GLdouble right,GLdouble bottom,GLdouble top,GLdouble near,GLdouble far)//openGL
   ```

   ![4b46937bgc48368aa04fe&690](C:\Users\shiguoliang\Desktop\assets\4b46937bgc48368aa04fe&690.jpg)

   3.2透视投影

   ```c++
   void glFrustum(GLdouble left,GLdouble Right,GLdouble bottom,GLdouble top,GLdouble near,GLdouble far);
   ```

   

   

![4b46937bgc483680df268&690](C:\Users\shiguoliang\Desktop\assets\4b46937bgc483680df268&690-1589700293324.jpg)

```c++
void gluPerspective(GLdouble fovy,GLdouble aspect,GLdouble zNear, GLdouble zFar);//openGL
```

![4b46937bgc48367697271&690](C:\Users\shiguoliang\Desktop\assets\4b46937bgc48367697271&690.jpg)



![4b46937bgc4836938f498&690](C:\Users\shiguoliang\Desktop\assets\4b46937bgc4836938f498&690.jpg)

4. 视口变换。视口变换就是将视景体内投影的物体显示在二维的视口平面上。通常，都调用函数glViewport()来定义一个视口。

   ```c++
   void glViewport(GLint x,GLint y,GLsizei width, GLsizei height);//openGL
   ```

   