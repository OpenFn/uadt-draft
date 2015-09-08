
##[Postgrest](https://github.com/begriffs/postgrest)

```sh
wget https://github.com/begriffs/postgrest/releases/download/v0.2.11.0/postgrest-0.2.11.0-osx.tar.xz
tar xzvf postgrest-0.2.11.0-osx.tar.xz

```

```sh
./postgrest-0.2.11.0 \
  -d fn-uadt \
  -U stuart \
  -a stuart
```

```
brew tap theory/sqitch
brew install sqitch_pg
```

```
mkdir -p db && cd db
sqitch init uadt --engine pg
git init
git commit -am "Initial sqitch config."

# Tell sqitch who we are
sqitch config --user user.name 'Stuart Corbishley'
sqitch config --user user.email 'corbish@gmail.com'

sqitch add v1schema -n 'Add v1 schema for all UADT objects.'

# Added deploy & rollback to v1schema files

createdb uadt_test
sqitch deploy db:pg:uadt_test

# Verify
psql -d uadt_test -c '\dn "1"'
# List of schemas
#  Name | Owner
# ------+--------
#  1    | stuart
# (1 row)

# Verify with sqitch
sqitch verify db:pg:uadt_test

```

```
$ sqitch status db:pg:uadt_test
# On database db:pg:uadt_test
# Project:  uadt
# Change:   98c3c07e1a5e9aa954fcf8face0e47365503e565
# Name:     v1schema
# Deployed: 2015-09-01 15:18:14 +0200
# By:       Stuart Corbishley <corbish@gmail.com>
#
Nothing to deploy (up-to-date)
```

[sqitch tutorial](https://metacpan.org/pod/sqitchtutorial)
[sqitch boilerplate](https://github.com/begriffs/postgrest-example)
[postgrest introduction](http://blog.jonharrington.org/postgrest-introduction/)
