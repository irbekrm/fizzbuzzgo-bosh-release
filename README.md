# fizzbuzzgo-bosh-release

A Bosh release of a very simple [Go app](https://github.com/irbekrm/FizzBuzzGo). Created for practice purposes.

## Creating (this) Bosh release

1. `bosh init-release --dir fizzbuzzgo-bosh-release --git`

2. Link the source code of FizzBuzzGo app as a Git submodule. Since the app is a Go package, set the path to match Go import path for this package (`github.com/irbekrm/FizzBuzzGo`) to make it easier to build the app at compile time.

```
      cd fizzbuzzgo-bosh-release

      cd src

      git submodule add git@github.com:irbekrm/FizzBuzzGo.git github.com/irbekrm/FizzBuzzGo
      
      cd ..
```

3. This Bosh release has a single job- `fizzbuzzgo`.

`jobs/fizzbuzzgo/templates/ctl.erb` - job's control script. Defines start and stop commands for this job. Ensures logs and process ID being written to the correct files. This file is an [ERB template](https://en.wikipedia.org/wiki/ERuby)

`jobs/fizzbuzzgo/monit` - job's `monit` file. Bosh's Agent running on VM will start and stop this job using [Monit](https://mmonit.com/monit/)

`jobs/fizzbuzzgo/spec` - job's spec file. `templates` block specifies where on VM Bosh will place the file generated from `templates/ctl.erb` on the. (The location is relative to `/var/vcap/jobs/fizzbuzzgo`)

```
      bosh generate-job fizzbuzzgo

      touch jobs/fizzbuzzgo/templates/ctl.erb

      // Write the job's control script (`jobs/fizzbuzzgo/templates/ctl.erb`)

      // Write the job's `monit` file (`jobs/fizzbuzzgo/monit`)

      // Write the job's spec file (`jobs/fizzbuzzgo/spec`)
```



