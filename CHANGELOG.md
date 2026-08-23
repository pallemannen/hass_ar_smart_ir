# Changelog

All notable changes to this fork are documented here, starting from where
we took over maintenance. For history before that, see the original
[marsh4200/ar_smart_ir](https://github.com/marsh4200/ar_smart_ir).

## 1.8.1

- Fix reconfigure flow: `async_step_reconfigure` was copying the entire
  existing entry's data into `self._data`, including `controller_data`,
  which then survived untouched through the whole wizard. A controller
  that only needs the entity picker (e.g. Broadlink) would submit a fresh
  `controller_entity`, and the leftover `controller_data` would still be
  there too - falsely tripping the "enter a remote entity or an MQTT
  topic, not both" conflict check even though only one field was shown.

## 1.8.0

- Add a reconfigure flow - swap manufacturer/model/controller on an
  existing device (e.g. try a different codeset) without deleting and
  recreating it. Reachable via the "Reconfigure" action on the config
  entry; each step defaults to the entry's current value.

## 1.7.5

- First release under this fork. No functional changes from upstream
  v1.7.4 - links, badges, and the "archived" banner updated to point at
  this fork instead of the original.
