#!/bin/bash -x
create()
{
     echo "Enter address book name"
     read ab
   #check address book is available or not in current working directory
     res=`ls | grep $ab | wc -w`
     if [ $res -gt 0 ]
     then 
           echo "Error : file already exist"
     else
           touch $ab
           echo "Address created!" 
     fi
}
insert()
{
     echo "Enter address book name"
     read ab
   #check address book is available or not in current working directory
     res=`ls | grep $ab | wc -w`
     if [ $res -gt 0 ]
     then 
           echo "Enter email "
           read email
           #check email is present in address book or not
           len=`cat $ab | grep $email | wc -w`
           if [ $len -gt 0 ]
           then 
              echo "Error : email already exist"
           else
                echo "Enter First name, Last name, mobile number, city, state, zip"
                read fname lname num ci sta zi
                record=`echo $fname $lname $email $num $ci $sta $zi`
                echo $record >> $ab
                echo "Record inserted!"
           fi
     else
           echo "Error : file is not present"
     fi
}
display()
{
     echo "Enter address book name"
     read ab
   #check address book is available or not in current working directory
     res=`ls | grep $ab | wc -w`
     if [ $res -gt 0 ]
     then 
           cat $ab
     else
           echo "Error : file is not present"
     fi
}
edit()
{
     echo "Enter address book name"
     read ab
   #check address book is available or not in current working directory
     res=`ls | grep $ab | wc -w`
     if [ $res -gt 0 ]
     then 
           echo "Enter email "
           read email
           #check email is present in address book or not
           len=`cat $ab | grep $email | wc -w`
           if [ $len -gt 0 ]
           then 
              echo "Enter the details you want to edit : "
              echo "First name last name email mobile number city state zip"
              read fname lname number city state zip
              new=`echo $fname $lname $email $number $city $state $zip`
              old=`cat $ab | grep $email `
              echo "Old record : $old"
              echo "New record : $new"
              sed -i s/"$old"/"$new"/g $ab
              echo "Record Modified"
           else
               echo "Error : email doesn't exist"
           fi
     else
           echo "Error : file is not present"
     fi
}
delete()
{
     echo "Enter address book name"
     read ab
   #check address book is available or not in current working directory
     res=`ls | grep $ab | wc -w`
     if [ $res -gt 0 ]
     then 
           echo "Enter email "
           read email
           #check email is present in address book or not
           len=`cat $ab | grep $email | wc -w`
           if [ $len -gt 0 ]
           then 
              old=`cat $ab | grep $email`
              sed -i s/"$old"//g $ab
              sed -i /^$/d $ab
              echo "Record Deleted"
           else
               echo "Error : name doesn't exist"
           fi
     else
           echo "Error : file is not present"
     fi
}
while [ true ]
do
      echo "***********MENU************"
      echo "1. Create"
      echo "2. Insert record"
      echo "3. Display"
      echo "4. Edit"
      echo "5. Delete"
      echo "7. Exit"
      echo "Enter choice : "
      read choice
      case $choice in
              1) create ;;
              2) insert ;;
              3) display ;;
              4) edit ;;
              5) delete ;;
              6) exit ;;
              *) echo "Wrong Choice!" ;;
      esac
done