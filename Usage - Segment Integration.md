# ClientSuccess / Segment Integration

## Getting Started (for CSMs)

If your engineers have already setup Segment, adding Segment.io data to ClientSuccess is nice and simple. All you need to do is turn on the app integration.  

To turn on the app integration, do the following:

1. Go to the Segment integrations screen and toggle on the ClientSuccess integration.
2. Add your "ClientSuccess Tracking Id" and "ClientSuccess Tracking API Key" (these can be found within ClientSuccess under the top right menu, Apps & Integrations > Usage).

<br />
NOTE: Because ClientSuccess focuses on group level events, you must pass group information before your events will show up. If you turn on the ClientSuccess integration in Segment and don't see events in ClientSuccess after 24 hours, it may be that your engineers need to send group information to Segment using Segment's `group` call.  

<br />
- - -

## Getting Started (for Devs)

ClientSuccess supports the `identify`, `group`, `track`, and `page` methods of Segment.

The `group` method is required for any data to stick in ClientSuccess. Any `track` and `page` events fired before the `group` method is called for a particular user, will be lost.  


#### Identify

When you `identify` a user, Segment will pass that user's information to ClientSuccess with `userId` as an external user Id for ClientSuccess usage. ClientSuccess uses the following of Segment's standard user profile fields (in parentheses): 

- `firstName` (`first_name`)
- `lastName` (`last_name`)

All other `identify` traits will be sent to ClientSuccess as custom attributes and will be ignored.


#### Group

When you call `group`, Segment will send that group's information to ClientSuccess with `groupId` as the id and `traits.name` as the group name. Both `groupId` and `traits.name` are required for ClientSuccess. As with `identify`, all other `group` traits will be ignored.

For `groupId`, you should send an identifier that is unique to the group (or client). This will be used to match usage events from individual users to specific groups (or clients), so the data can be aggregated.


#### Track

When you `track` an event, Segment will send that event to ClientSuccess as a custom event. ClientSuccess focuses only on group and user-level events, any event without a `userId` (`user_id`) is completely ignored by ClientSuccess and will not show up in our reporting.

ClientSuccess reports include a value for each tracked event. Our segment integration uses the number from `properties.value` as the `value` in ClientSuccess reports (see [Segment's docs](https://segment.com/docs/spec/track/#properties)). You can override this by passing `properties.csValue` with each `track` event. If neither of these is set, then `value` is set to 1 so that ClientSuccess reporting tracks the number of times that event happens (as is common for a pageview or other simple event).


#### Page

When you track a `page` event, Segment will send that event to ClientSuccess as a custom event. As with `Track` calls, any event without a `userId` (`user_id`) is completely ignored by ClientSuccess and will not show up in our reporting.
