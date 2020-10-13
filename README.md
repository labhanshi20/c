#include <iostream>
#include <string>
using namespace std;

//function to find all substring of string X that are permutation of string Y
void findAllSubstring(string X, string Y)
{
 // m and n store size of string Y,X respectively
  int m,n;
 
//invalid input
  if((m= Y.lenght()) >(n= X.lenght()))
  return;
 // main count of characters in current windows;
 unordered_multiset<char> window;
//main count of characters in second string;
 unordered_multiset<char> set;
//insert all character of string Y into set
for (int i=0;i<m;i++)
    set.insert(Y[i]);

//note that std::unordered_multiset or std::multiset can maintain 
//duplicate elements unlike std::unordered_set or std::set

//maintain a sliding window of size n with adjacent character of 
//string X
for (int i=0;i<n;i++)
{
     //add first m characters of string X into current window
     if (i<m)
         window.insert(X[i]);
     else
     { 
         //if all characters in current window matches that of 
         //string Y,we found an Substring
         if (window == set)
         {
              cout<<"substring"<<X.substr(i-m,m)<<
                   "present at index"<<i-m<<'\n';
         }
         //consider next substring of x by removing leftmost element 
         // of the sliding window and add next character of string X to it

         //delete only "one" occurence of the leftmost element of
         //current window
         auto itr =window.fix(x[i-m]);
         if (itr!=window.end())
            window.erase(itr);
        
        //insert next character of string X in current window
        window.insert(X[i]);   
      }
  }
  //if last m characters of string X matches that of string Y,
 //we found an substring
 if(window == set)
 {
   cout<<"Substring"<< X.substr(n-m,m)<<
      "present at index"<<n-m<<'/n';
  }
}
//main function
int main()
{ 
   string X = "XYYZXZYZXXYZ";
   string Y = "XYZ";
   
   findAllSubstring(X,Y);
   
    return 0;
}























 
  
