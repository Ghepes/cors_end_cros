# cros
Cros domain accept with json. From your Domain To accept request, It is set by default to block requests to the bucket, so you must specify where the request comes from "DOMAIN NAME"

### A simple example of how you can accept requests from a specific domain

 ### * Exemple json :
cross cors-domainx.json
It's up to you how you set setting up to receive requests.  [CROS info: https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS)

[Exemple google Basic CROS config ](https://cloud.google.com/storage/docs/cors-configurations)
### EXAMPLES
````
[
    {
      "origin": ["*"],
      "method": ["GET"],
      "responseHeader": ["Content-Type"],
      "maxAgeSeconds": 3600
    },
    {
      "origin": ["https://domainx.xyz"],
      "method": ["PUT", "OPTIONS"],
      "responseHeader": ["Content-Type", "Content-Length", "ETag"],
      "maxAgeSeconds": 3600
    }
  ]
````

### EXEMPLES DUAL DOMAIN
````
[
    {
      "origin": ["*"],
      "method": ["GET"],
      "responseHeader": ["Content-Type"],
      "maxAgeSeconds": 3600
    },
    {
      "origin": ["https://exemple.com", "https://x.exemple.com"],
      "method": ["PUT", "OPTIONS"],
      "responseHeader": ["Content-Type", "Content-Length", "ETag"],
      "maxAgeSeconds": 3600
    }
  ]

````

### EXEMPLES DUAL DOMAIN end GET RESTRICT
````
[
    {
      "origin": ["https://x.exemple.com"], // Only for https://x.exemple.com the content
      "method": ["GET"],
      "responseHeader": ["Content-Type"],
      "maxAgeSeconds": 3600
    },
    {
      "origin": ["https://exemple.com", "https://x.exemple.com"],
      "method": ["PUT", "OPTIONS"],
      "responseHeader": ["Content-Type", "Content-Length", "ETag"],
      "maxAgeSeconds": 3600
    }
  ]

````

Example for Private folder accessible only from a domain (exactly your case with /secure/key.json):
````
[
  {
    "origin": ["https://blob.domain.com"],
    "method": ["GET"],
    "responseHeader": ["Content-Type"],
    "maxAgeSeconds": 3600
  }
]
````

Example for multiple domains only on GET with 600:
````
[
  {
    "origin": ["https://vendor.exemple.com", "https://user.exemple.com"],
    "method": ["GET"],
    "responseHeader": ["Content-Type"],
    "maxAgeSeconds": 600
  }
]
````




open CLI and add the command:

````
gsutil cors set cors-domainx.json gs://domainx.xyz
````
````
gsutil cors get gs://domain.xyz
````


Congratulations, requests from the domain domainx.xyz are now accepted.
