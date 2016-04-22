Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider("virtualbox") {|vb| vb.memory = "512" }

  config.vm.provision "chef_solo" do |chef|
    chef.json = {
      "nginx" => {
        "default_site_enabled" => false,
        "init_style" => "init",
        "server_tokens" => "off",
        "source" => {
          "modules" => ["nginx::http_gzip_static_module", "nginx::http_ssl_module", "nginx::ngx_lua_module", "nginx::ngx_openresty"]
        }
      }
    }

    chef.cookbooks_path = ["cookbooks"]
    chef.add_recipe "nginx::source"
  end
end
