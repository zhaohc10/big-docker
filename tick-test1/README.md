# GoLang MeetUp Milano - TICK Stack
Summary of the talk held at the GoLang Meetup TICK event.


## Demo
### Launch TICK stack via docker-compose
```bash
$ docker-compose up -d
```

### Add the cpu_alert task
```bash
$ docker-compose run kapacitor-cli
$ kapacitor define cpu_alert -type stream -tick /var/lib/kapacitor/tasks/cpu_alert.tick -dbrp kapacitor_example.autogen
```

Now, test the cpu_alert task (remember to save the returned id):

```bash
$ kapacitor record stream -task cpu_alert -duration 20s
$ <randomid>
$ kapacitor replay -recording <randomid> -task cpu_alert
```

You should see a new log into the `kapacitor` folder called `alerts.log`
