# Bosh release for Apache Kafka

This is a Bosh release for Apache Kafka. This bosh release builds on the [Insightfactory Bosh release][1] in order to provide a standalone release for Apache Kafka.


## Supported Version

Apache Kafka 0.8.1.1

## Dependencies

Apache Zookeeper 3.4.6

## Usage

Take a look at the manifests directory for sample deployment manifests. Edit required variables with erb tags.

To build:

1. Run `git clone https://github.com/murraju/kafka-boshrelease`
2. `cd kafka-boshrelease`
3. Run `bosh create release`
4. Run `bosh upload release`
5. Run `bosh deployment sample_manifest.yml`
6. Run `bosh -n deploy`.
7. Run `bosh vms` to list VMs and IPs.

## Create new final release

Create a `config/private.yml` file with the following contents:

``` yaml
---
blobstore:
  s3:
    access_key_id:     ACCESS
    secret_access_key: PRIVATE
    bucke_name: BUCKET
```

```
bosh create release
# To test
git commit -m "updated spark release"
bosh create release --final
git commit -m "creating vN release"
git tag vN
git push origin master --tags
```



## Disclaimer

This is a development release and a work in progress. Please log issues. This release has been tested against AWS EC2 and OpenStack BOSH CPIs (Cloud Provider Interface).

## Copyright and Credits

&copy; 2014, Murali Raju <murali.raju@appliv.com> [@murraju][3]


[1]: https://github.com/murraju/insightfactory-boshrelease
[3]: http://twitter.com/murraju
