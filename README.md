Types of Routing:-

There are 2 types of Routing in MVC application
Conventional or Traditional Routing (Using Routing Config)
Attribute Routing (Available in MVC 5) 

Conventional or Traditional Routing :-

Conventional or Traditional Routing also is a pattern matching system for URL that maps incoming request to the particular controller and action method.
We set all the routes in the RouteConfig file.
RouteConfig file is available in the App_Start folder.
We need to register all the routes to make them operational.


Conventional Routing:-

public class RouteConfig  
    {  
        public static void RegisterRoutes(RouteCollection routes)  
        {  
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");  
  
            routes.MapRoute(  
                name: "Default",  
                url: "{controller}/{action}/{id}",  
                defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }  
            );  
        }  
    }  
Attribute Routing :-

It is a very simple routing method compared to conventional routing. 
All the concepts are just like the conventional approach but here, we define all the routes and attributes. 

In attribute, we define the routing on a simple controller or action method. 

public class RouteConfig  
    {  
        public static void RegisterRoutes(RouteCollection routes)  
        {  
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");  
  			routs.mapMvcAttributeRoutes();
            routes.MapRoute(  
                name: "Default",  
                url: "{controller}/{action}/{id}",  
                defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }  
            );  
        }  
    } 



Action Filters :-
 
Action Filter is an attribute that you can apply to a controller action or an entire controller. 
This filter will be called before and after the action starts executing and after the action has executed.
 Action filters implement the IActionFilter interface that has two methods OnActionExecuting andOnActionExecuted. 
OnActionExecuting runs before the Action and gives an opportunity to cancel the Action call. 
These filters contain logic that is executed before and after a controller action executes, you can use an action filter, for instance, to modify the view data that a controller action returns.

namespace ActionFiltersinMVC.AuthData    
{    
    public class AuthAttribute: ActionFilterAttribute,    
    IAuthenticationFilter    
    {    
    
        public void OnAuthentication(AuthenticationContextfilterContext)    
        {    
            //Logic for authenticating a user    
        }    
    
        //Runs after the OnAuthentication method    
        public void OnAuthenticationChallenge(AuthenticationChallengeContextfilterContext)    
        {    
            //TODO: Additional tasks on the request    
        }    
    }    
}