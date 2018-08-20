# Changelog


## 5.0.0

### Added

- A new `check_rate_inc` function, which allows the caller to specify the
  integer with which to increment the bucket by. This is useful for limiting
  APIs which have some notion of "cost" per call.


## 4.0.0

## Changed

- Use a worker-pool for the backend (via poolboy),
  this avoids bottle-necking all traffic through a single hammer
  process, thus improving throughput for the system overall

## Added

- New configuration options for backends:
  - `:pool_size`, determines the number of workers in the pool (default 4)
  - `:pool_max_overflow`, maximum extra workers to be spawned when the
    system is under pressure (default 4)
- Multiple instances of the same backend! You can now have two ETS backends,
  fifteen Redis's, whatever you want


## 3.0.0

### Changed

- Require elixir >= 1.6
- Use a more sane supervision tree structure


## 2.1.0

### Changed

- Add option to use more than one backend
- Add option to suppress all logging


## 2.0.0

### Changed

- New, simpler API
  - No longer need to start backend processes manually
  - Call `Hammer.check_rate` directly, rather than `use`ing a macro
- Hammer is now an OTP application, configured via `Mix.Config`


## 1.0.0

### Added
- Formalise backend API in `Hammer.Backend` behaviour


## 0.2.1

### Changed

- Minor fixes
