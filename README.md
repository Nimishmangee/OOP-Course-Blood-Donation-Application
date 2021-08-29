# OOP-Course-Blood-Donation-Application
Password:Admin, Language:C++, Used vectors
#include<iostream>
#include<vector>
#include<string.h>
//PASS=Admin
using namespace std;
class bbank{
public:
    //USED VECTOR FOR UPDATION OF NEW DATA
    vector<pair<string,pair<string,string>>> v;
    string bbankname,city,don_center,don_city;  // THESE ARE DATA MEMBERS OF THE CLASS
    void get_data(string bbname, string location,string placeofcoll){
        bbankname=bbname;
        city=location;
        don_center=placeofcoll;
    }
    void update_data(){  //THIS IS ONE OF MEMBER FUNCTIONS OF THE CLASS
        string donor;
        string sam;
        cout<<"Enter donor name:";
        cin>>donor;
        cout<<"Enter donor sample collected:";
        cin>>sam;
        cout<<"Enter city of the donor:";
        cin>>don_city;
        v.push_back(make_pair(don_city,make_pair(sam,donor)));
        }
    //PASS=Admin
};
int main(){
    bbank ob[100];
    int ch,count=0,c=1,j,i;
    char ch1;
   string bbankname,location,placeofcoll,x,group;
    string auth;
    char pass[10];
    cout<<"Admin/User:";
    cin>>auth;
    if(auth=="Admin"){
        cout<<"Enter password:";
        cin>>pass;                //PASS=Admin
        if(!strcmp(pass,"Admin")){
            while(c!=0){
                // UNABLE TO DIFFERENTIATE BETWEEN ADMIN AND USER BUT GIVEN ALL FUNCTIONALITIES TOGETHER
                cout<<"\n\tMAIN MENU";
                cout<<"\n\n01. Register a New Blood Bank";
                cout<<"\n\n02. Update new donor details";
                cout<<"\n\n03. Search for donor";
                cout<<"\n\n04. Search for donor specific details";
                cout<<"\n\n05. Search for blood banks in specific areas"<<endl<<endl;
                cin>>ch;
                //PASS=Admin
            switch(ch){
                    case 1:
                    cout<<"Enter name of the blood bank: ";
                    cin>>bbankname;
                    cout<<"Enter location of blood bank:";
                    cin>>location;
                    cout<<"Enter place of collection center:";
                    cin>>placeofcoll;
                    ob[count].get_data(bbankname,location,placeofcoll);
                    count++;
                    break;
                case 2:
                    cout<<"Enter name of blood bank:";
                    cin>>x;
                    for(int i=0;i<=count;i++){
                        if(ob[i].bbankname==x)
                            ob[i].update_data();
                        else
                            continue;
                    }
                    break;
                case 3:
                    cout<<"Enter blood group required:";
                    cin>>group;
                    if(count==0)
                        cout<<"No match found";
                    for(i=0;i<=count;i++){
                        for(j=0;j<ob[i].v.size();j++){
                            if(ob[i].v[j].second.first==group){
                                cout<<"Match found for blood group: "<<ob[i].v[j].second.first<<" with donor name:" <<ob[i].v[j].second.second;
                                break;}
                    }
                        if(ob[i].v[j].second.first==group)
                            break;
                    }
                    if(i<count)
                        cout<<"No match found";
                    break;
                case 4:
                    cout<<"Do you want to search by blood group(b) or by city(c):";
                    cin>>ch1;
                    if(ch1=='b'){
                        cout<<"Enter blood group:";
                        cin>>group;
                        if(count==0)
                            cout<<"No match found";
                        else
                        {for(i=0;i<=count;i++){
                            for(j=0;j<ob[i].v.size();j++){
                                if(ob[i].v[j].second.first==group){
                                    cout<<"Match found for blood group: "<<ob[i].v[j].second.first<<" with donor name:" <<ob[i].v[j].second.second<<" and city:"<<ob[i].v[j].first;
                                    break;}
                        }
                            if(ob[i].v[j].second.first==group)
                                break;
                        }
                        }
                    }
                    else if(ch=='c'){
                        cout<<"Enter city:";
                        cin>>x;
                        if(count==0)
                            cout<<"No match found";
                        else
                        {for(i=0;i<=count;i++){
                            for(j=0;j<ob[i].v.size();j++){
                                if(ob[i].v[j].first==x){
                                    cout<<"Match found city: "<<x<<" with donor name:" <<ob[i].v[j].second.second<<" and blood group:"<<ob[i].v[j].second.first;
                                    break;}
                        }
                            if(ob[i].v[j].second.first==group)
                                break;
                        }
                        }
                    }
                    break;
                case 5:
                    cout<<"Enter city for blood bank's information:";
                    cin>>location;
                    for(int i=0;i<=count;i++){
                        if(ob[i].city==location)
                            cout<<i+1<<" th blood bank found:"<<ob[i].bbankname<<endl;
                        else
                            continue;
                    }
                    break;
                }
                cout<<"Do you wish to continue(0/1): ";
                cin>>c;
            }
        }
        else
            cout<<"Authority denied";
    }
    else if(auth=="User"){
        while(c!=0){
            // UNABLE TO DIFFERENTIATE BETWEEN ADMIN AND USER BUT GIVEN ALL FUNCTIONALITIES TOGETHER
            cout<<"\n\tMAIN MENU";
            //cout<<"\n\n01. Register a New Blood Bank";
            cout<<"\n\n02. Update new donor details";
            cout<<"\n\n03. Search for donor";
            //cout<<"\n\n04. Search for donor specific details";
            cout<<"\n\n05. Search for blood banks in specific areas"<<endl<<endl;
            cin>>ch;
        switch(ch){
                /*case 1:
                cout<<"Enter name of the blood bank: ";
                cin>>bbankname;
                cout<<"Enter location of blood bank:";
                cin>>location;
                cout<<"Enter place of collection center:";
                cin>>placeofcoll;
                ob[count].get_data(bbankname,location,placeofcoll);
                count++;
                break;*/
            case 2:
                cout<<"Enter name of blood bank:";
                cin>>x;
                for(int i=0;i<=count;i++){
                    if(ob[i].bbankname==x)
                        ob[i].update_data();
                    else
                        continue;
                }
                break;
            case 3:
                cout<<"Enter blood group required:";
                cin>>group;
                if(count==0)
                    cout<<"No match found";
                for(i=0;i<=count;i++){
                    for(j=0;j<ob[i].v.size();j++){
                        if(ob[i].v[j].second.first==group){
                            cout<<"Match found for blood group: "<<ob[i].v[j].second.first<<" with donor name:" <<ob[i].v[j].second.second;
                            break;}
                }
                    if(ob[i].v[j].second.first==group)
                        break;
                }
                if(i<count)
                    cout<<"No match found";
                break;
           /* case 4:
                cout<<"Do you want to search by blood group(b) or by city(c):";
                cin>>ch1;
                if(ch1=='b'){
                    cout<<"Enter blood group:";
                    cin>>group;
                    if(count==0)
                        cout<<"No match found";
                    else
                    {for(i=0;i<=count;i++){
                        for(j=0;j<ob[i].v.size();j++){
                            if(ob[i].v[j].second.first==group){
                                cout<<"Match found for blood group: "<<ob[i].v[j].second.first<<" with donor name:" <<ob[i].v[j].second.second<<" and city:"<<ob[i].v[j].first;
                                break;}
                    }
                        if(ob[i].v[j].second.first==group)
                            break;
                    }
                    }
                }
                else if(ch=='c'){
                    cout<<"Enter city:";
                    cin>>x;
                    if(count==0)
                        cout<<"No match found";
                    else
                    {for(i=0;i<=count;i++){
                        for(j=0;j<ob[i].v.size();j++){
                            if(ob[i].v[j].first==x){
                                cout<<"Match found city: "<<x<<" with donor name:" <<ob[i].v[j].second.second<<" and blood group:"<<ob[i].v[j].second.first;
                                break;}
                    }
                        if(ob[i].v[j].second.first==group)
                            break;
                    }
                    }
                }
                break;*/
            case 5:
                cout<<"Enter city for blood bank's information:";
                cin>>location;
                for(int i=0;i<=count;i++){
                    if(ob[i].city==location)
                        cout<<i+1<<" th blood bank found:"<<ob[i].bbankname<<endl;
                    else
                        continue;
                }
                break;
            }
            cout<<"Do you wish to continue(0/1): ";
            cin>>c;
        }
    }
    return 0;

    }


