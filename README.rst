tequila-solr
============

This repository holds an `Ansible <http://www.ansible.com/home>`_ role
that is installable using ``ansible-galaxy``.  This role contains
tasks used to install and set up a Solr search engine for a Django
deployment.  It exists primarily to support the `Caktus Django project
template <https://github.com/caktus/django-project-template>`_.


License
-------

This Ansible role is released under the BSD License.  See the `LICENSE
<https://github.com/caktus/tequila-solr/blob/master/LICENSE>`_ file
for more details.


Contributing
------------

If you think you've found a bug or are interested in contributing to
this project check out `tequila-solr on Github
<https://github.com/caktus/tequila-solr>`_.

Development sponsored by `Caktus Consulting Group, LLC
<http://www.caktusgroup.com/services>`_.


Installation
------------

Create an ``ansible.cfg`` file in your project directory to tell
Ansible where to install your roles (optionally, set the
``ANSIBLE_ROLES_PATH`` environment variable to do the same thing, or
allow the roles to be installed into ``/etc/ansible/roles``) ::

    [defaults]
    roles_path = deployment/roles/

Create a ``requirements.yml`` file in your project's deployment
directory ::

    ---
    # file: deployment/requirements.yml
    - src: https://github.com/caktus/tequila-solr
      version: 0.1.0

Run ``ansible-galaxy`` with your requirements file ::

    $ ansible-galaxy install -r deployment/requirements.yml

or, alternatively, run it directly against the url ::

    $ ansible-galaxy install git+https://github.com/caktus/tequila-solr

The project then should have access to the ``tequila-solr`` role in
its playbooks.


Variables
---------

The following variables are made use of by the ``tequila-solr``
role:

- ``project_name`` **required**
- ``root_dir`` **default:** ``"/var/www/{{ project_name }}"``
- ``log_dir`` **default:** ``"{{ root_dir }}/log"``
- ``solr_mirror`` **default:** ``"https://archive.apache.org/dist"``
- ``solr_version`` **default:** ``"4.9.1"``
- ``solr_cores`` **default:** ``['collection1']``
- ``solr_schema_file`` **required** (ex: ``"files/schema.xml"``)
- ``solr_xms`` **default:** ``"256M"``
- ``solr_xmx`` **default:** ``"512M"``
