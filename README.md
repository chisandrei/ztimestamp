# ZTimestamp

[![CI](https://github.com/svenvc/ztimestamp/actions/workflows/CI.yml/badge.svg)](https://github.com/svenvc/ztimestamp/actions/workflows/CI.yml)

I am ZTimestamp.


I am a Magnitude.


I represent a point in time, a combination of a date and a time.


I am an alternative for DateAndTime and TimeStamp.  
I have nanosecond precision and live in the UTC/GMT/Zulu timezone.  
I use ISO/International conventions and protocols only.   
I support some essential arithmetic.  

I have an efficient internal representation:

	jnd - the julian day number <SmallInteger>
	ns - the number of nanoseconds since midnight, the beginning of the day <SmallInteger>

Examples:

	ZTimestamp now.
	ZTimestamp fromString: '1969-07-20T20:17:40Z'.
	ZTimestamp fromString: '2021-11-17T09:05:12.94603Z'.

There is some compatibility with existing, standard Chronology objects.
I correctly parse representations with a timezone designator
and can print a representation in arbitrary timezone offsets. 

The key idea of ZTimestamp is to store and work with timestamps in UTC internally, 
while converting to and from specific local representations when needed interfacing with the user or other systems.

ZTimestampFormat, working with ZTimezone, is the tool to do these conversions.

	ZCurrentTimezone
	  value: (ZTimezone id: #'Europe/Brussels')
	  during: [ ZTimestampFormat isoTZ useCurrentTimezone format: ZTimestamp now ].


## Time Zone Database

ZTimezone adds proper timezone support based on the standard Olsen Timezone database. 

- http://en.wikipedia.org/wiki/Tz_database
- https://www.iana.org/time-zones

The necessary information will be loaded, parsed and cached from a binary file of the zoneinfo database (see also man tzfile). This should work automagically on macOS and Unix, on Windows you have to download the necessary files and specify their location although there is a fallback that downloads the dataset (see #downloadFallbackZoneinfoDataset)

Latest data: [tzdata-latest.tar.gz](https://www.iana.org/time-zones/repository/tzdata-latest.tar.gz)

Github repository: https://github.com/eggert/tz


## Formatting & Parsing

Also contains ZTimestampFormat, a 'by example' formatter/parser for DateAndTime, TimeStamp, Date, Time and ZTimestamp.


## SNTP

Also contains ZTimestampSNTPClient, a simple SNTP client to check your local clock.


## Installation

This is a [Pharo Smalltalk](http://wwww.pharo.st) project 
using the [Tonel](https://github.com/pharo-vcs/tonel) source code format.

In Pharo 7 and up you can use Iceberg to load this project.

You can also load using the following expression:

    Metacello new
      baseline: 'ZTimestamp';
      repository: 'github://svenvc/ztimestamp';
      load.

There is also a ZTimestamp-GT package with extensions for GToolkit, which can be loaded with the 'gt' group.

Written and supported by Sven Van Caekenberghe. MIT Licensed.
