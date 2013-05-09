[puppet-python](https://github.com/stankevich/puppet-python)
======

Puppet module for installing and managing python, pip, virtualenvs and Gunicorn virtual hosts.

## Usage

### python

Installs and manages python, python-dev, python-virtualenv and Gunicorn.

**version** — Python version to install. Default: system default

**dev** — Install python-dev. Default: false

**virtualenv** — Install python-virtualenv. Default: false

	class { 'python':
	  version    => 'system',
	  dev        => true,
	  virtualenv => true,
	}

### python::pip

Installs and manages packages from pip.

**ensure** — present/absent. Default: present

**virtualenv** — virtualenv to run pip in.

**url** — URL to install from. Default: none

**proxy** — Proxy server to use for outbound connections. Default: none

	python::pip { 'flask':
	  virtualenv => '/var/www/project1',
	  proxy      => 'http://proxy.domain.com:3128',
	}

### python::requirements

Installs and manages Python packages from requirements file.

**virtualenv** — virtualenv to run pip in. Default: system-wide

**proxy** — Proxy server to use for outbound connections. Default: none

	python::requirements { '/var/www/project1/requirements.txt':
	  virtualenv => '/var/www/project1',
	  proxy      => 'http://proxy.domain.com:3128',
	}

### python::virtualenv

Creates Python virtualenv.

**ensure** — present/absent. Default: present

**version** — Python version to use. Default: system default

**requirements** — Path to pip requirements.txt file. Default: none

**proxy** — Proxy server to use for outbound connections. Default: none

**systempkgs** — Copy system site-packages into virtualenv. Default: don't

**distribute** — Include distribute in the virtualenv. Default: true

	python::virtualenv { '/var/www/project1':
	  ensure       => present,
	  version      => 'system',
	  requirements => '/var/www/project1/requirements.txt',
	  proxy        => 'http://proxy.domain.com:3128',
	  systempkgs   => true,
	  distribute   => false,
	}

## Authors

[Sergey Stankevich](https://github.com/stankevich)
[Ashley Penney](https://github.com/apenney)
[Marc Fournier](https://github.com/mfournier)
