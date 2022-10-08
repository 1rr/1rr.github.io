CREATE DATABASE foo
SHOW DATABASES
USE foo
SHOW MEASUREMENTS
DROP MEASUREMENT mars
SHOW FIELD KEYS FROM "mars-A6"
SELECT "power" FROM "drilling" WHERE ("module_id"='rover') AND time >= now() - 9h
SHOW SERIES
DROP SERIES FROM "drilling" WHERE ("module_id" = 'oppy')

###
brew services restart influxdb