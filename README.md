# Specs for active admin project

create a connection maindb with DB main and collection connection

#### Minimal Requirement
Rails, gems: ActiveAdmin, Device, CanCanCan, docker , active admin mongoid

### General Task
create active admin docker instance including CanCanCan and
and according to the account collection .(see below)

### Milestones:

1. create simple account with editing possibility

1.1 Authenticated ActiveAdmin
1.2 Rails highest stable version
1.3 yaml config per environment for example - https://github.com/railsconfig/config
1.4 Devise gem
1.5 sqlite DB for user and role models for devise or else, file per each env
1.6 Mongoid gem
1.7 manage account collection
1.8 add data according to the collection attached
1.9 url slug: suitable for the path 'maindn/main/account'
1.91 indexing - columns: _id, name
    show - all
    edit - all
    no create!
1.92 enable pagination    

2. Authorization with CanCanCanAbilityAdapter :

3. Limit changes permissions to specific fields :


### Filters
1. by name
2. contains
3. id


### Important support only one field pagination

please see code 

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


#### Collection field and types:

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


