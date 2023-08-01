// In the name of Allah

#include<iostream>
using namespace std;
int main() {

     int w[1000],v[1000],bag;
     int item;
     cin>>item;
     cin>>bag;
     //structure of the table
     int t[item+1][bag+1];

     // input of weight
     for( int i=1;i<=item;i++){

          cin>>w[i];
     }
     // input of value
    for( int i=1;i<=item;i++){

          cin>>v[i];
     }
     //for( int i=1;i<=item;i++){

        //  cout<<v[i];
     //}

     for( int i=0;i<=bag;i++){


            t[0][i]=0;
     }


    for( int i=0;i<=item;i++){

            t[i][0]=0;
     }


     for(int i=1;i<=item;i++){

          for(int j=1;j<=bag;j++){


              if(j<w[i]){
               // if the numbers are not in range
               // just print the upper previous cell
               t[i][j] = t[i-1][j];
              }
              else {
                t[i][j]= max((t[i-1][j-w[i]]+v[i]),t[i-1][j]);
              }
          }


     }

     for( int i=0;i<=item;i++){

         for( int j=0;j<=bag;j++){


               cout<<t[i][j]<<" ";
         }

         cout<<endl;
     }
}
