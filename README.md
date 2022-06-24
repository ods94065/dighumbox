# Dig Hum Box

Everything you need to construct a Dig Hum Vagrant box.

# What you need

- For MacOS: xcode commandline tools (`xcode-select --install`)
- Vagrant (`brew install vagrant`)
- VirtualBox (`brew install virtualbox`; may require system restart)
- Ansible (`brew install ansible`)

# Creating a development VM for the box

```sh
vagrant box install roboxes/debian11
vagrant up
```

This should run to completion without errors!

# Running and testing the app

For now, `vagrant ssh` into the VM, and run:

```sh
cd /app
./manage.py runserver 0.0.0.0:8000
```

Yes, the `0.0.0.0` is required.

Then, from the host (outside of the VM), fire up a browser and point it to `http://localhost:8000`.

Ctrl-C the running command to stop the app.

This also has an instance of `apache2` running on port 80, which I've mapped to host port 7080. To see it, simply point your browser to `http://localhost:7080`.

# Provisioning the development VM

The provisioning script is an Ansible script: `playbook.yml`. If you make a change to the script and want to apply it, simply use `vagrant provision`.

The local directory `app/` is mounted into the VM at `/app`. To change the app's code, you should just be able to edit locally and see the changes take effect immediately while the app is running in the VM.

# Creating the actual box

This will be a `vagrant package` command of some sort. Details TBD!
