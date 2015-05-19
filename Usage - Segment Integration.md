# ClientSuccess / Segment Integration

## Setup Process (for CSMs)

If your engineers have already setup Segment, adding Segment.io data to ClientSuccess is nice and simple. All you need to do is turn on the app integration.  

To turn on the app integration, do the following:

1. Go to the Segment integrations screen and toggle on the ClientSuccess integration.
2. Add your "ClientSuccess Tracking Id" and "ClientSuccess Tracking API Key" (these can be found within ClientSuccess under the top right menu, Apps & Integrations > Usage).

<br />
NOTE: Because ClientSuccess focuses on group level events, you must pass group information before your events will show up. If you turn on the ClientSuccess integration in Segment and don't see events in ClientSuccess after 24 hours, it may be that your engineers need to send group information to Segment using Segment's `group` call.  

<br />
- - -

## Info for Developers

ClientSuccess supports the `identify`, `group`, `track`, and `page` methods of Segment.

The `group` method is required for any data to stick in ClientSuccess. Any `track` and `page` events fired before the `group` method is called for a particular user, will be lost.  


## Identify

When you `identify` a user, Segment will pass that user's information to ClientSuccess with `userId` as an external user Id for ClientSuccess usage. ClientSuccess uses the following of Segment's standard user profile fields (in parentheses): 

- `firstName` (`first_name`)
- `lastName` (`last_name`)

All other traits will be sent to ClientSuccess as custom attributes and may be ignored.


## Group

When you call `group`, Segment will send that group's information to ClientSuccess with `groupId` as the id and `name` as the group name.  Both `groupId` and `name` are required for ClientSuccess.


## Track

When you `track` an event, Segment will send that event to ClientSuccess as a custom event.


## Page

When you track a `page` event, Segment will send that event to ClientSuccess as a custom event.
