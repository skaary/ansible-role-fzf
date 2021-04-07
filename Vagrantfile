Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = { ansible_ssh_user: 'vagrant', vagrant: true, user: 'vagrant', user_home: '/home/vagrant' }
    ansible.become = true
    ansible.playbook = 'test/vagrant-playbook.yml'
  end
end