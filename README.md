# Day 40 — Complete LAMP Stack with Ansible
#100DaysOfCloudAndSecurity capstone: 16 days of Ansible concepts in one deploy.

## Concept map (where each day shows up)
- Day 26/33 variables & group_vars/all split → group_vars/all/
- Day 27 inventory → inventory/hosts.ini
- Day 31 facts → rendered into index.php
- Day 32 roles → roles/{common,apache,php,mysql}
- Day 34 conditionals → common: fail-fast on non-Debian
- Day 35 templates → vhost.conf.j2, index.php.j2
- Day 36 handlers + force_handlers → apache role, site.yml
- Day 37 list-form installs → common, php
- Day 38 block/rescue/always → site.yml
- Day 39 collections + requirements.yml → community.mysql

## Run it
1. Ubuntu 24.04 target VM; put its IP + key in inventory/hosts.ini
2. cp group_vars/all/vault.yml.example group_vars/all/vault.yml
   → set a real password → ansible-vault encrypt group_vars/all/vault.yml
3. ansible-galaxy collection install -r requirements.yml
4. ansible-playbook -i inventory/hosts.ini site.yml --ask-vault-pass
5. Run step 4 AGAIN → recap should show changed=0 (idempotency proof)
6. curl http://YOUR.VM.IP/ → PHP version + "MySQL connection: OK"

## Evidence checklist for the post
- [ ] Screenshot: first run recap, failed=0
- [ ] Screenshot: second run recap, changed=0
- [ ] Screenshot/paste: curl output with MySQL OK
- [ ] One real thing that broke, and the fix
