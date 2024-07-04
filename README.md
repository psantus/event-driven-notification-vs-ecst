# Event-driven Architecture: reconciling Notification and Event-carried State Transfer (ECST) event styles

This repo contains source code showing how to enrich
a "Notification" event to obtain an "Event-carried State
Transfer" (or "fully-qualified") kind of event.

It illustrates this [blog post published on dev.to](https://dev.to/aws-builders/event-driven-architecture-reconcile-notification-and-event-carried-state-transfer-patterns-5697).

## Contents
2 CloudFormaton stacks (one with a minimal example, the other one with
a more complete setup) that deploy
* An EventBridge bus
* Mathcing rules to push events to
    * Lambdas to enrich events (via an API Gateway to make
      synchronous invocations and hence have retry capability on error.
    * Consumer applications modelled either as Lambdas or 
    as API Destinations (3rd-party API), hosted on webhook.site for easy testability.
* We furthermore demonstrate some of EventBridge capabilities:
    * logging via Cloudwatch
    * archive and replay
    * retry, dead-letter queue management and notification

These stacks require the `lambdalayer.zip` file to be uploaded to
a S3 bucket. This file just contains a basic installation of 
the aws-sdk package (cf. `package.json`) that is deployed as a Lambda layer
enabling to have Lambda function code that is 
* declared inline  in the CloudFormation templates
* readable and modifiable directly in the Lambda GUI in the AWS Management Console.

## Copyright

You can replicate and modify this example as long as you quote 
the author (Paul SANTUS - TerraCloud), together with a link to 
this Github repo.

## Liability 

You use this code under your own responsibility. 