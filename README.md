# conversation_demo
for anyone quick deploy a bluemix watson conversation demo with node-red at bluemix integrated into facebook messenger

# about
this document is focused to anyone, independent of the technical skills, quickly deploy his own watson conversations demo.
to simplify the front-end development, we will use fecebook messenger as front-end. 
in order to simplify the facebook messenger integration with bluemix watson conversations we will use chatfuel.com.

# to start
you must create a page at facebook. you must have a facebook account. http://www.facebook.com

you will need an account at chatfuel.com. you will login with the Facebook account. http://www.chatfuel.com

you must have a bluemix.net account. http//:www.bluemix.net

# step 1: facebook page
create a facebook page in your account. 

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/fb_create_page.png?raw=true">

select the page type according to your demos needs, for example: company type.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/fb_create_company.png?raw=true">

# step 2: login at chatfuel
login at chatfuel utilizing the facebook account.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/chatfuel.png?raw=true">

# step 3: create a watson convesation workspace
once you are at bluemix.net dashboard (https://console.ng.bluemix.net/dashboard/services), press the create service button.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_create_svr.png?raw=true">

search for watson services and select the Conversation service, in the creation page take a note of the suggested service name and press "create" button. (you may change the service name if you want).

go to the "service credential" option and pickup the username and password, you will need it to configurate your service at node-red.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_cv_serviCred.png?raw=true">

return to "manage" option in the service overall page, press the "launch tool" button

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_conv_launch.png?raw=true">

you can create a new conversation workspace, if you know how to use this tool, or can import an basic example of dialogs with this file:
file json workspace example : workspace-simple-example-english.json or workspace-exemplo-simples-portugues.json

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_cv_create_import.png?raw=true">

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_wk_id_import.png?raw=true">

now the workspace is created and with a very simple dialog (greeting, demo propouse, farewell). select the workspace detail in order to know the workspace id, you will need it at node-red configuration.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_wk_detail_wks_id.png?raw=true">

# step 4 : create a node-red application
go back to bluemix dashboard: https://console.ng.bluemix.net/dashboard/services and press the "create app" button.
select the node-red starter option.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_node-red-start.png?raw=true">

define a name for your app and press "create" button.

just after you app is created you will be at a "get started" tab and can press the button  "start" in order to start the app and access the node-red interface.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/bm_start_app.png?raw=true">

once you app is running, press the button "view app". the brownser will open a new tab with the node-red starting page, press "Go to your node-re flow editor".

# step 5 : import the node-red example
open the node-red-chatbot-demos.json file and copy the content at the clipboard.
now open the node-red menu for import from the clipboard option.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/nr-import.png?raw=true">

it will import the node-red flow to handle the message from facebook messenger, pass through watson conversation, handle the outpout from conversations and return to messenger. 

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/nr-import-button.png?raw=true">

Now you need to associate your watson conversation services with this flow.


# step 6 : configure the watson conversation
in order to configure the watson conversation service to this demo, get the workspace id (step 3).
open the conversation box in blue (duble click on it) and type the workspace id in it. 

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/nr-conv-wkid.png?raw=true">

# step 7 : integrate facebook messenger with bluemix watson conversation 
in order to integrate the facebook messenger with bluemix, we will use the chatfuel service. 
open the chatfuel.com and loggin with facebook account. 

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/cf-config-face.png?raw=true">

at the "configuration" option (left menu), select the "connect to page" button in order to associate the chatfuel with the page you created at facebook (step 1).

now go to the "build" option (left menu), press the  "default aswer" button and delete the default answer on the right side.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/cf_default-delete.png?raw=true">

now you will configure how to get a message and send to the node-red app. 
first add a plugin card and select the "user-input" type. create the user variable as "watsonMessage".

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/cf-userinput.png?raw=true">

finally, send this user input to the node-red. 
go back to node-red flow editor and copy the url (example: https://node-red-demo-simple-conversation.mybluemix.net/red/).
go to the chatfuel and add another plugin card, but now we will create a json api.

<img src="https://github.com/rickubo/conversation_demo/blob/master/img/cf-jsonapi.png?raw=true">

at the json api configuration type the url for the node-red page:
https://node-red-demo-simple-conversation.mybluemix.net/messenger?message={{watsonMessage}}

ps: replace "node-red-demo-simple-conversation" with the name of the url of your app.

copy the url path in the browser url field once you are at the application's node red page. remember to remove the "/red" part and add "/messenger", which is the node-red flow landing page. add "?message={{watsonMessage}}" to send a parameter forward to node-red flow.

Now you can open the facebook page and send a message on messenger to try it.

HAVE FUN!!!

THANKS

ricardo KUBO 
twitter @rickubo
https://www.linkedin.com/in/ricardokubo





