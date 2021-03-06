# [Master][]

## Fixed

- [#203][]: Fix a bug that prevented transaction options from being passed to
  subclasses.

# [1.2.3][] (2014-05-12)

## Fixed

- [#192][]: Fix a bug that raised `ActiveRecord::Rollback` when composing even
  when not in a transaction.

# [1.2.2][] (2014-05-07)

## Fixed

- Fix a bug that raised `NameError`s when there were invalid nested hash
  errors.
- Add missing translation for symbol filters.

# [1.2.1][] (2014-05-02)

## Fixed

- [#179][]: Fix a bug that marked model inputs as invalid even if they returned true
  for `object.is_a?(klass)`.

# [1.2.0][] (2014-04-30)

## Added

- [#175][]: Add support for Rails-style date and time parameters like `date(1i)`.
- [#173][]: Add a decimal filter.
- [#155][]: Add support for disabling and modifying transactions through the
  `transaction` helper method.
- [#140][]: Add support for `column_for_attribute` which provides better
  interoperability with gems like Formtastic and Simple Form.

# [1.1.7][] (2014-04-30)

## Fixed

- [#174][]: Fix a bug that leaked validators among all child classes.

# [1.1.6][] (2014-04-29)

## Fixed

- [#36][]: Fix a bug that caused nested hash error messages to be misleading.

# [1.1.5][] (2014-03-31)

## Fixed

- The `transform_keys` method broke backwards compatibility because it's not
  available until Rails 4.0.2.

# [1.1.4][] (2014-03-31)

## Fixed

- Fix an issue where non-stripped hash keys would be incorrectly converted to strings.

# [1.1.3][] (2014-03-31)

## Fixed

- [#165][]: Fix Rubocop errors and pin the version to avoid future issues with new cops
  breaking the build.

## Security

- [#163][]: Fix some denial of service attacks via hash symbolization.

# [1.1.2][] (2014-03-05)

## Fixed

- [#156][]: Don't constantize classes for model filters on initialization. This fixes a
  bug that made those filters dependent on load order.

# [1.1.1][] (2014-03-04)

## Fixed

- [#153][]: Allow merging ActiveModel errors into ActiveInteraction errors with
  `ActiveInteraction::Errors#merge!`.

# [1.1.0][] (2014-02-28)

## Added

- [#116][], [#119][], [#122][]: Speed up many filters by caching class constants.
- [#115][]: Add support for callbacks around `execute`.
- [#136][]: Allow callable defaults.

## Changed

- [#114][]: Support `:only` and `:except` options simultaneously with `import_filters`.
  Previously this raised an `ArgumentError`.
- [#114][]: Support passing a single symbol to `:only` and `:except`. Previously an Array
  was required.

## Security

- [#138][]: Only set instance variables for attributes with readers defined.


# [1.0.5][] (2014-02-25)

## Fixed

- [#143][]: Rollback database changes when `compose` fails.

# [1.0.4][] (2014-02-11)

## Fixed

- Add translations to the gem specification.

# ~~[1.0.3][] (2014-02-11)~~

## Fixed

- [#135][]: Fix a bug that caused invalid strings to be parsed as `nil` instead of
  raising an error when `Time.zone` was set.
- [#134][]: Fix bug that prevented loading I18n translations.

# [1.0.2][] (2014-02-07)

## Fixed

- [#130][]: Stop creating duplicate errors on subsequent calls to `valid?`.

# [1.0.1][] (2014-02-04)

## Fixed

- [#125][]: Short circuit `valid?` after successfully running an interaction.
- [#129][]: Fix a bug that prevented merging interpolated symbolic errors.
- [#128][]: Use `:invalid_type` instead of `:invalid` as I18n key for type errors.
- [#127][]: Fix a bug that skipped setting up accessors for imported filters.

# [1.0.0][] (2014-01-21)

## Added

- [#102][]: Add predicate methods for checking if an input was passed.
- [#103][]: Allow fetching filters by name.
- [#104][]: Allow import filters from another interaction with `import_filters`.

## Changed

- [#111][]: Replace `Filters` with a hash. To iterate over `Filter` objects, use
  `Interaction.filters.values`.
- Rename `Filter#has_default?` to `Filter#default?`.

## Fixed

- [#98][]: Add `respond_to_missing?` to complement `method_missing` calls.
- [#106][]: When adding a filter that shares a name with an existing filter, it will now
  replace the existing one instead of adding a duplicate.

# [0.10.2][] (2014-01-02)

## Fixed

- [#94][]: Fix a bug that marked Time instances as invalid if Time.zone was set.

# [0.10.1][] (2013-12-20)

## Fixed

- [#90][]: Fix bug that prevented parsing strings as times when ActiveSupport was
  available.

# [0.10.0][] (2013-12-19)

## Added

- Support casting "true" and "false" as booleans.

## Fixed

- [#89][]: Fix bug that allowed subclasses to mutate the filters on their superclasses.

# [0.9.1][] (2013-12-17)

## Fixed

- [#84][]: Fix I18n deprecation warning.
- [#82][]: Raise `ArgumentError` when running an interaction with non-hash inputs.
- [#77][]: For compatibility with `ActiveRecord::Errors`, support indifferent access of
  `ActiveInteraction::Errors`.
- [#88][]: Fix losing filters when using inheritance.

# [0.9.0][] (2013-12-02)

## Added

- Add experimental composition implementation (`ActiveInteraction::Base#compose`).

## Removed

- Remove `ActiveInteraction::Pipeline`.

# [0.8.0][] (2013-11-14)

## Added

- [#44][], [#45][]: Add ability to document interactions and filters.

# [0.7.0][] (2013-11-14)

## Added

- [#41][]: Add ability to chain a series of interactions together with
  `ActiveInteraction::Pipeline`.

# [0.6.1][] (2013-11-14)

## Fixed

- Re-release. Forgot to merge into master.

# ~~[0.6.0][] (2013-11-14)~~

## Added

- Add ability to introspect interactions with `filters`.
- [#57][]: Allow getting all of the user-supplied inputs in an interaction with
  `inputs`.
- [#61][]: Add a symbol filter.
- [#58][]: Allow adding symbolic errors with `errors.add_sym` and retrieving them with
  `errors.symbolic`.

## Changed

- Error class now end with `Error`.
- By default, strip unlisted keys from hashes. To retain the old behavior,
  set `strip: false` on a hash filter.
- [#49][]: Prevent specifying defaults (other than `nil` or `{}`) on hash filters. Set
  defaults on the nested filters instead.
- [#66][]: Replace `allow_nil: true` with `default: nil`.

## Fixed

- Fix bug that prevented listing multiple attributes in a hash filter.
- Fix bug that prevented hash filters from being nested in array filters.

# [0.5.0][] (2013-10-16)

## Added

- [#34][]: Allow adding errors in `execute` method with `errors.add`.

## Fixed

- [#56][]: Prevent manually setting the outcome's result.

# [0.4.0][] (2013-08-15)

## Added

- Support i18n translations.

# [0.3.0][] (2013-08-07)

## Added

- [#30][]: Allow nested default values.

## Changed

- [#36][]: Give better error messages for nested attributes.
- [#39][]: Add a more useful invalid interaction error message.
- [#38][]: Use default value when given an explicit `nil`.

# [0.2.2][] (2013-08-07)

## Fixed

- [#40][]: Fix support for `ActiveSupport::TimeWithZone`.

# [0.2.1][] (2013-08-06)

## Fixed

- [#37][]: Fix setting a default value on more than one attribute at a time.

# [0.2.0][] (2013-07-16)

## Added

- [#23][]: Add support for strptime format strings on Date, DateTime, and Time filters.

## Changed

- [#20][]: Wrap interactions in ActiveRecord transactions if they're available.
- [#24][]: Add option to strip string values, which is enabled by default.

# [0.1.3][] (2013-07-16)

## Fixed

- Fix bug that prevented `attr_accessor`s from working.
- Handle unconfigured timezones.
- [#27][]: Use RDoc as YARD's Markdown provider instead of kramdown.

# [0.1.2][] (2013-07-14)

## Fixed

- [#29][]: `execute` will now have the filtered version of the values passed
  to `run` or `run!` as was intended.

# [0.1.1][] (2013-07-13)

## Fixed

- [#28][]: Correct gemspec dependencies on activemodel.

# ~~[0.1.0][] (2013-07-12)~~

- Initial release.

  [master]: https://github.com/orgsync/active_interaction/compare/v1.2.3...master
  [1.2.3]: https://github.com/orgsync/active_interaction/compare/v1.2.2...v1.2.3
  [1.2.2]: https://github.com/orgsync/active_interaction/compare/v1.2.1...v1.2.2
  [1.2.1]: https://github.com/orgsync/active_interaction/compare/v1.2.0...v1.2.1
  [1.2.0]: https://github.com/orgsync/active_interaction/compare/v1.1.7...v1.2.0
  [1.1.7]: https://github.com/orgsync/active_interaction/compare/v1.1.6...v1.1.7
  [1.1.6]: https://github.com/orgsync/active_interaction/compare/v1.1.5...v1.1.6
  [1.1.5]: https://github.com/orgsync/active_interaction/compare/v1.1.4...v1.1.5
  [1.1.4]: https://github.com/orgsync/active_interaction/compare/v1.1.3...v1.1.4
  [1.1.3]: https://github.com/orgsync/active_interaction/compare/v1.1.2...v1.1.3
  [1.1.2]: https://github.com/orgsync/active_interaction/compare/v1.1.1...v1.1.2
  [1.1.1]: https://github.com/orgsync/active_interaction/compare/v1.1.0...v1.1.1
  [1.1.0]: https://github.com/orgsync/active_interaction/compare/v1.0.5...v1.1.0
  [1.0.5]: https://github.com/orgsync/active_interaction/compare/v1.0.4...v1.0.5
  [1.0.4]: https://github.com/orgsync/active_interaction/compare/v1.0.3...v1.0.4
  [1.0.3]: https://github.com/orgsync/active_interaction/compare/v1.0.2...v1.0.3
  [1.0.2]: https://github.com/orgsync/active_interaction/compare/v1.0.1...v1.0.2
  [1.0.1]: https://github.com/orgsync/active_interaction/compare/v1.0.0...v1.0.1
  [1.0.0]: https://github.com/orgsync/active_interaction/compare/v0.10.2...v1.0.0
  [0.10.2]: https://github.com/orgsync/active_interaction/compare/v0.10.1...v0.10.2
  [0.10.1]: https://github.com/orgsync/active_interaction/compare/v0.10.0...v0.10.1
  [0.10.0]: https://github.com/orgsync/active_interaction/compare/v0.9.1...v0.10.0
  [0.9.1]: https://github.com/orgsync/active_interaction/compare/v0.9.0...v0.9.1
  [0.9.0]: https://github.com/orgsync/active_interaction/compare/v0.8.0...v0.9.0
  [0.8.0]: https://github.com/orgsync/active_interaction/compare/v0.7.0...v0.8.0
  [0.7.0]: https://github.com/orgsync/active_interaction/compare/v0.6.1...v0.7.0
  [0.6.1]: https://github.com/orgsync/active_interaction/compare/v0.6.0...v0.6.1
  [0.6.0]: https://github.com/orgsync/active_interaction/compare/v0.5.0...v0.6.0
  [0.5.0]: https://github.com/orgsync/active_interaction/compare/v0.4.0...v0.5.0
  [0.4.0]: https://github.com/orgsync/active_interaction/compare/v0.3.0...v0.4.0
  [0.3.0]: https://github.com/orgsync/active_interaction/compare/v0.2.2...v0.3.0
  [0.2.2]: https://github.com/orgsync/active_interaction/compare/v0.2.1...v0.2.2
  [0.2.1]: https://github.com/orgsync/active_interaction/compare/v0.2.0...v0.2.1
  [0.2.0]: https://github.com/orgsync/active_interaction/compare/v0.1.3...v0.2.0
  [0.1.3]: https://github.com/orgsync/active_interaction/compare/v0.1.2...v0.1.3
  [0.1.2]: https://github.com/orgsync/active_interaction/compare/v0.1.1...v0.1.2
  [0.1.1]: https://github.com/orgsync/active_interaction/compare/v0.1.0...v0.1.1
  [0.1.0]: https://github.com/orgsync/active_interaction/compare/62f999b...v0.1.0

  [#20]: https://github.com/orgsync/active_interaction/issues/20
  [#23]: https://github.com/orgsync/active_interaction/issues/23
  [#24]: https://github.com/orgsync/active_interaction/issues/24
  [#27]: https://github.com/orgsync/active_interaction/issues/27
  [#28]: https://github.com/orgsync/active_interaction/issues/28
  [#29]: https://github.com/orgsync/active_interaction/issues/29
  [#30]: https://github.com/orgsync/active_interaction/issues/30
  [#34]: https://github.com/orgsync/active_interaction/issues/34
  [#36]: https://github.com/orgsync/active_interaction/issues/36
  [#37]: https://github.com/orgsync/active_interaction/issues/37
  [#38]: https://github.com/orgsync/active_interaction/issues/38
  [#39]: https://github.com/orgsync/active_interaction/issues/39
  [#40]: https://github.com/orgsync/active_interaction/issues/40
  [#41]: https://github.com/orgsync/active_interaction/issues/41
  [#44]: https://github.com/orgsync/active_interaction/issues/44
  [#45]: https://github.com/orgsync/active_interaction/issues/45
  [#49]: https://github.com/orgsync/active_interaction/issues/49
  [#56]: https://github.com/orgsync/active_interaction/issues/56
  [#57]: https://github.com/orgsync/active_interaction/issues/57
  [#58]: https://github.com/orgsync/active_interaction/issues/58
  [#61]: https://github.com/orgsync/active_interaction/issues/61
  [#66]: https://github.com/orgsync/active_interaction/issues/66
  [#77]: https://github.com/orgsync/active_interaction/issues/77
  [#82]: https://github.com/orgsync/active_interaction/issues/82
  [#84]: https://github.com/orgsync/active_interaction/issues/84
  [#88]: https://github.com/orgsync/active_interaction/issues/88
  [#89]: https://github.com/orgsync/active_interaction/issues/89
  [#90]: https://github.com/orgsync/active_interaction/issues/90
  [#94]: https://github.com/orgsync/active_interaction/issues/94
  [#98]: https://github.com/orgsync/active_interaction/issues/98
  [#102]: https://github.com/orgsync/active_interaction/issues/102
  [#103]: https://github.com/orgsync/active_interaction/issues/103
  [#104]: https://github.com/orgsync/active_interaction/issues/104
  [#106]: https://github.com/orgsync/active_interaction/issues/106
  [#111]: https://github.com/orgsync/active_interaction/issues/111
  [#114]: https://github.com/orgsync/active_interaction/issues/114
  [#115]: https://github.com/orgsync/active_interaction/issues/115
  [#116]: https://github.com/orgsync/active_interaction/issues/116
  [#119]: https://github.com/orgsync/active_interaction/issues/119
  [#122]: https://github.com/orgsync/active_interaction/issues/122
  [#125]: https://github.com/orgsync/active_interaction/issues/125
  [#127]: https://github.com/orgsync/active_interaction/issues/127
  [#128]: https://github.com/orgsync/active_interaction/issues/128
  [#129]: https://github.com/orgsync/active_interaction/issues/129
  [#130]: https://github.com/orgsync/active_interaction/issues/130
  [#134]: https://github.com/orgsync/active_interaction/issues/134
  [#135]: https://github.com/orgsync/active_interaction/issues/135
  [#136]: https://github.com/orgsync/active_interaction/issues/136
  [#138]: https://github.com/orgsync/active_interaction/issues/138
  [#140]: https://github.com/orgsync/active_interaction/issues/140
  [#143]: https://github.com/orgsync/active_interaction/issues/143
  [#153]: https://github.com/orgsync/active_interaction/issues/153
  [#155]: https://github.com/orgsync/active_interaction/issues/155
  [#156]: https://github.com/orgsync/active_interaction/issues/156
  [#163]: https://github.com/orgsync/active_interaction/issues/163
  [#165]: https://github.com/orgsync/active_interaction/issues/165
  [#173]: https://github.com/orgsync/active_interaction/issues/173
  [#174]: https://github.com/orgsync/active_interaction/issues/174
  [#175]: https://github.com/orgsync/active_interaction/issues/175
  [#179]: https://github.com/orgsync/active_interaction/issues/179
  [#192]: https://github.com/orgsync/active_interaction/issues/192
  [#203]: https://github.com/orgsync/active_interaction/issues/203
