//***************************************************************
// HEADER FILE USED IN PROJECT
//***************************************************************

#include<iostream>
#include<string.h>
#include<process.h>
#include<stdio.h>
#include<fstream>
#include<stdlib.h>
using namespace std;

//***************************************************************
// CLASS - ITEM
//****************************************************************
struct x{
int pcode,price,quan,cc;
char pname[20],sname[20];
}x;

class item
{
 public:
 int pcode,price,instock,quan;
 char pname[20],sname[20];
 void enterdata()
 {
 cout<<"\n\t\t ENTER THE DETAILS OF PRODUCT : ";
 cout<<"\n\t\t           ENTER PRODUCT CODE : \t";
 cin>>pcode;
 cout<<"\n\t\t         ENTER NAME OF SCHOOL : \t";
 cin>>sname;
 cout<<"\n\t\t        ENTER NAME OF PRODUCT : \t";
 cin>>pname;
 cout<<"\n\t\t                  ENTER PRICE : \t"<<"Rs.";
 cin>>price;
 cout<<"\n\t  ENTER QUANTITY OF PRODUCT (INSTOCK) : \t";
 cin>>instock;
 cout<<endl<<endl;
 }
 void displaydata()
 {
 cout<<"\n\t\t    PRODUCT CODE : \t";
 cout<<pcode;
 cout<<"\n\t\t  NAME OF SCHOOL : \t";
 cout<<sname;
 cout<<"\n\t\t NAME OF PRODUCT : \t";
 cout<<pname;
 cout<<"\n\t\t           PRICE : \t"<<"Rs.";
 cout<<price;
 cout<<"\n\t\t        IN STOCK : \t";
 cout<<instock;
 cout<<endl<<endl;
 }
 int getprice()
 {
 return price;
 }
 int getcode()
 {
 return pcode;
 }
}i;

//***************************************************************
// INTRODUCTION FUNCTION
//****************************************************************

void welcome()
{
 void buy();
 void products(int);
 void password();
 void quit();
 char choice;
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<"------------------------------------------------------------------------------ \n";
 cout<<"\t\t\t\t WELCOMES YOU \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t SHOP WITH US.(press 1) \n\n";
 cout<<"\t GET DETAILS OF ALL PRODUCTS.(press 2)\n\n\n";

 cout<<"\t\t\t\t\t      Only for owner:Press 3 to login. \n";
 cout<<"\t\t\t\t\t      (A password would be verified) \n\n";
 cout<<"-------------------------------------------------------------------------------\n";
 cout<<"\t\t\t\t\t\t\t EXIT.(press 4) \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t ENTER YOUR CHOICE.... \t";
 cin>>choice;
 switch(choice)
 {
  case '1' : buy();
		  break;
  case '2' : products(2);
		  break;
  case '3' : password();
		  break;
  case '4' : quit();
		  break;
  default : system("cls");
	 cout<<"------------------------------------------------------------------------------ \n";
			  cout<<"\t OOPS!! Your choice doesn't match the following cases. \n";
			  welcome();
 }
}

//***************************************************************
// FUNCTION TO WRITE DATA IN FILE
//****************************************************************

void enterrecord()
{
system("cls");
 void login();
 char ans='y',res;
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t ENTER DETAILS \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 ofstream fout("product.txt",ios::out|ios::binary|ios::app);
 do
 {
 i.enterdata();
 fout.write((char*)&i,sizeof(i));
 cout<<"\n\t\t   YOUR DATA IS SUCCESSFULLY STORED \n";
 cout<<"\n\t\t   WANT TO ENTER ANOTHER RECORD(Y/N) : \t";
 cin>>ans;
 }while(ans=='Y'||ans=='y');
 fout.close();
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t   BACK(press 1) MAIN MENU(press any button)\n";
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t ENTER YOUR CHOICE.... \t";
 cin>>res;
 if(res=='1')
 {
system("cls");
 login();
 }
 else
 {
system("cls");
 welcome();
 }
}

//***************************************************************
// FUNCTION - CREDITS
//****************************************************************

void quit()
{
system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\n\n\n\t\t THANK YOU FOR VISITING US. ";
 cout<<"\n\n\n\t\t\t\t\t\t PROGRAMMER - NILESH TANWAR"<<"\n\n\n";
 cout<<"\n\n -----------------------------------------------------------------------------\n";
 cout<<"\t\t\t (c).NILESH MARKETING LIMITED";
 cout<<"\n-------------------------------------------------------------------------------- \n";
 getchar();
}

//***************************************************************
// FUNCTION TO READ ALL RECORDS FROM FILE
//****************************************************************

void products(int choice)
{
 void login();
 system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t DETAILS OF PRODUCT \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 ifstream fin("product.txt",ios::in);
 fin.seekg(0);
 while(fin.read((char*)&i,sizeof(i)))
 {
 i.displaydata();
 }
 fin.close();
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t\t\t BACK (press any button)\n";
 system("pause");
  switch(choice)
 {
  case 1 : system("cls");
			  login();
			  break;
  case 2 : system("cls");
			  welcome();
			  break;
 }
}

//***************************************************************
// FUNCTION TO MODIFY RECORDS OF FILE
//****************************************************************

void modify()
{
 void login();
 int code,newprice,quantity,found=0;
 char schname[15],prdname[15],res;
 long pos;
system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t MODIFY DETAILS OF PRODUCT \n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"ENTER THE PRODUCT CODE WHOSE RECORD IS TO BE MODIFIED : \t";
 cin>>code;
 fstream fp("product.txt",ios::in|ios::binary|ios::out);
 fp.seekg(0);
 while(fp)
 {
 pos=fp.tellg();
 fp.read((char*)&i,sizeof(i));
 if(i.getcode()==code)
 {
 i.displaydata();
 cout<<"\n\n\t\t\t ENTER THE NEW DETAILS OF PRODUCT:";
 cout<<"\n\t (Press '0' to retain old one) ENTER CHANGED NAME OF SCHOOL : \t";
 cin>>schname;
 cout<<"\n\t (Press '0' to retain old one) ENTER CHANGED NAME OF PRODUCT : \t";
 cin>>prdname;
 cout<<"\n\t           (Press '0' to retain old one) ENTER CHANGED PRICE : \t";
 cin>>newprice;
 cout<<"\n\t      (Press '0' to retain old one) ENTER QUANTITY (IN STOCK): \t";
 cin>>quantity;
 cout<<endl<<endl;
 if(strcmp(schname,"0")!=0)
  strcpy(i.sname,schname);
 if(strcmp(prdname,"0")!=0)
  strcpy(i.pname,prdname);
 if(newprice!=0)
  i.price=newprice;
 if(quantity!=0)
  i.instock=quantity;
 fp.seekg(pos);
 fp.write((char*)&i,sizeof(i));
 cout<<"\n\n\t\t !! RECORD MODIFIED !!";
 found=1;
 break;
 }
 }
 if(found==0)
 {
 cout<<"\n\n RECORD NOT FOUND ";
 fp.close();
 }
 else
 {
 cout<<"\n\n\t PRESS ENTER TO SEE CONTENTS OF FILE : \n";
 getchar();
 fp.seekg(0);
 while(fp.read((char*)&i,sizeof(i)))
 {
 i.displaydata();
 }
 fp.close();
 }
 cout<<"\n\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t   BACK(press 1) MAIN MENU(press any button)\n";
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t ENTER YOUR CHOICE.... \t";
 cin>>res;
 if(res=='1')
 {
system("cls");
 login();
 }
 else
 {
system("cls");
 welcome();
 }
}

//***************************************************************
// FUNCTION TO DELETE RECORD FROM FILE
//****************************************************************

void deleteproduct()
{
system("cls");
 void login();
 int found=0;
 char res;
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t DELETE A PRODUCT \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 int no;
 cout<<"\n\n\t ENTER THE PRODUCT CODE WHOSE RECORD IS TO BE DELETED : \t";
 cin>>no;
 fstream fx("product.txt",ios::in|ios::out);
 fstream fp("Temp.txt",ios::out);
 fp.seekg(0);
 while(fx.read((char*)&i,sizeof(i)))
 {
 if(i.getcode()!=no)
 fp.write((char*)&i,sizeof(i));
 else
 found=1;
 }
 fx.close();
 remove("product.txt");
 rename("Temp.txt","product.txt");
 fp.close();
 if(found==0)
 cout<<"\n\n\t\t RECORD NOT FOUND";
 else
 cout<<"\n\n\t\t RECORD DELETED !!";
 cout<<"\n\n\t PRESS ENTER TO SEE FILE CONTENTS : \n";
 system("pause");
 ifstream fo("product.txt",ios::in);
 fo.seekg(0);
 while(fo.read((char*)&i,sizeof(i)))
 {
 i.displaydata();
 }
 fo.close();
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t   BACK(press 1) MAIN MENU(press any button)\n";
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t ENTER YOUR CHOICE.... \t";
 cin>>res;
 if(res=='1')
 {
system("cls");
 login();
 }
 else
 {
system("cls");
 welcome();
 }
}

//***************************************************************
// FUNCTION TO SEE DETAILS OF ORDER PLACED
//****************************************************************

void orderdetails()
{
 void login();
 char res;
system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t OWNER'S LOGIN : ORDER DETAILS \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 ifstream fin("details.txt",ios::in);
 int ps=1,r=0;
 if(fin){
 cout<<"\n\n\t\t\t DETAILS OF ORDER PLACED BY CUSTOMER "<<ps;
 while(fin.read((char *)&x,sizeof(x))){
 if(x.cc!=ps)
  {
      cout<<"\n\t\t\t\t\t TOTAL AMOUNT : Rs."<<r;
      r=0;
      ps++;
      cout<<"\n-------------------------------------------------------------------------------- \n";
      cout<<"\n\n\t\t\t DETAILS OF ORDER PLACED BY CUSTOMER "<<x.cc;
  }
 cout<<"\n\n\t\t            PRODUCT CODE : \t";
 cout<<x.pcode;
 cout<<"\n\t\t          NAME OF SCHOOL : \t";
 cout<<x.sname;
 cout<<"\n\t\t         NAME OF PRODUCT : \t";
 cout<<x.pname;
 cout<<"\n\t   QUANTITY OF PRODUCT PURCHASED : \t";
 cout<<x.quan;
 cout<<"\n\t\t              TOTAL COST : \t"<<"Rs.";
 cout<<(x.price)*(x.quan);
 r=r+x.quan*x.price;
 cout<<endl<<endl;
 }
 cout<<"\n\t\t\t\t\t TOTAL AMOUNT : Rs."<<r;
 }
 fin.close();
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t   BACK(press 1) MAIN MENU(press any button)\n";
 cout<<"\n ----------------------------------------------------------------------------- \n";
 cout<<"\t ENTER YOUR CHOICE.... \t";
 cin>>res;
 if(res=='1')
 {
system("cls");
 login();
 }
 else
 {
system("cls");
 welcome();
 }
}


//***************************************************************
// ADMINSTRATOR MENU FUNCTION
//****************************************************************

void login()
{
 char choice;
system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t OWNER'S LOGIN : WELCOME \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<" CHOOSE THE TASK: \n\n";
 cout<<"\t\t GET DETAILS OF ALL THE PRODUCTS.(press 1) \n";
 cout<<"\t\t MODIFY PRODUCT DETAILS.(press 2) \n";
 cout<<"\t\t ENTER NEW PRODUCT DETAILS.(press 3) \n";
 cout<<"\t\t DELETE A PRODUCT.(press 4) \n";
  cout<<"\t\t DETAILS OF ORDER PLACED.(press 5) \n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t\t\t\t   MAIN MENU(press 6)\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\t\t ENTER YOUR CHOICE.....";
 cin>>choice;
  switch(choice)
 {
  case '1' : products(1);
			break;
  case '2' : modify();
			break;
  case '3' : enterrecord();
			break;
  case '4' : deleteproduct();
			break;
  case '5' : orderdetails();
			break;
  case '6' :system("cls");
			welcome();
			break;
  default :system("cls");
	 cout<<"------------------------------------------------------------------------------ \n";
	cout<<"\t OOPS!! Your choice doesn't match the following cases. \n";
	login();
 }
}

//***************************************************************
// THE SECURITY CHECK OF PROGRAM
//****************************************************************

void password()
{
system("cls");
 char pass[10];
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" ----------------------------------------------------------------------------- \n";
 for(int i=3;i>0;i--)
 {
 cout<<"\n\t ENTER THE PASSWORD:(only "<<i<<" chance) \t";
 cin>>pass;
 if(strcmp(pass,"nilesh")==0)

	{
	 login();
	 return ;
	}
 else
 cout<<"\n\t YOU ENTERED A WRONG PASSWORD !!!..... \n";
}
 cout<<"\n\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t AMBIGUOUS USER !! ALERT !!..... \n";
 cout<<" ----------------------------------------------------------------------------- \n";
 cout<<"\a";
exit(0);
}

//***************************************************************
// FUNCTION TO PLACE ORDER AND GENERATE BILL FOR SHOPPING
//****************************************************************

void buy()
{
 static int c=0;
 c++;
 void deleteproduct();
 void shop();
 char ans='y';
 int r=0,xa,n=0,y,code[15],no[15];
 long pos;
 system("cls");
 cout<<"------------------------------------------------------------------------------ \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<" -----------------------------------------------------------------------------\n";
 cout<<"\t\t\t\t SHOP WITH US \n";
 cout<<"------------------------------------------------------------------------------ \n";
 ifstream fin("product.txt",ios::in|ios::app);
 fin.seekg(0);
 while(fin.read((char*)&i,sizeof(i)))
 {
 i.displaydata();
 }
 fin.close();
 cout<<"\n\n\t\t\t START SHOPPING";
 int j=0;
 while(ans=='y'||ans=='Y')
 {
 cout<<"\n\n\t\t ENTER THE PRODUCT CODE : \t";
 cin>>code[j];
 cout<<"\n     ENTER QUANTITY (LESS THAN INSTOCK) : \t";
 cin>>no[j];
 fstream fp("product.txt",ios::in|ios::binary|ios::out);
 fp.seekg(0);
 while(fp)
 {
 pos=fp.tellg();
 fp.read((char*)&i,sizeof(i));
 if(i.getcode()==code[j])
 {
 if(i.instock>no[j])
 i.instock=i.instock-no[j];
 else if(i.instock<=no[j])
 i.instock=0;
 i.quan=no[j];
 fp.seekg(pos);
 fp.write((char*)&i,sizeof(i));
 }
 }
 cout<<"\n\n\t\t WANT TO PURCHASE ANOTHER PRODUCT (Y/N) : \t";
 cin>>ans;
 j++;
 n++;
 }
system("cls");
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\t\t\t RAINBOW UNIFORM MARKETING LTD. \n";
 cout<<"\t\t Main bazzar,Jwalapur,Haridwar,Uttarakhand  \n";
 cout<<"\t\t\t Ph:-254908,Mobile-9680605690 \n\n";
 cout<<"------------------------------------------------------------------------------ \n";
 cout<<"\t\t\t\t SHOP WITH US \n";
 cout<<"-------------------------------------------------------------------------------- \n";
 cout<<"\n   S.NO."<<"\t DETAILS"<<"\t   QUANTITY"<<"\t   AMOUNT(IN Rs.) \n\n";
 ofstream fout("details.txt",ios::app|ios::out);
 for(int s=0;s<=n;s++)
 {
 fstream fx("product.txt",ios::in);
 fx.seekg(0);
 while(fx.read((char*)&i,sizeof(i)))
 {
 if(i.getcode()==code[s])
 {
 x.cc=c;
 cout<<"   "<<(s+1);
 y=i.getcode();
 x.pcode=y;

 cout<<"\t   "<<y;
 cout<<"\t";
 cout<<i.sname;
 strcpy(x.sname,i.sname);

 cout<<"\t";
 cout<<i.pname;
 strcpy(x.pname,i.pname);

 cout<<"\t\t";
 cout<<no[s];
 x.quan=no[s];

 xa=i.getprice();
 x.price=xa;
 fout.write((char *)&x,sizeof(x));
 cout<<"\t\t"<<xa<<"*"<<no[s]<<"="<<no[s]*xa;
 cout<<"\n"<<"\n";
 r+=(no[s]*xa);
 }
 }
 fx.close();
 }
 fout.close();
 cout<<"\n"<<"\t"<<"\t"<<"\t";
 cout<<"\t"<<"\t total amount = Rs."<< r ;
 cout<<"\n\n\t\t\t\t    *Only valid product code are considered. \n\n\n";
 cout<<"\n"<<"\t\t\t\t"<<"THANK YOU FOR SHOPPING"<<"\t";
 cout<<"\n\n ----------------------------------------------------------------------------- \n";
 cout<<"\t\t\t\t\t\t MAIN MENU(press any button)\n";
 system("pause");
system("cls");
 welcome();
}

//***************************************************************
// THE MAIN FUNCTION OF PROGRAM
//****************************************************************

int main()
{
 welcome();
 return 0;
}


