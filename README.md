<h1>PROTECT Main Branch AUTOMATICALLY<h1>
  
This web service will listen for a webhook from github when a new repository is created, and automatically apply protection to the main branch and sends out a notification to notify user of this event.

<p>Start by cloning the repository containing the web service code.</p>
<p><b><i>git clone https://github.com/nero-code-inc/repo-web-service.git</i></b></p>

<h1>Installation</h1>
<p>The follow is steps are required: </p>
<ul>
  <li>Install python3</li>
  <li>A requirements.txt file if provide containing the neccessary dependencies,run <b>sudo pip3 install -r requirements.txt</b> to install neccessary dependencies.</li>
</ul>

<h1>Setup</h1>
<ul>
  <li>Create an organization account on github.</li>
  <li>Setup a webhook on your github organization https://developer.github.com/webhooks/creating/#setting-up-a-webhook.</li>
  <li>Make sure to do the following:<br>
    <b>Set:<br>
    Payload URL=ngrok forwarding url<br>
    Content type=application/json<br>
    Secret=Any of your choice<br>
    Which events would you like to trigger this webhook?=repository, also do not forget to save it.</b></li>
  <li>Provide the neccessary credential in the .env file</li>
  <li>Setup a connection with ngrok https://dashboard.ngrok.com/get-started/setup to allow internet access to you local environment to enable testing.</li>
</ul>

<h1>Deploy</h1>
<ul>
  <li>run <b>flask run --host=0.0.0.0 &</b> to start your web service.<br>
  Before you run the above command, do the following:<br>
    <b>export FLASK_APP=webhook.py<br>
      export FLASK_ENV=development</b>
  </li>
  <li>run <b>./ngrok http 5000</b> to start your service forwarding.</li>
  <li>Copy the forwarding address given by ngrok to your webhook created earlier to enable to send payload to you service.</li>
  <li>Create a repository under your organization and verify that it is automatically protected and create an issue to notify you of this event.</li>
