# Encryption-Decryption

#include<iostream>
#include<fstream>
#include<cstring>
using namespace std;
char shift_func(char letter,int key)
{
	int init=int(letter);
	int shifted=init;
	for(int i=0;i<key;i++)
	{
		if(shifted<126)
		{
			shifted=shifted+1;
		}
		else
		{
		shifted=(shifted+33)-126;
        }
	}
	char result=shifted;
	return result;
}
int main()
{
	ifstream i;
	ofstream o;
	string line;
	int k;
					
	cout<<"Enter encryption key: ";
	cin>>k;
		int shift=k%66;
	
	i.open("Assignment 1_Plaintext.txt");
			o.open("Encrypted.txt",ios::out | ios::app);

	while(getline(i, line))
	{		
	char newstring[line.length()];
	if(line[0]>32&&line[0]<127)
	{
	for(int i=0; i<line.length(); i++)
		{
		    int x=line[i];
			newstring[i]=shift_func(x,shift);
		}				
		cout<<newstring<<endl;
		o<<newstring;
		o<<endl;
	}
	else{
		cout<<endl;
		o<<endl;
	}
    }
    		//o.close();	
    o.close();
    i.close();
}
