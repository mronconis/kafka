# Migrating ZooKeeper-based Kafka clusters
The following migration procedure is based on the official RedHat documentation available [here](https://docs.redhat.com/en/documentation/red_hat_streams_for_apache_kafka/2.9/html/using_streams_for_apache_kafka_on_rhel_in_kraft_mode/assembly-kraft-migration-str#proc-migrating-kafka-to-kraft-str)

## Pre-requisite
Apply the following pre-requisite before starting the migration process:
- Upgrade Zk/Kafka cluster to latest version 3.9.x (SfAK 2.9.x);
- Set `inter.broker.protocol.version` to current protocol version 3.9.

## Pre-migration
Configure ansible inventory to meet migration pb requirements:
1. Add hosts belonging to the `zookepper` group to the `controller` group.
2. Add hosts belonging to the `kafka` group to the `broker` group.
3. Configure `host_vars` to add the following configurations:
    - For each controller nodes add `kafka_controller_id` with a unique id on all cluster nodes (broker/controller);
    - For each controller nodes add `kafka_dir_id` with a random generated UID;
    - For each broker nodes add `kafka_node_id` with the value of the current `kafka_broker_id`.
4. Configure `kafka_cluster_id` in group_vars `all` with the specific cluster ID. If not provided, it will be automatically discovered via zookeeper-shell tool.
5. Configure group_vars for `controller` group to provide the KRaft controller configurations.
6. Configure group_vars for `kafka` to add the following configurations:
    - Add `kafka_kraft_mode` initialy set to 'false';
    - Add CONTROLLER listener to `kafka_listeners`.

## Run migration
The migration playbook is divided into several plays, one for each specific stage (configurable via ansible `--tags`), it is recommended to run it step-by-step.

```bash
ansible-playbook -i inventories/<inventory_name> \
    -e "kafka_log4j_debug_migration=true" \
    -e "kafka_home=/opt/kafka/kafka_2.13-3.9.2.redhat-00007" \
    --tags <phase{1..5}> \
    migrate.yml
```

## Post-migration

1. Remove hosts belonging to the `controller` group from the `zookeeper` group.
2. Remove hosts belonging to the `broker` group from the `kafka` group.
3. Remove all `zookeeper` group_vars. 
4. Rename group_vars root item from 'kafka:' to 'broker:'.
5. Remove non-KRaft compatible configurations from `kafka_additional_conf`:
    - `inter.broker.protocol.version`
    - any control-plane listener configuration (for example, `control.plane.listener.name` and its associated listener entry)
