API_VERSION = "2"

require "yaml"

config_file = ENV["CONFIG_FILE"] || "vmachines/default.yaml"
config = YAML.load_file config_file
machines = config["machines"]

Vagrant.configure(API_VERSION) do |config|
  machines.each do |machine|
    config.vm.define machine["name"] do |name|

      name.vm.provider :virtualbox do |virtualbox|
        virtualbox.name = machine["name"]
        virtualbox.cpus = machine["cpu"]
        virtualbox.memory = machine["memory"]
        virtualbox.linked_clone = machine["linked_clone"]
      end

      name.vm.box = machine["box"]
      name.vm.hostname = machine["name"]
      name.vm.network :private_network, ip: machine["private_ip"]

      name.vm.provision "shell", path: machine["shell_script_path"]

      name.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = machine["ansible_playbook_path"]
      end

    end
  end

  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.ssh.insert_key = false
  config.ssh.forward_agent = true

# The code below was commented out to pass verify github workflow
#   config.ssh.private_key_path = [
#     "~/.ssh/id_rsa",
#     "~/.vagrant.d/insecure_private_key"
#   ]

#   config.vm.provision :file do |file|
#     file.source = "~/.ssh/id_rsa.pub"
#     file.destination = "~/.ssh/authorized_keys"
#   end

end
