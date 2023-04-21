# Write a function to compute the distance between two points and use it to develop another function that will compute the area of the triangle whose vertices are A(x1,y1), B(x2, y2), and C(x3, y3). Use these functions to develop a function which returns a value 1 if the point (x, y) lines inside the triangle ABC, otherwise a value 0
The below code is ©Soumya_Chakraborty 
   
    #include<stdio.h>
    #include<math.h>
These two header files are included for standard input/output operations and math functions.

    void res(float x1, float y1, float x2, float y2, float x3, float y3,
              float x, float y, float *area, int *flag); 
This is a function prototype for res function that takes the coordinates of the triangle's vertices and the point, and two pointers to store the area of the triangle and the result of the position check
    
    float distance(float x1, float y1, float x2, float y2);
This is a function prototype for distance function that takes the coordinates of two points and returns their distance
    
    float cal_area(float a, float b, float c);
This is a function prototype for cal_area function that takes the three sides of a triangle and returns its area
    
    int position(float area, float A, float B, float C);
This is a function prototype for position function that takes the area of the triangle and the areas of three sub-triangles and returns 1 if the point is inside or on the edge of the triangle and 0 otherwise

    void main() //The main function of the program.
    {
    
    float x1, y1, x2, y2, x3, y3, x, y; // Declare variables to store the coordinates of the triangle's vertices and the point
    float area=0; // Declare and initialize a variable to store the area of the triangle
    int flag=0;// Declare and initialize a variable to store the result of the position check

    printf("Enter the values of (x1,y1): ");
    scanf("%f%f", &x1, &y1);

    printf("Enter the values of (x2,y2): ");
    scanf("%f%f", &x2, &y2);

    printf("Enter the values of (x3,y3): ");
    scanf("%f%f", &x3, &y3);

    printf("Enter point values (x,y): ");
    scanf("%f%f", &x, &y);
Taking input from the user for the coordinates of the three points and the point to be checked.

    res(x1, y1, x2, y2, x3, y3, x, y, &area, &flag);
Calling the res() function with the coordinates of the three points and the point to be checked as arguments.

    printf("\n Area of triangle: %.2f\n", area);
Printing the area of the triangle formed by the three given points

    if (flag==1) // If the flag variable is equal to 1, which means the point is inside or on the edge of the triangle
        printf("\nPoint(%.2f, %.2f) lies inside the triangle.",x,y);
        // Print a message to the screen with the coordinates of the point and say that it lies inside the triangle
    else 
Otherwise, if the flag variable is not equal to 1, which means the point is outside the triangle
       
       printf("\nPoint(%.2f, %.2f) lies outside the triangle.",x,y);
Print a message to the screen with the coordinates of the point and say that it lies outside the triangle.

    }
    void res(float x1, float y1, float x2, float y2, float x3, float y3,
         float x, float y, float *area, int *flag)
The res() function takes the coordinates of the three points and the point to be checked as input and calculates the area of the triangle formed by the three given points and checks whether the given point lies inside or outside the triangle.
     
    {
    float a, b, c, d, e, f, A, B, C ;
Declaration of variables used in the res() function.

    a = distance(x1,y1,x2,y2); //Calculate side a using distance function
    b = distance(x2,y2,x3,y3); //Calculate side b using distance function
    c = distance(x3,y3,x1,y1); //Calculate side c using distance function
Calculating the length of sides of the triangle formed by the three given points

    *area = cal_area(a,b,c);
Calculating the area of the triangle formed by the three given points.

    d = distance(x1,y1,x,y); //Calculate side d using distance function
    e = distance(x2,y2,x,y); //Calculate side e using distance function
    f = distance(x3,y3,x,y); //Calculate side f using distance function
Calculating the distance of the given point from the

    A = cal_area(d,e,a); // Calculate the area of sub-triangle ADE using cal_area function
    B = cal_area(e,b,f); // Calculate the area of sub-triangle BEF using cal_area function
    C = cal_area(f,c,d); // Calculate the area of sub-triangle CFD using cal_area function

    *flag = position(*area, A, B, C);
Check if the point is inside the triangle using position function and store the result in *flag
    
    }
    float distance(float x1, float y1, float x2, float y2)
This function calculates the distance between two points given their coordinates
    
    {
    return (sqrt(pow((x2-x1),2)+pow((y2-y1),2))); 
Return the distance using the formula d = sqrt((x2-x1)^2+(y2-y1)^2)
     
    }
      float cal_area(float a, float b, float c)
This function calculates the area of a triangle given its three sides
    
    { 
        float S,ar; // Declare two variables to store the semi-perimeter and the area

    S = (a+b+c)/2.0; // Calculate the semi-perimeter using the formula S = (a+b+c)/2

    ar = (sqrt(S*(S-a)*(S-b)*(S-c))); // Calculate the area using Heron's formula ar = sqrt(S*(S-a)*(S-b)*(S-c))
    return (ar); // Return the area
    }
     int position(float area, float A, float B, float C) 
This function checks if a point is inside a triangle given its coordinates and the coordinates of the triangle's vertices
    
    {
        float res;
Declare a variable to store the difference between the area of the triangle and the sum of the areas of three sub-triangles

    res = area-(A+B+C); // Calculate the difference

    if(res==0 || res<0.0001) // If the difference is zero or very small
    {
        return(1); // Return 1 to indicate that the point is inside or on the edge of the triangle
    }
    else // Otherwise
    {
        return(0); // Return 0 to indicate that the point is outside the triangle
       }
    }
The above code is ©Soumya_Chakraborty
