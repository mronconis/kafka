# Developer

## Configure ansible collection
```bash
mkdir -p .collections/ansible_collections/saiello
ln -s "$PWD" .collections/ansible_collections/saiello/kafka
```

## Run molecule scenario
```bash
molecule test -s <scenario_name>
```

If you want to inspect the cluster after testing:
```bash
molecule test -s <scenario_name> --destroy=never
```

If you want add some ansible args:
```bash
molecule test -s <scenario_name> -- <ANSIBLE_ARGS>
```
