SalesForce-Membership-Authenticator
===================================

This is some open apex code to help setup a custom authentication provider for SalesForce - Visual Force pages. This uses a simple cookie authentication scheme, so it is not exactly robust, but could be made more secure. It currently relies on a generated token that can only exist in one client location at a time, controlling multiple logins.

b3Auth is a generic authentication membership verification class. You can make modifications here, to your membership verification needs.

General setup is as follows, inside the Custom Controller for the Visual Force View, upon instantiation you will call the authentication method.

//a test controller for a page
public Test_Controller()
    {
       //here is where we roll our authentication
       mc = new Member_Controller();
       
       //change the provider, Member_Provider_Default is the native
       //Member object's password.
       //you don't need to specify default this is just an example, as it is initiated on creation of the controller
       //mc.provider = new Member_Provider_Default();
      
       if(mc.isAuth()){
       //do some other things you need to do with auth'd peeps
        
       }
    }




Any page that is bound to a controller using this method, will in effect be 'secured'. This will verify that a cookie is needed before proceeding.

The really cool thing about this, is that you can use Visual Force pages to output JSON for a simple rest service, and secure those behind this authentication method, so they do not respond to any requests.
