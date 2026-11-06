#include<iostream>
#include<string>
using namespace std;
class library{
private:
       int bookID[100];
	   string bookname[100];
	   string author[100];
	   int issued[100];
	   
	   int totalbooks=0;
	    
	public:
//addbooks
void addbook(){
     if(totalbooks>=100){
     	cout<<"library is full now\n";
     	return;
	 }
     cout<<"enter book ID : ";
     cin>>bookID[totalbooks];
     
     cin.ignore();
     cout<<"enter  book name: ";
     getline(cin,bookname[totalbooks]);
      
     cout<<"enter auhor name : ";
     getline(cin,author[totalbooks]);
     
     issued[totalbooks]=false;
     
     totalbooks++;
     cout<<"\n book added succesfully \n";
}	
	//DISPLAY BOOKS
	void displaybooks(){
		if(totalbooks==0){
			cout<<"boks are not available \n";
			return;
		}
		cout<<"\n ALL BOOKS \n";
		for(int i=0;i<totalbooks;i++){
			cout<<"\n BOOK ID : "<<bookID[i];
			cout<<"\n BOOK NAME : "<<bookname[i];
			cout<<"\n AUTHOR : "<<author[i];
			
			if (issued[i]){
				cout<<"\n status is issued";
			}
			else{
				cout<<"\n status available\n";
			}
		}
	}
	//search books 
	void searchbooks(){
		int id;
		bool found=false;
		cout<<"enter book id to search :";
		cin>>id;
		
		
		for(int i=0;i<totalbooks;i++){
			if(bookID[i] == id){
				cout<<"\n book found!\n ";
				cout<<"\nbok name: "<<bookname[i];
				cout<<"\n author : "<<author[i];
				found =true;
				break;
			}
		}
		if(!found){
			cout<<"\n book not found \n";
		}
	}
	//issue book
	void issuebook(){
		int id;
		cout<<"enter book ID to issue :";
		cin>>id;
		for(int i=0;i<totalbooks;i++){
			if(bookID[i]==id){
				if(issued[i]){
					cout<<"book is already issued \n";
				}
				else{
					issued[i]=true;
					cout<<"book Issued succesfully!\n";
				}
				return;
			}
			cout<<"bok not found \n";
		}
	}
		//retyrn book
		void returnbook(){
			int id;
			cout<<"enter book ID to return :";
			cin>>id;
			for(int i=0;i<totalbooks;i++){
				if (bookID[i]==id){
					if(issued[i]){
						issued[i]=false;
						cout<<"book returned succesfully \n";
					}
					else{
						cout<<"this book was not issued \n";
					}
					return;
				}
			}
			cout<<"book not found \n";
			
			
		}
		void exit(){
			cout<<"EXIT \nTHANK YOU";
		}
	
};
	int main(){
	library lib;
	int choice;
	
	
	do{
	
	
		cout<<"========================"<<endl;
		cout<<"LIBRARY MANAGMENT SYSTEM"<<endl;
		cout<<"========================="<<endl;
		cout<<"1. ADD BOOKS "<<endl;
		cout<<"2. DISPLAY BOOKS "<<endl;
		cout<<"3. SEARCH BOOKS"<<endl;
		cout<<"4. ISSUE BOOKS "<<endl;
		cout<<"5. RETURN BOOK"<<endl;
		cout<<"6. EXIT"<<endl;
		
	
	cout<<"enter your choice : ";
	cin>>choice;
	switch(choice){
		case 1:
			lib.addbook();
			break;
	    case 2:
	    	lib.displaybooks();
	    	break;
	    case 3:
	    	lib.searchbooks();
	    	break;
	    case 4:
	        lib.issuebook();
	    	break;			
	    case 5:
	    	lib.returnbook();
	    	break;	
	    case 6:
	    	lib.exit();
	    	break;	
	    default :
		cout<<"invalid choice"  ;	}
	
}while(choice!=6);

	return 0;
	
}
