^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package sentor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

2.1.0 (2020-04-20)
------------------
* Merge pull request `#11 <https://github.com/LCAS/sentor/issues/11>`_ from adambinch/sentor_devel
  A significant change to the way sentor executes processes, and how args are specified in the config.
* The format of the config is now backwards compatible
  (sentor can handle two formats for the signal when condition).
  The lindsey config has been reverted back to the previous version.
* A few minor improvements
* No longer using separate timers to handle critical and non-critical lambda expressions.
  Reduces the number of threads used by sentor by the number of monitors specified in the config.
* The safety callback in the topic monitor is called in the run function, rather than a separate timer.
  Reduces the number of threads used by sentor by the number of monitors specified in the config.
* Merge branch 'master' of github.com:LCAS/sentor into sentor_devel
* Merge pull request `#12 <https://github.com/LCAS/sentor/issues/12>`_ from adambinch/fix
  fix
* fix
* Added authorships
* Adjustments to example config
* The hz monitor is instantiated only when needed.
* minor change
* Merge branch 'master' of github.com:LCAS/sentor into sentor_devel
* Merge pull request `#10 <https://github.com/LCAS/sentor/issues/10>`_ from adambinch/fix
  small fix
* Merge branch 'master' into fix
* small fix
* Merge branch 'master' of github.com:LCAS/sentor into sentor_devel
* Specifying process indices for the signal when condition, and for each lambda expression, is now
  the default method of executing processes.
  The signal when condition now has child args `condition` (published/not published),
  `timeout`, `safety_critical` `process_indices` and `repeat_exec`.
  Each lambda expression now has child args `expression`,
  `timeout`, `safety_critical` `when_published`, `process_indices` and `repeat_exec`.
* Merge pull request `#9 <https://github.com/LCAS/sentor/issues/9>`_ from adambinch/sentor_mapping
  Sentor can now map topic values.
* minor change
* Example config for the new features
* Added an alternative mode `alt_exec` for executing processes. For a topic monitor, each lambda
  expression listed now has an optional arg `process_indices` in which
  you can specify which set of process you want to execute when that particular
  lambda expression is satisfied.
* fix
* Added another process `reconf` - sentor can now dynamic reconfigure.
  Updated config.
  The hz monitor is now only instantiated when it is needed.
* fix
* Minoir change
* Topic map can now be built as the standard deviation of topic args.
  Added `stat` message field to custom topic map msg.
  Some restructuring and minor improvements.
* minor change
* Minor improvements.
* Added service `/sentor/get_maps` that returns all map data.
  Changed default publishing/plotting rate of maps to zero which disables publishing/plotting of maps.
  Changed the way the topic map is discretised as the previous method was causing the map to be displaced.
  Some structural changes and improvements to code.
* Merge branch 'sentor_mapping' of github.com:adambinch/sentor into sentor_mapping
* Auto safety tagging is set to True by default.
  Can now make topic maps with other statistics (min and max)
  A few minor improvements
* Auto safety tagging is set to True by default.
  A few minor improvements
* Created a topic map server to deal with writing/plotting the topic maps, and other services on the maps.
  The topic map can be now be a sum of the topic args (as well as the weighted mean).
  Real time plots (and the plot) rate, is now specified in the sentor launch file.
* Topic maps are now saved in `home/.sentor_maps`.
  Topic map message now gives extra information.
* Improvement to the way the topic map is discretised.
  Better example config.
  Generated example topic map, saved in `sentor/maps`.
* Default plotting rate is 1hz
* minor fix
* Sentor topic mapper can now generate real-time plots. New args in config.
* Created a class (TopicMapPublisher) for publishing topic maps.
  The services start/stop monitor now starts/stops the safety monitor, topic mapper and topic map publisher.
  Made a service `/sentor/write_maps` for writing topic maps
  Renamed messages `Map` and `MapArray` as `TopicMap` and `TopicMapArray`, respectively.
  All sentor services with srv `Empty` now return an empty response (`EmptyResponse`)
  Some other fixes and minor changes.
* Improvement to the way the topic mapper handles exceptions.
  Some other minor changes.
* Sentor can now map topic values.
  A numpy array is created as a discretized representation of the metric map.
  When a topic message is obtained, a user defined argument on the message is evaluated.
  A weighted mean of this value is stored in an element of the array, where the indices of the element is
  given by the 'map to baselink' tf transform. As more data from a location is gathered, the weighted mean
  (and thus the 'topic map'), is updated. Any region of this topic map that
  has not been explored will contain nans.
  Sentor can now store the weighted mean of a topic value in an element of an array.
  The index of the element corresponds to a location in the map.
  The index of the array is chosen by looking up the transform between map and baselink.
* Contributors: Adam Binch, adambinch

2.0.4 (2020-02-22)
------------------
* Merge pull request `#8 <https://github.com/LCAS/sentor/issues/8>`_ from adambinch/sentor_devel
  New top-level arg `lambdas_when_published` that ensures that lambda e…
* Simplified code a little. Small change to the readme.
* Made latest changes thread safe.
* updated readme
* Fix
* New top-level arg `lambdas_when_published` that ensures that lambda expressions
  can be satisfied only when the topic is being published.
* Merge pull request `#7 <https://github.com/LCAS/sentor/issues/7>`_ from adambinch/sentor_devel
  Sentor devel: New Features
* minor chnage to readme
* New Features:
  By setting the arg `auto_safety_tagging` (see `sentor.launch`) to True
  sentor will automatically set safe operation to True when all
  safety critical condition across all monitors are unsatisfied.
  If `auto_safety_tagging` is set to `False` then the (renamed) service
  `/sentor/set_safety_tag` must be called.
* The safety monitor will automatically set safe operation to True
  if all safety critical conditions across all monitors
  are not violated.
* Merge pull request `#6 <https://github.com/LCAS/sentor/issues/6>`_ from adambinch/sentor_devel
  Sentor devel: Safety critical conditions are now affected by the `repeat_exec` arg.
* Safety critical conditions are now affected by the `repeat_exec` arg.
* moved this to the rasberry repo
* start of sentor config for thorvald
* Merge pull request `#5 <https://github.com/LCAS/sentor/issues/5>`_ from adambinch/sentor_devel
  New top level arg added that allows you to turn off the default notif…
* New top level arg added that allows you to turn off the default notifications.
* Merge branch 'adambinch-sentor_devel'
* Updated README.md to reflect the previous change.
* The arg `topic_latched` for the process `publish` is now optional (default='True')
* The arg `repeat_exec` now works with the `signal_when` conditions, as well as the lambda expressions.
  Updated the README.md.
* minor change
* The `verbose` option for each process was meant to be optional but was not. Fixed now.
  Improvement to the README.md.
* README.md correction
* correction to README.md
* Updated the README.md and the argument descriptions in the config.
* New arg for each process `verbose`. Setting to False will limit notifications to errors
  whilst processes are executed.
  Expanded the default config `execute` to include a safety critical lambda condition.
  Tidied/removed unnecessary code.
* `repeat` is now a top level arg and has been renamed to `repeat_exec`.
  If true then all processes under `execute` will be executed repeatedly (every `timeout`) seconds
  whilst all lambda condition's are satisfied.
* Found a better way of repeating processes whilst lambdas are satisfied
* removed `oneshot` option as it was causing problems. Simplified code
* Improved the way errors are logged.
  New top level arg `include` in config. Set to false to not include that monitor,
  rather than commenting it out (for convenience).
* Fixed an issue that was causing processes to be executed immediately (without taking `timeout` into account).
  Previously, processes will be executed when the lambda conditions are satisfied. But they would not execute again unless they become unsatisfied, then satisfied again.
  This is desirable behaviour in a lot of cases but maybe not all. So we now have the option to execute repeatedly (every timeout seconds), whilst the lambda conditions are satisfied.
  See the new top level arg `oneshot` in the config.
* When executing a log you can now include data from the topic that
  is being monitored.
* Minor change
* minor change
* When sentor logs a call to a service it also logs the request.
  When sentor logs that a goal for an action has been sent it also logs the goal.
* When actionlib goals or service calls fail, those events are logged as warnings rather than errors.
* Removed `message` from process keywords in config and replaced with a new process `log`
  in which you can log messages.
* The `signal_when` condition in the config now also has a `safety_critical` tag.
  Added a new thread to the example config `execute.yaml`. This thread calls the service `/sentor/reset_safety_tag`.
  The key word `function` in the config has been changed to `expression`.
  A few minor improvements to code.
* Added missing package dependencies.
  Set default pub rate of the `/safe_operation` topic to 10 hz.
* You can now tag lambda expressions as `safety_critical`.
  A new topic `/safe_operation` will publish `True` if all safety critical
  lambda expressions are satisfied. If one is from any thread then
  the topic will publish false until a new service `/sentor/reset` is set to `True`.
  Due to the inclusion of the new tags the config `rob_lindsey.yaml` has been updated.
  It should still functions exactly the same as before.
* The optional arg `user_msg` has been changed to `message`.
  Important info added to the README.md
* The new features (publishing to topics, calling services etc) are now referred to as
  'processes' rather than 'actions' to avoid confusion with actionlib actions.
* Small chnage to the README.md
* correction to README.md
* correction to README.md
* Updated the README.md.
  Renamed arg in config to be consistent with the naming of others.
  Added arg descriptions to the config.
  A couple of minor improvements to code.
* Renamed config
  Removed unnecessary config
  Small improvement to code
* Correction
* Tested with a multi thread config (`multi_thread.yaml`). Seems to work fine.
  Shortened default log messages published to the `sentor/event` topic.
  When executing actions using a simple action server sentor now provided feedback on the goal.
  Renamed config.
  Ros logs made during sentor initialisation are no longer published to the `sentor/event` topic.
  Updated pacakge.xml
  To test with multi thread config simply launch the launch file `sentor.launch`.
  As before send the robot in simulation to WayPoint1. The robot will automatically navigate to
  WayPoint45. In the mean time sentor will execute a shell command `cowsay moo`. When the robot reaches its goal
  it will teleport back to x=0,y=0 and relocalise.
* Sentor can now execute basic shell commands using subprocess.
  Renamed and updated config.
  Needed to (rospy) sleep the sentor node in some places so that messages
  can published to slack (by slackeros).
  Some other minor changes.
* Minor changes
* Merge branch 'sentor_devel' of https://github.com/adambinch/sentor into sentor_devel
  # Conflicts:
  #	config/action.yaml
  #	src/sentor/Executor.py
* Sentor now publishes new events to the topic `/sentor/event`.
  Users can now set their own (string) messages to be publsihed to this topic.
  Removed some unnecessary stuff. Some minor changes.
* Sentor now publishes new events to the topic `/sentor/event`.
  Users can now set their own (string) messages to be publsihed to this topic.
  Removed some unnecessary stuff.
* Sentor can now make clients and send goals for any action type.
  Included the python package `math` in `ROSTopicFilter.py` so that
  it can be used in the lambda functions.
* Sentor can now publish to topics.
  Also, a new arg `lock_exec` in the config gives the option of locking out other threads
  while the current one is executing its sequence of actions.
* rospy sleep now included in set of actions.
  Tidied up my changes to `TopicMonitor`
* New top level arg `exec_once` in config. If True then actions will be
  executed only the first time that the signal conditions are met.
* correction
* correction
* correction
* Sentor can now call services
* Contributors: Adam Binch, Lindsey User, Marc Hanheide, adambinch

2.0.3 (2019-04-12)
------------------
* Merge pull request `#3 <https://github.com/LCAS/sentor/issues/3>`_ from francescodelduchetto/master
  fix some bugs
* Merge branch 'master' into master
* Merge branch 'master' of https://github.com/francescodelduchetto/sentor
* fix various errors
* Contributors: Lindsey User, Marc Hanheide

2.0.2 (2019-04-12)
------------------
* Merge pull request `#2 <https://github.com/LCAS/sentor/issues/2>`_ from francescodelduchetto/master
  update readme with description of config file usage
* rospy spin instead of 'handmade' spin
* print also the message together with the expression
* Merge branch 'master' into master
* Merge pull request `#1 <https://github.com/LCAS/sentor/issues/1>`_ from francescodelduchetto/2.0
  merge 2.0 to master
* Update README.md
* Update README.md
* Update README.md
* Update README.md
* Contributors: Marc Hanheide, francescodelduchetto

2.0.1 (2019-01-19)
------------------
* Merge pull request `#1 <https://github.com/LCAS/sentor/issues/1>`_ from LCAS/2.0
  Merging 2.0 into master with some modifications for release
* prepare for installation
* prettier prints and longer sleep in loop to avoid None in hz
* added timeout for lambdas and not published
* first commmit version 2.0: yaml file for configuration, singaling also for published, lambda funcs are specified in the yaml as a string
* ehm
* remove logs
* Merge branch 'master' of https://github.com/francescodelduchetto/sentor
* check log to be rem
* another small bit
* remove logs and madd another check to avoid duplicate msg expr in the same list
* some debug logs
* more waiting
* fix bug
* better handling of satsfied expressions as we don't drop anymore expression satisfied very close in time
* Update README.md
* gitignore
* comments and readme
* bug in list inserting elements
* monitoring either the frequency or the expression on msgs
* Merge branch 'master' of github.com:francescodelduchetto/sentor
* tab
* Update README.md
* warning message more significative
* Merge branch 'master' of github.com:francescodelduchetto/sentor
* comment
* elifs instead of ifs
* explanation on usage of filtering
* added possiblity to filter the value of messages and get a warning when it is satisfied
* slightly better printing
* only one warning message when the topic is not published anymore; better terminal printing
* Delete ROSTopicHz.pyc
* Update README.md
* Update README.md
* initial commit
* Contributors: Lindsey User, Marc Hanheide, francescodelduchetto
