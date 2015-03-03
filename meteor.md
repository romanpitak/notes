# Meteor

## Directory structure

    lib/                      # common code like collections and utilities
    lib/methods.js            # Meteor.methods definitions
    lib/constants.js          # constants used in the rest of the code

    client/compatibility      # legacy libraries that expect to be global
    client/lib/               # code for the client to be loaded first
    client/lib/helpers.js     # useful helpers for your client code
    client/body.html          # content that goes in the <body> of your HTML
    client/head.html          # content for <head> of your HTML: <meta> tags, etc
    client/style.css          # some CSS code
    client/<feature>.html     # HTML templates related to a certain feature
    client/<feature>.js       # JavaScript code related to a certain feature

    server/lib/permissions.js # sensitive permissions code used by your server
    server/publications.js    # Meteor.publish definitions

    public/favicon.ico        # app icon

    settings.json             # configuration data to be passed to meteor --settings
    mobile-config.js          # define icons and metadata for Android/iOS

### Special Directories

- client
- server
- public
- private
- client/compatibility
- tests

Special client, server, and lib directories work if they are **anywhere in the path**, you can use top-level folders to organize code into modules.

## Collections

### Data and security

server: publish all messages for a given room

    Meteor.publish("messages", function (roomId) {
      check(roomId, String);
      return Messages.find({room: roomId});
    });

server: publish the set of parties the logged-in user can see.

    Meteor.publish("parties", function () {
      return Parties.find({$or: [{"public": true},
                                 {invited: this.userId},
                                 {owner: this.userId}]});
    });

server: don't allow client to insert a party

    Parties.allow({
      insert: function (userId, party) {
        return false;
      }
    });

#### Types

The check call will throw an error if its argument is of an unexpected type.

    check(username, String)
    check(office, {building: String, room: Number})

Force argument checks

    meteor add audit-argument-checks

and any method or publish function which skips checking any of its arguments
will fail with an exception

## Reactivity

    Tracker.autorun(function () {
      Meteor.subscribe("messages", Session.get("currentRoomId"));
    });

sets up a data subscription based on the session variable currentRoomId. If the value of Session.get("currentRoomId") changes for any reason, the function will be automatically re-run, setting up a new subscription that replaces the old one

reactive functions:

- Templates
- Tracker.autorun
- Blaze.render
- Blaze.renderWithData

reactive data sources:

- Session variables
- Database queries on Collections
- Meteor.status
- The ready() method on a subscription handle
- Meteor.user
- Meteor.userId
- Meteor.loggingIn
