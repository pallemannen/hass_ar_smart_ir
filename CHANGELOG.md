# Changelog

All notable changes to this fork are documented here, starting from where
we took over maintenance. For history before that, see the original
[marsh4200/ar_smart_ir](https://github.com/marsh4200/ar_smart_ir).

## Unreleased

- Add a device-wide repeat: every command that does not set its own repeat
  count or delay is sent that many times, that far apart. Useful when a
  device sometimes misses a command. Per-command repeat settings and
  codesets that set `num_repeats` keep working as before; the default is 1,
  so nothing changes until it is raised.
- Learning a code no longer pins the command to a single send: a learned
  code follows the device-wide repeat, unless the command already had its
  own repeat settings, which are now kept.

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
