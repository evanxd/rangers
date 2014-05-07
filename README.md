# Rangers
A  Web browser automation framework.

## Sample Code
The below code presents how to write test code for Gaia app with Rangers.
It is much easier than the https://github.com/mozilla-b2g/gaia/blob/master/apps/calendar/test/marionette/create_event_test.js test code existed in Gaia.
```
var EVENT_TITLE = 'Hello world!';

var rangers = new Rangers({ target: 'b2g-desktop', searchTimeout: 10000 }),
    eventTitle = '';

eventTitle = rangers
  .go('app://calendar.gaiamobile.org')
  .click('#time-header a[href="/event/add/"]')
  .click('#modify-event-view input[name="title"]')
  .type(EVENT_TITLE)
  .click('#modify-event-view .save')
  .click('#event-list:first-child')
  .select('#event-view .title .content')
  .waitForTextEqual(EVENT_TITLE)
  .text();

assert.equal(eventTitle, EVENT_TITLE);
```
