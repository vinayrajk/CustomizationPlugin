# CustomizationPlugin
Most of the products or integrations requires pre-configurations or settings such as integrations setup, customer class, Order Types, any default values, default Numbering sequence, etc. Every time if there is an implementation of a product package there will be a good amount of manual efforts are involved to setup the initial configurations. 
 
So Is there any possibility to capture the settings automatically, without any manual effort? Yes it is possible, Acumatica has a powerful and flexible framework to code such things. 

Customization Plug-In is a separate code file with class that Acumatica can dynamically compile and load during publication process. Class events will be automatically subscribed and executed on Database or/and Files operation

# Sample Code 
    //Customization plugin is used to execute custom actions after customization project was published 
    public class MyPlugIn : CustomizationPlugin
    {
        //This method executed right after website files were updated, but before website was restarted
        //Method invoked on each cluster node in cluster environment
        //Method invoked only if runtimecompilation is enabled
        //Do not access custom code published to bin folder, it may not be loaded yet
        public override void OnPublished()
        {
            this.WriteLog("OnPublished Event");
        }

        //This method executed after customization was published and website was restarted.
        public override void UpdateDatabase()
        {
            this.WriteLog("UpdateDatabase Event");

        }
    }
