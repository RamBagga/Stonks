#include <bits/stdc++.h>
#include<dos.h>
#include <windows.h>
using namespace std;
int uid=0;
struct stock{
    string name;
    int price;
    int quantity;
};
class user
{
  string email,first_name,middle_name,last_name;
  string password,temppass;
  int mobile_number,age,flag=0;
  long portfoliovalue;
  string names[4]={"HDFC Bank","Reliance","TCS","Infosys"};
  int prices[4];
  public:
      long balance=0;
      stock owned[4];
      user()
      {
       for(int i=0;i<4;i++)
       {
         owned[i].name=names[i];
         owned[i].price=0;
         owned[i].quantity=0;
       }
      }
      void setemail()
      {
       cout << "\n\nEnter E-mail address :";
       cin>>email;
      }
      void setfname()
      {
          cout<<"\n\nEnter your first name:";
          cin>>first_name;
      }
      void setlname()
      {
          cout<<"\n\nEnter your last name:";
          cin>>last_name;
      }
      void setpass()
      {
          cout<<"\n\nSet a password:";
          cin>>temppass;
      }
      void setage()
      {
          cout<<"\n\nInput your age:";
          cin>>age;
      }
      bool comppass()
      {
          string s;
          cout<<"Input your password again:";
          cin>>s;
          if(s==temppass)
            {
                password=temppass;
                return true;
            }
          else
            return false;
      }
      string getemail()
      {
          return email;
      }
      string getpass()
      {
          return password;
      }
      string getfname()
      {
          return first_name;
      }
      string getlname()
      {
          return last_name;
      }
      long getbalance()
      {
          return balance;
      }
      long getportvalue()
      {
          long temp=0;
          for(int i=0;i<4;i++)
          {
              temp+=(owned[i].price*owned[i].quantity);
          }
          temp+=balance;
          return temp;
      }
};
vector<user> id(10000);
COORD coord= {0,0};
void gotoxy(int x,int y)
{
    coord.X=x;
    coord.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),coord);
}
void delay(unsigned int mseconds)
{
    clock_t goal = mseconds + clock();
    while (goal > clock());
}
void loading ()
{
    system("cls");
    for(int j=0;j<4;j++)
    {
    gotoxy(50,15);
    for(int i=0;i<4;i++)
    {
        cout<<"."<<" ";
        delay(120);
    }
    system("cls");
    }
}
void reg()
{
    loading();
    id[uid].setemail();
    id[uid].setfname();
    id[uid].setlname();
    id[uid].setage();
    id[uid].setpass();
    if(id[uid].comppass())
    {
      cout << "\n\nYour account has been successfully created.";

      uid++;
      delay(4000);
    }
    else
    {
      cout << "\n\nPasswords don't match !!";
      delay(4000);
      reg();
    }
}
void mainmenu();
void stockprices(int i);
void portfolio(int i);
void buy(int i);
void addmoney(int i);
void loginpage(int i)
{
    loading();
    while(1)
    {
        cout<<"\n\n\t\t\t\tSTOCKER";
        cout<<"\n\nWelcome ";
        cout<<id[i].getfname()<<" ";
        cout<<id[i].getlname();
        cout<<"\n\n\t 1.Check your portfolio";
        cout<<"\n\n\t 2.Buy/Sell";
        cout<<"\n\n\t 3.Add/Withdraw INR";
        cout<<"\n\n\t 4.Logout";
        char choice;
        cout<<"\n\n\t Input your choice:";
        cin>>choice;
        switch(choice)
        {
        case '1':
            portfolio(i);
            break;
        case '2':
            buy(i);
            break;
        case '3':
            addmoney(i);
            break;
        case '4':
            mainmenu();
            break;
        }
    }
}
void addmoney(int i)
{
        loading();
        cout<<"\n\t\t\t\tStocker";
        cout<<"\n\n\t\t1.Deposit";
        cout<<"\n\n\t\t2.Withdraw\n\n\t\t3.Go back\n\n\t\tInput:";
        char ch;
        cin>>ch;
        switch(ch)
        {
        case '1':
                {cout<<"\n\n\t\tEnter amount to be added \n";

            cout<<"\t\tfrom your UPI account linked to your mobile number:";
            int add;
            cin>>add;
            id[i].balance+=add;
            cout<<"\n\n\n\t\tSuccessfully Added!!";
            delay(2000);
            break;
                }
        case '2':
            {
                cout<<"\n\n\n\t\tInput money to be withdrawn to your bank account linked to your registered";
                cout<<"\n\t\tmobile number:";
                int withdraw;
                cin>>withdraw;
                if(withdraw>id[i].balance)
                {
                    cout<<"\n\n\t\tInsufficient balance!!";
                    delay(2000);
                    addmoney(i);
                }
                id[i].balance-=withdraw;
                cout<<"\n\n\t\tSuccessfully Withdrawn!!";
                delay(2000);
                break;
            }
        case '3':
            {
                loginpage(i);
                break;
            }
        }
        loginpage(i);
}
int counter=0;
void buy(int i)
{
    loading();
    while(1)
    {
    gotoxy(10,0);
    cout<<"S.No";
    gotoxy(20,0);
    cout<<"Name";
    gotoxy(40,0);
    cout<<"Price";
    srand(time(0));
    int startprice[4]={1500,1000,2500,3000};
    if(counter%2==0)
    {
    for(int j=0;j<4;j++)
    {
        id[i].owned[j].price=startprice[j]+(rand()%100);
    }
    }
    else{
    for(int j=0;j<4;j++)
    {
        id[i].owned[j].price=startprice[j]-(rand()%100);
    }
    }
    counter++;
    int row=3;
    for(int j=0;j<4;j++)
    {
        gotoxy(10,row);
        cout<<j+1;
        gotoxy(20,row);
        cout<<id[i].owned[j].name;
        gotoxy(40,row);
        cout<<id[i].owned[j].price;
        row=row+2;
    }
    cout<<"\n\n\t\tPress 1 to buy!";
    cout<<"\n\n\t\tPress 2 to sell!";
    cout<<"\n\n\t\tPress 3 to refresh prices";
    cout<<"\n\n\t\tPress 4 to go back";
    cout<<"\n\n\t\tInput:";
    char ch;
    cin>>ch;
    switch(ch)
    {
    case '1':
        {
            int sno,quan;
            cout<<"\n\n\t\tInput S.no of the stock you want to buy:";
            cin>>sno;
            cout<<"\n\n\t\tInput quantity you want to buy:";
            cin>>quan;
            if((id[i].owned[sno-1].price*quan)>id[i].balance)
            {
                cout<<"\n\n\t\tInsufficient balance!!";
                delay(5000);
                buy(i);
            }
            cout<<"\n\n\t\tSuccessfully completed!!";
            id[i].owned[sno-1].quantity+=quan;
            id[i].balance-=(id[i].owned[sno-1].price*quan);
            delay(5000);
            break;
        }
    case '2':
        {
            int sno,quan;
            cout<<"\n\n\t\tInput S.no of the stock you want to sell:";
            cin>>sno;
            cout<<"\n\n\t\tInput quantity you want to sell:";
            cin>>quan;
            if(id[i].owned[sno-1].quantity<quan)
            {
                cout<<"\n\n\t\tInsufficient stocks owned!!";
                delay(5000);
                buy(i);
            }
            cout<<"\n\n\t\tSuccessfully completed!!";
            id[i].owned[sno-1].quantity-=quan;
            id[i].balance+=(id[i].owned[sno-1].price*quan);
            delay(5000);
            break;
        }
    case '3':
        {
            buy(i);
            break;
        }
    case '4':
        {
            loginpage(i);
            break;
        }
    }
    loginpage(i);
    }
}
void portfolio(int i)
{
    loading();
    while(1)
    {
    gotoxy(40,5);
    cout<<"Total Portfolio value";
    gotoxy(38,6);
    cout<<"_______";
    gotoxy(38,7);
    cout<<id[i].getportvalue();
    int r=13,c=10;
    gotoxy(15,10);
    cout<<"Name";
    gotoxy(30,10);
    cout<<"Price";
    gotoxy(45,10);
    cout<<"Quantity";
    gotoxy(60,10);
    cout<<"Amount owned";
    for(int j=0;j<4;j++)
    {
        c=15;
        gotoxy(c,r);
        cout<<id[i].owned[j].name;
        c+=15;
        gotoxy(c,r);
        cout<<id[i].owned[j].price;
        c+=15;
        gotoxy(c,r);
        cout<<id[i].owned[j].quantity;
        c+=15;
        gotoxy(c,r);
        cout<<(id[i].owned[j].price)*(id[i].owned[j].quantity);
        ++r;
    }
    gotoxy(10,r);
    cout<<"INR balance: "<< id[i].getbalance();
    cout<<"\n\nPress any key to go back!";
    char a;
    cin>>a;
    loginpage(i);
    }
}
void log()
{
    loading();
    string em,pass;
    cout<<"\n\n\t\t\t\tSTOCKER";
    gotoxy(40,15);
    cout<<"Email:";
    gotoxy(40,18);
    cout<<"Password:";
    gotoxy(50,15);
    cin>>em;
    gotoxy(50,18);
    cin>>pass;
    if(uid==0)
    {
        cout<<"\n\n\n\t\tNo users registered!!";
        delay(4000);
    }
    else{
    for(int i=0;i<id.size();i++)
    {
        if(id[i].getemail()==em)
        {
            if(id[i].getpass()==pass)
            {
                    loginpage(i);
                    break;
            }
            else{
                gotoxy(40,20);
            cout<<"Wrong Password!!!"<<endl;
            delay(4000);
            log();
            }
        }
        if(i==id.size()-1)
        {
            gotoxy(40,20);
            cout<<"Email not registered"<<endl;
            delay(4000);
        }
    }
    }
}
void mainmenu()
{
    while(1)
    {
    system("COLOR 7D");
    system("cls");
    cout<<"\t\t\t\tSTOCKER";
    cout<<"\n\n\tWelcome ";
    cout<<"\n\n\t\t1.Login";
    cout<<"\n\n\t\t2.Register";
    cout<<"\n\n\t\t3.Exit";
    char choice;
    cout<<"\n\n\t\tInput:";
    cin>>choice;
    switch(choice)
    {
    case '1':
        log();
        break;
    case '2':
        reg();
        break;
    case '3':
        exit(1);
        break;
    }
    }
}
int main()
{
    system("COLOR 7D");
    mainmenu();
	return 0;
}
