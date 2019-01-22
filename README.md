# nextcloud_ics_sync

Python project to sync ics calendars into nextcloud.

Adapted from https://github.com/buzz/ics2owncloud.py .
 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

This project has been tested on CentOS 7.6 with nextcloud 14.x, google calendar and zimbra calendar.

```
Python        : 3.4.9
pip3          : 8.1.2
requests      : 2.9.1
icalendar     : 3.9.2
```

### Installing

You could either install requirements system wide or use virtual environment / conda, choose your poison.

To get this up and running you just need to do the following :

* Clone the repo
```bash
git clone https://github.com/MrBE4R/nextcloud_ics_sync.git
```
* Install requirements
```bash
pip3 install -r ./nextcloud_ics_sync/requirements.txt
```
* Edit config.json with you values
```bash
cp nextcloud_ics_sync/nextcloud_ics_sync.ini{.example,}
EDITOR ./nextcloud_ics_sync/nextcloud_ics_sync.ini
```
* Start the script and enjoy your calendars being synced
```bash
cd ./nextcloud_ics_sync && ./nextcloud_ics_sync.py
```

You should get something like this :
```bash
[XXXX-XX-XX XX:XX:XX,XXX] [INFO] Initializing script...
[XXXX-XX-XX XX:XX:XX,XXX] [INFO] Done.
[XXXX-XX-XX XX:XX:XX,XXX] [INFO] Importing calendars...
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]  Working on section import_a
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]   Working with calendar nextcloud_a...
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]    Imported: uuid (Event Name)
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]    Imported: uuid (Event Name)
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]    Imported: uuid (Event Name)
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]    Imported: uuid (Event Name)
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]   Done.
[XXXX-XX-XX XX:XX:XX,XXX] [INFO]  Done.
[XXXX-XX-XX XX:XX:XX,XXX] [INFO] Done.
```

You could add the script in a cron to run it periodically.

## Deployment

How to configure config.json
```ini
[DEFAULT]                                                                       # The nextcloud server where we will sync all calendar
username: username                                                              # Nextcloud username
password: password                                                              # Nextcloud password
server: https://nextcloud.example.com/                                          # Nextcloud URL

[import_a]                                                                      # a convenient name for you
calendar: calendar_xy                                                           # name of the calendar in nextcloud. must exist prior sync
ics_url: https://cloud.owncloud.org/index.php/apps/calendar/export.php?calid=6  # url to the ics file
ics_username :                                                                  # username of the distant ics server
ics_password :                                                                  # password of the distant ics server

[import_b]
calendar: zimbra
ics_url: https://zimbra.example.com/home/username/Calendar?fmt=ics
ics_username : 
ics_password : 

[import_c]
calendar: google
ics_url: https://calendar.google.com/calendar/ical/username/private-xxxxxxx/basic.ics
ics_username : 
ics_password : 
```
For now ```ics_username``` and ```ics_password``` are mandatory in each import, meaning the keys should be here but empty if not needed by the distant ics server.

## TODO

- [ ]  validate if ```ics_username``` and ```ics_password``` are in config to avoid putting empty value in config
- [ ]  your suggestions

## Built With

* [Python](https://www.python.org/)
* [icalendar](https://icalendar.readthedocs.io/en/latest/)
* [requests](http://docs.python-requests.org/en/latest/)

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

* **Jean-François GUILLAUME (Jeff MrBear)** - *Initial work* - [MrBE4R](https://github.com/MrBE4R)

See also the list of [contributors](https://github.com/MrBE4R/nextcloud_ics_sync/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* Hat tip to anyone whose code was used