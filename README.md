# write-a-trigger-when-new-account-inserted-that-time-or-old-records-closed-new-stage-then-when-you-c
write a trigger when new account inserted  that time or old records closed=new stage then when you change that time error fire
trigger beforeUpdateTrigger on Opportunity (after update,before update)
{
    if((trigger.isafter && trigger.isupdate)||(trigger.isbefore && trigger.isupdate))
        
    {
        myaccountHandlers.mymethods(trigger.New,trigger.oldmap);
    }
    
    
}
   

public class myaccountHandlers 
{
     public static void mymethods(list<opportunity>opplist,map<id,opportunity>oppmap)
     {
        for(opportunity app:opplist)
        { 
            opportunity  ooppsce=oppmap.get(app.Id);   //frist ftach old record field value 
             (ooppsce.StageName=='closed Won' &&  app.StageName !=ooppsce.StageName)) 
                  //then compare old value and new value
            {  //frist if staggename =closed won when record insert
                //OR old record closed won and new stagename not equal to closed won then this loop wxecuted
                app.addError('hey you cannot update Now');
            }
        }
     }

}
