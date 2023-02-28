
import java.util.*;
import javax.swing.*;
 class Acount {
     int ano;
     String anm;
     int aopnbal;
    Vector<Integer>tls;
     boolean astate;
     Acount()
     {
        ano=0;
        anm=new String();
        aopnbal=0;
        astate=true;
        tls= new Vector<Integer>();

     }
     int balEnd()
     {
        int bal = aopnbal,amt=0;
        int i=0,n=tls.size();
        while(i<n){
            Integer obj= tls.get(i);
            amt= obj.intValue();
            bal+=amt;
            i++;

        }
        return bal;
     }
     void set(int no)
     {
        ano=no;
        anm= JOptionPane.showInputDialog(null, "a/c holder name");
        try
        {
            aopnbal = Integer.parseInt(JOptionPane.showInputDialog(null, "opening balance"));
        }
        catch(Exception e)
        { 
            aopnbal=4000;

        }
        astate=true;
     }
     public String toString()
     {
        String a = "\n a/c no:" + ano + "\n name:" + anm + "\n opening balance" + tls + "closing balance: " + balEnd() + "\n state :" + astate;
        return a;
     }
     void display()
     {
        JOptionPane.showMessageDialog(null, toString());
     }
     void delrecord()
     {
        astate= false; 
     }
     void deposit()
     {
          int amt=0;
          try
          {
            amt= Integer.parseInt(JOptionPane.showInputDialog(null, "deposit amount"));

          }
          catch(Exception e)
          {
            amt=-1;

          }
          if(amt<=0)
          {
            JOptionPane.showMessageDialog(null,"invalid");
            return;
          }
          tls.add(amt);
     }
     void withdrow()
     {
        int amt=0;
          try
          {
            amt= Integer.parseInt(JOptionPane.showInputDialog(null, "withdrow amount"));

          }
          catch(Exception e)
          {
            amt=-1;

          }
          if(amt<=0)
          {
            JOptionPane.showMessageDialog(null,"invalid");
            return;
          }
          int bal = balEnd() - amt;
          if(bal<=500)
          {
            JOptionPane.showMessageDialog(null, "below 500");
            return;
          }
          tls.add(-amt);
     }
     void closeAcount()
     {
      int bal = balEnd();
      tls.add(-bal);
      delrecord();
     }
    
}
class AcountList{
  LinkedList<Acount>ls;
  Acount ref;
  AcountList()
  {
    ref=null;
    ls=new LinkedList<Acount>();
  }
  int search(int no)
  {
    int i=0,n=ls.size();
    while(i<n){
      ref=ls.get(i);
      if(ref.ano==no)
         break;
      i++;

    }
    if(i==n){
      ref=null;
      return -1;

    }
    else
      return i;
  }
  void add()
  {
    int no=0;
    try
    {
      no=Integer.parseInt(JOptionPane.showInputDialog(null,"a/c no:"));
    }
    catch(Exception e)
    {

    }
    int pos=search(no);
    if(pos>=0)
    {
      JOptionPane.showMessageDialog(null,"record exit");
    }
    else
    {
      ref=new Acount();
      ref.set(no);
      ls.add(ref);
    }
  }
  void mod()
  {
    int no=0;
    try
    {
      no=Integer.parseInt(JOptionPane.showInputDialog(null,"a/c no:"));
    }
    catch(Exception e)
    {

    }
    int pos=search(no);
    if(pos==-1 || ref.astate==false)
    {
      JOptionPane.showMessageDialog(null,"record  not exit");
    }
    else
     ref.set(no);

  }
  void delet()
  {
    int no=0;
    try
    {
      no=Integer.parseInt(JOptionPane.showInputDialog(null,"a/c no:"));
    }
    catch(Exception e)
    {

    }
    int pos=search(no);
    if(pos==-1 || ref.astate==false)
    {
      JOptionPane.showMessageDialog(null,"record  not  exit");
      return;
    }
    else
     ref.closeAcount();
  }
  void transact()
  {
    int no=0;
    try
    {
      no=Integer.parseInt(JOptionPane.showInputDialog(null, "a/c no:"));
    }
    catch(Exception e)
    {

    }
    int pos=search(no);
    if(pos==-1 || ref.astate==false)
    {
      JOptionPane.showMessageDialog(null,"record  not  exit");
      return;
    }
    int opt= JOptionPane.showOptionDialog(null, "choose option", "transaction" ,JOptionPane.YES_OPTION,JOptionPane.INFORMATION_MESSAGE,null,new String[]{"depo","withd","balance","back"} ,0);
    switch(opt)
    {
      case 0:
        ref.deposit();
        break;
      case 1:
         ref.withdrow();
         break;
      case 2:
        JOptionPane.showMessageDialog(null,"Balance:" + ref.balEnd());
    }
  }

}


 // A school method based C++ program to
// check if a number is prime
#include <bits/stdc++.h>
using namespace std;

// function check whether a number
// is prime or not
bool isPrime(int n)
{
	// Corner case
	if (n <= 1)
		return false;

	// Check from 2 to square root of n
	for (int i = 2; i <= sqrt(n); i++)
		if (n % i == 0)
			return false;

	return true;
}

// Driver Code
int main()
{
	isPrime(11) ? cout << " true\n" : cout << " false\n";
	return 0;
}
