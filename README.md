# os2display administrator interface

For documentation for this specific installation see [SPECIFICS.md](SPECIFICS.md)

For general information about installation see the [installation guide](https://github.com/os2display/docs/blob/master/installation/Installation%20guide.md) in the docs repository.

## Information
When working with os2display together with the vagrant provided, you have to visit screen.os2display.vm, search.os2display.vm, middleware.os2display.vm, admin.os2display.vm and accept the self-sign certificates. If you don't open a tab for each in Chrome, it will not work.

## Helpful commands
We have defined a couple of commands for os2display.

To push content:
```
php app/console ik:push
```

To reindex search:
```
php app/console ik:reindex
```
This does not include deletion of records that are removed from symfony but not search.

To clear cache:
```
php app/console cache:clear
```

To brute force clear cache:
```
rm -rf app/cache/*
```


## API tests

Clear out the acceptance test cache and set up the database:

```
app/console --env=acceptance cache:clear
app/console --env=acceptance doctrine:database:create
```

Run API tests:

```
./vendor/behat/behat/bin/behat --suite=api_features
```

Run only tests with a specific tag:

```
./vendor/behat/behat/bin/behat --suite=api_features --tags=group
```
