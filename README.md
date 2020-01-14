# Ansible Roles

Some work needed, debug stuff still dotted around. Devoloped on Ansible 2 which lacks a systemd module. Firewalld needs implementing. Unneeded number of handlers...


## Rough Usage

On a fresh device after cloning the repo:

``` shell
yum install python2-pip -q -y

pip install ansible==2

pip install --upgrade Jinja2

ansible-playbook -i "localhost," -c local site.yml -e 'magento_archive=https://insert-url-to-the-file/Magento-CE-2.2.4_sample_data-2018-05-01-09-51-36.tar.gz magento_install=true magento_cache_hosts="" mysql_innodb_buffer=32M redis_maxmemory=16M'
```

This will use the given "Magento-CE-2.2.4_sample_data-2018-05-01-09-51-36.tar.gz" archive, performing a Magento 2 install. For the sake of example, the InnoDB buffer pool and Redis maxmemory variables are set _low_ (to avoid OOM when testing on smaller servers). See `magento.yml` for more configurables.

Once this completes, you should now be able to browse your new Magento site at `http(s)://<your ip>/`.

The admin path can be shown via the magento command-line tool:

`su - magento -c 'php /var/www/vhosts/example.com/public_html/bin/magento info:adminuri'`
> Admin URI: /admin_<random_string>

The admin username is “admin” and the password is “<your ip>_admin”.

---

Initally written by Joseph Chapman, continued here with my own opinions :bowtie:

