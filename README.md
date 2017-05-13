# Punchcard
## Minimal time tracking tool for cli

[![Build Status](https://travis-ci.org/pstaender/punchcard.svg?branch=master)](https://travis-ci.org/pstaender/punchcard)

### Requirements

  * ruby 2+
  * bash (maybe windows works, too?)

### Install

Choose your preferred filename and location:

```sh
  $ curl https://raw.githubusercontent.com/pstaender/punchcard/master/punchcard.rb > /usr/local/bin/punch
  $ chmod +x /usr/local/bin/punch
```

### Usage

#### Start Project

```sh
  $ punch start "Punchcard (programming)"
```

#### Wildcard

Save keystrokes by using wildcard. The last active project, which matches the pattern (case insensitive) will be selected:

```sh
  $ punch start "Punch*"
```

#### Stop Project

```sh
  $ punch stop "Punch*"
```

#### Toggle

Toggle between start and stop:

```sh
  $ punch toggle "Punch*"
```

#### Status

```sh
  $ punch status "Punch*"

    Punchcard (programming)
    01:10:09
```

#### List details

```sh
  $ punch details "Punch*"

    Punchcard (programming) (stopped)

    00:00:08	2017-05-07 08:16:06 - 2017-05-07 08:16:14
    00:04:35	2017-05-07 08:22:02 - 2017-05-07 08:26:37
    ...
    ========
    01:10:04	(total)
```

#### Set Hourly Rate

```sh
  $ punch set "Punch*" hourlyRate 250€
```

#### Total time in seconds

```sh
  $ punch total "Punch*"
```

#### List all projects with total time in CSV format

```sh
  $ punch all

    "project","status","last active on","total duration","hourly rate","earnings"
    "Website","stopped","2017-05-07 15:50:00","04:06:00","250.0 €","1025.00 €"
    "Punchcard (programming)","stopped","2017-07-11 12:47:42","01:10:04","",""
```

You can use `all` with any other action as well, e.g. `punch all stop` to stop all running projects

Hint: Use your favorite output formatter to get a nicer project summary of your choice; e.g. with [csv2md](https://www.npmjs.com/package/csv2md):

```sh
  $ punch all | csv2md --pretty

    | project                   | status  | last active on      | total duration | hourly rate | earnings |
    |---------------------------|---------|---------------------|----------------|-------------|----------|
    | Website                   | stopped | 2017-05-07 15:50:00 | 04:06:00       | 250.0 €     | 1025.0 € |
    | Punchcard (programming)   | stopped | 2017-05-07 12:47:42 | 01:10:04       |             |          |
```

### Store projects files in a custom folder and sync them between computers

By default, PunchCard will store the data in `~/.punchcard/`. Define your custom destination with:

```sh
  export PUNCHCARD_DIR=~/Nextcloud/punchcard
```


### Tests

```sh
  $ bundle exec rspec
```
