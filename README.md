# Extract US Cities

This project uses Natural Language Processing techniques to identify US cities in a body of text.  

The goal of this project is high precision identification vs. loose identification.  So you won't get matches for Cities that don't have any refining context surrounding them.  

Examples:
"Brandon went to the park." 
This won't return results because even though there are several cities names Brandon there no context indicating it's a place.

"Some interesting things happened in Charlotte today."
This also won't return results even though we know Charlotte is a place (unless interesting things are happening inside of a person named Charlotte which would be strange BUT possible I guess).  This is because we don't have enough context to know which Charlotte it is.  Is it Charlotte, MI or Charlotte, TX or... (this list goes on).

Ultimately we need enough local context to narrow the it down to one match.

## Installation

Extract US Cities is available as an [npm package](https://www.npmjs.org/package/extract-us-cities).

```sh
npm install extract-us-cities
```

## Usage
```javascript
const { extract } = require('extract-us-cities');

const string = 'A string with a US city in it like Appleton WI, 54911';
const result = extract(string);
/* result = [
  {
    city: 'Appleton',
    state_code: 'WI',
    state_name: 'Wisconsin',
    county_name: 'Outagamie',
    lat: 44.2774,
    lng: -88.3894,
    incorporated: true,
    timezone: 'America/Chicago',
    foundState: true,
    end: 53,
    foundZip: true,
    zip: '54911',
    start: 35,
  },
];
*/
```

## Issues
I'm not perfect so when you find bugs please post them on the 
[github issue](https://github.com/Cleanshooter/extract-us-city/issues) tracker.

## Contribute
PRs are welcome, please ensure you've run and possibly added some more test cases.

### Benchmarking 
On my Dell XP 15 it currently takes 49,967 ms to process "Pride and Prejudice" by Jane Austen.  
Which isn't bad (less than a minute) but I'm open to ideas on how to improve processing time.

## License
This project is licensed under the terms of the ISC license
