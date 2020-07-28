# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

* [`swap`](#swap): Set the swappiness of the system either by a cron job or as an absolute value.

## Classes

### swap

The cron job is run every 5 minutes by default. Using the cron job doesn't
really make a lot of sense unless it is run reasonably often. Therefore, only
minute steps are supported per crontab(5).

An absolute value setting will always override the cron job.

#### Parameters

The following parameters are available in the `swap` class.

##### `swappiness`

Data type: `Integer[0,100]`

Set the system to run at this swappiness and do not adjust. Take care,
whatever value you place in here used **as-is**!

Default value: 60

##### `dynamic_script`

Data type: `Boolean`

Place the dynamic_swappiness script on the system and enable it.

* This can be useful, particularly in situations where you are
  oversubscribing VMs. However, most systems will rely on static measures.

Default value: `false`

##### `cron_step`

Data type: `Integer[0,59]`

The crontab(5) minute step value for the swappiness set.

* Has no effect if `$dynamic_script` is `false`

Default value: 5

##### `maximum`

Data type: `Integer[0,100]`

The percentage of memory free on the system above which we will set
vm.swappiness to $min_swappiness

* Has no effect if `$dynamic_script` is `false`

Default value: 30

##### `median`

Data type: `Integer[0,100]`

If the percentage of free memory on the system is between this number and
`$maximum`, set `vm.swappiness` to `$low_swappiness`.

* Has no effect if `$dynamic_script` is `false`

Default value: 10

##### `minimum`

Data type: `Integer[0,100]`

If the percentage of free memory on the system is between this number and
`$median`, set `vm.swappiness` to `$high_swappiness`. If below this number,
set to `$max_swappiness`.

* Has no effect if `$dynamic_script` is `false`

Default value: 5

##### `min_swappiness`

Data type: `Integer[0,100]`

The minimum swappiness to ever set on the system.

* Has no effect if `$dynamic_script` is `false`

Default value: 5

##### `low_swappiness`

Data type: `Integer[0,100]`

The next level of swappiness to jump to on the system.

* Has no effect if `$dynamic_script` is `false`

Default value: 20

##### `high_swappiness`

Data type: `Integer[0,100]`

The medium-high level of swappiness to set on the sysetm.

* Has no effect if `$dynamic_script` is `false`

Default value: 40

##### `max_swappiness`

Data type: `Integer[0,100]`

The absolute maximum to ever set the swappiness on the system.

* Has no effect if `$dynamic_script` is `false`

Default value: 80
