# **Remote Sync** 


## <span style="text-decoration:underline;">Overview</span>

Many CIAM customers have multiple user stores that need to be maintained until legacy systems can be decommissioned.
When the identity information sourced in Okta changes these users and attributes need to be synchronized downstream. Okta Workflows provides an easy to implement, fully customizable method to update a remote system with CRUD (create, update and delete) operations.
This integration uses Okta Group membership to identify those users that shall be synced. Adding a user to the group initiates the creation in the remote system. Removing a user from group deletes the user from remote system.
In this sample the users name, address and email are synced to remote system. The flows can be modified to change attribute sync requirements. 

The implementation uses a modular approach that splits the downstream CRUD operations into child flows to facilitate adaptation to complex environments.

## Before you get Started / Prerequisites

Before you get started, here are the things you’ll need:



*   Access to an Okta tenant with Okta Workflows enabled for your Org 
*   The Remote System API calls in this sample are using a mock API. Create HTTP Connector for mock API Auth = none


## Setup Steps



1. Configure an HTTP Connector to communicate with a remote system
    * Okta Workflow HTTP Connections securely enable;
		* Basic Auth
		* Custom Auth
		* OAuth
2. Select flow titled "[child]Create User via API".
    * Modify API URL and API Request JSON to match your remote system requirements
	* Select appropriate HTTP Connector for "HTTP Raw Request" card
3. Select flow titled "[child]Update User via API".
    * Modify API URL and API Request JSON to match your remote system requirements
	* Select appropriate HTTP Connector for "HTTP Raw Request" card
4. Select flow titled "[child]Delete User via API".
    * Modify API URL and API Request JSON to match your remote system requirements
	* Select appropriate HTTP Connector for "HTTP Raw Request" card
5. Create Okta Group named "API Provisioning Group"
6. Add custom attribute to Okta User Profile name = 'customId' type=string
	* This attribute shall hold user Id from Remote System
7. Ensure that both flows are turned on.


## Testing this Flow

The easiest way to test a flow is to add your test user to the Okta Group "API Provisioning Group"



1. In the Okta Admin UI, navigate to the test users page
2. In the Groups tab of the Users page, add "API Provisioning Group"
3. Inspect the remote system for test user.
4. In the Profile tab of the Users page, edit value for "city" attribute
5. Inspect the remote system for change in test users "city" value.
6. In the Groups tab of the Users page, remove "API Provisioning Group"
7. Inspect the remote system, searching for test user, which should not be present.


## Limitations & Known Issues



*   None