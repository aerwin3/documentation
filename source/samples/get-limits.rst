.. code-block:: bash

 curl -s --user 'api:YOUR_API_KEY' -G \
    https://api.mailgun.net/v3/domains/YOUR_DOMAIN_NAME/limits/tag

.. code-block:: java

 import com.mashape.unirest.http.HttpResponse;
 import com.mashape.unirest.http.JsonNode;
 import com.mashape.unirest.http.Unirest;
 import com.mashape.unirest.http.exceptions.UnirestException;

 public class MGSample {

     // ...

     public static JsonNode getLimitsTag() throws UnirestException {

         HttpResponse <JsonNode> request = Unirest.get("https://api.mailgun.net/v3/domains/"+ YOUR_DOMAIN_NAME + "/limits/tag")
             .basicAuth("api", API_KEY)
             .asJson();

         return request.getBody();
     }
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('YOUR_API_KEY');
  $domain = 'YOUR_DOMAIN_NAME';

  # Issue the call to the client.
  $result = $mgClient->get("domains/$domain/limits/tag");

.. code-block:: py

 def get_stats():
     return requests.get(
         "https://api.mailgun.net/v3/domains/YOUR_DOMAIN_NAME/limits/tag",
         auth=("api", "YOUR_API_KEY"))

.. code-block:: rb

 def get_stats
   url_params = {}
   url_params[:limit] = 10
   query_string = url_params.collect {|k, v| "#{k.to_s}=#{CGI::escape(v.to_s)}"}.
     join("&")
   RestClient.get "https://api:YOUR_API_KEY"\
   "@api.mailgun.net/v3/domains/YOUR_DOMAIN_NAME/limits/tag"
 end

.. code-block:: csharp

 using System;
 using System.IO;
 using RestSharp;
 using RestSharp.Authenticators;

 public class GetTagsChunk
 {

     public static void Main (string[] args)
     {
         Console.WriteLine (GetTags ().Content.ToString ());
     }

     public static IRestResponse GetTags ()
     {
         RestClient client = new RestClient ();
         client.BaseUrl = new Uri ("https://api.mailgun.net/v3");
         client.Authenticator =
             new HttpBasicAuthenticator ("api",
                                         "YOUR_API_KEY");
         RestRequest request = new RestRequest ();
         request.AddParameter ("domain", "YOUR_DOMAIN_NAME", ParameterType.UrlSegment);
         request.Resource = "domains/{domain}/limits/tag";
         return client.Execute (request);
     }

 }

.. code-block:: go

 // Not supported yet.

.. code-block:: js

 var DOMAIN = 'YOUR_DOMAIN_NAME';
 var mailgun = require('mailgun-js')({ apiKey: "YOUR_API_KEY", domain: DOMAIN });

 mailgun.get(`/domains/${DOMAIN}/limits/tag`, function (error, body) {
   console.log(body);
 });
