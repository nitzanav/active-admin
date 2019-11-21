# ActiveAdmin for MongoDB

### Minimal Requirement
Rails, gems: ActiveAdmin, Device, CanCanCan, docker, Mongoid

### General Task
Create an app for activeadmin to manage MongoDB collections
Athorization and authentication using Devise and CanCanCan gems.
Collections names are accounts and collection.

### Milestones:

1. Create an app for activeadmin to manage MongoDB collections

    * Authenticated ActiveAdmin
    * Rails highest stable version
    * yaml config per environment for example - https://github.com/railsconfig/config
    * Devise gem
    * sqlite DB for user and role models for devise or else, file per each env
    * Mongoid gem
    * manage account collection
    * add data according to the collection attached
    * url slug: suitable for the path 'maindn/main/account'
    * index page - columns: _id, name
        show page - all
        edit page - all
        no create!
    * pagination
    * Filter - Fields: _id, name (I think that contians is enabled by default, anyway it is required for name field) 

2. Manage connection data object:

    * Notes
    * `connection_data` is an array nested inside each account document
    * Note that there is no way to find a connection data by connection_id, need to find it by fetching account. acctually `Account.find(account_id).connections_data[connection_id]`
    * Thus, the URL should be: /admin/account/:id/connections/:id
    * connection data and be blocked for view for developers.


3. Authorization with CanCanCanAbilityAdapter:

    * Developers Role - can manage
    * QA Role - can read
    * Support Role - can read 
    * Limit change permissions to specific fields see below


### Important support only one field update

the default behivor of active-admin is to send all form fields when submitting a chage.
changing one field should send only the modified fields ( see below implementation example ) , 
and the server should support it.

```javascript

$(document).ready(function() {
  $('input, select, textarea').on('change', function() {
    $(this).addClass('changed');
  });
  
  $('form').on('submit', function() {
    $('input:not(.changed), textarea:not(.changed)').prop('disabled', true);
    
    // alert and return just for showing
    alert($(this).serialize().replace('%5B', '[').replace('%5D', ']'));
    return false;
  });
});

```


### Collection fields and types:

```json
{
    "_id" : 28211.0,
    "created" : NumberLong(1572924604),
    "updated" : NumberLong(1573128004),
    "company_id" : NumberLong(0),
    "network_id" : NumberLong(1),
    "email_encrypt" : true,
    "new_job_queue" : NumberLong(1),
    "segment_engine" : NumberLong(2),
    "supp_segment_engine" : 0(2),
    "use_onguniq" : NumberLong(1),
    "use_last_metadata" : NumberLong(1),
    "use_fapi_links" : NumberLong(1),
    "status" : NumberLong(1),
    "use_inhouse" : NumberLong(1),
    "is_us_connection" : NumberLong(1),
    "removal_settings_bounce" : "global",
    "removal_settings_complaint" : "global",
    "removal_settings_unsubscribe" : "local",
    "ignore_empty" : true,
    "notification" : {
        "email" : "test@test.com"
    },
    "name" : "shay",
    "package_id" : NumberLong(160),
    "token" : "adasd12314",
    "preprocess" : NumberLong(45),
    "segment_cache" : false,
    "unique_click_per_mailing" : true,
    "is_setup_wizard_completed" : true,
    "default_tracking_domain" : "http://tracking",
    "default_image_domain" : "http://images",
    "connection_data_pulled" : {
        "14514" : NumberLong(1572924609),
        "14515" : NumberLong(1574115628),
        "14516" : NumberLong(1573572096)
    },
    "connection_data" : {
        "14514" : {
            "esp_id" : NumberLong(88),
            "domain_breakdown" : NumberLong(1),
            "url_rest" : "http://emailapi.dynect.net/rest/",
            "url_rest_read" : "http://emailapi-readonly.dynect.net/rest/",
            "use_internal_unsubscribe" : NumberLong(1),
            "use_smtp_for_sends" : NumberLong(1),
            "host_smtp" : "smtp.dynect.net",
            "host_smtp_port" : NumberLong(587),
            "username" : "a@a.com",
            "password" : "1234",
            "api_key" : "2acf2",
            "enabled" : false
        },
        "14515" : {
            "api_key" : "adasd12314",
            "username" : "a@a.com",
            "password" : "1234",
            "host_smtp" : "smtp.dynect.net",
            "esp_id" : NumberLong(10),
            "custom_headers" : null,
            "external_datasync" : NumberLong(1),
            "domain_breakdown" : NumberLong(1),
            "url_rest" : "http://emailapi.dynect.net/rest/",
            "url_rest_read" : "http://emailapi-readonly.dynect.net/rest/",
            "use_internal_unsubscribe" : NumberLong(1),
            "use_smtp_for_sends" : NumberLong(1),
            "host_smtp_port" : NumberLong(587),
            "email_encrypt" : NumberLong(1),
            "request_account_id" : NumberLong(28211),
            "request_connection_id" : NumberLong(14515),
            "account_id" : NumberLong(28211),
            "last_checked" : NumberLong(1574243082),
            "id" : NumberLong(14515),
            "field_mapping" : {
                "366737" : "email"
            },
            "field_contact_mapping" : []
        }
    },
    "active_connections" : [
        NumberLong(14515)
    ],
    "export_password" : "",
    "default_list_id" : NumberLong(53889),
    "collect_country_stats" : false,
    "collect_platform_stats" : false,
    "collect_browser_stats" : false,
    "do_not_collect_contact_ip" : false,
    "frozen" : null,
    "included_segment_cache" : NumberLong(0),
    "excluded_segment_cache" : NumberLong(0),
    "enable_email_masking" : false,
    "disable_tracking" : false,
    "disable_opening" : false,
    "content_text_no_link_tracking" : false,
    "is_qa" : false,
    "queue" : {
        "interval" : NumberLong(600),
        "location" : "",
        "time" : [
            NumberLong(0)
        ]
    },
    "customer_contacts_activity_webhook_url" : ""
}
```


