# mailcow dockerless

My notes and patches to be able to run mailcow without a dependency on Docker.

- Line endings are not uniform
- The database configuration allows access only via the socket. This means that remote databases cannot be used.
- Many file paths are hardcoded, although this would not be necessary.
- Excessive use of environment variables.<br>These are not accessed uniformly.
- The use of PECL extensions forces to build them from the source code.



## patches

- 00-mailcow.dos2unix.patch
- 05-mailcow.add-new-vars.patch
- 10-mailcow.reduce-env-vars.patch
- 15-mailcow.disable-docker.patch
- 20-mailcow.fix-hard-coded-path_1.patch
- 25-mailcow.fix-hard-coded-path_2.patch
- 30-mailcow.fix-hard-coded-hosts.patch

## use

```bash

cd /usr/share

$ patch  --strip 0 --input 00-mailcow.dos2unix.patch
patching file mailcow/rspamd/dynmaps/aliasexp.php
patching file mailcow/rspamd/dynmaps/bcc.php
patching file mailcow/rspamd/dynmaps/settings.php
patching file mailcow/rspamd/meta_exporter/pipe.php
patching file mailcow/rspamd/meta_exporter/pipe_rl.php
patching file mailcow/rspamd/meta_exporter/pushover.php
patching file mailcow/web/inc/ajax/container_ctrl.php
patching file mailcow/web/inc/ajax/destroy_tfa_auth.php
patching file mailcow/web/inc/ajax/qitem_details.php
patching file mailcow/web/inc/ajax/qr_gen.php
patching file mailcow/web/inc/ajax/show_rspamd_global_filters.php
patching file mailcow/web/inc/ajax/sieve_validation.php
patching file mailcow/web/inc/ajax/syncjob_logs.php
patching file mailcow/web/inc/ajax/transport_check.php
patching file mailcow/web/inc/functions.acl.inc.php
patching file mailcow/web/inc/functions.address_rewriting.inc.php
patching file mailcow/web/inc/functions.admin.inc.php
patching file mailcow/web/inc/functions.app_passwd.inc.php
patching file mailcow/web/inc/functions.customize.inc.php
patching file mailcow/web/inc/functions.dkim.inc.php
patching file mailcow/web/inc/functions.docker.inc.php
patching file mailcow/web/inc/functions.domain_admin.inc.php
patching file mailcow/web/inc/functions.fail2ban.inc.php
patching file mailcow/web/inc/functions.fwdhost.inc.php
patching file mailcow/web/inc/functions.inc.php
patching file mailcow/web/inc/functions.mailbox.inc.php
patching file mailcow/web/inc/functions.mailq.inc.php
patching file mailcow/web/inc/functions.oauth2.inc.php
patching file mailcow/web/inc/functions.policy.inc.php
patching file mailcow/web/inc/functions.pushover.inc.php
patching file mailcow/web/inc/functions.quarantine.inc.php
patching file mailcow/web/inc/functions.quota_notification.inc.php
patching file mailcow/web/inc/functions.ratelimit.inc.php
patching file mailcow/web/inc/functions.rspamd.inc.php
patching file mailcow/web/inc/functions.tls_policy_maps.inc.php
patching file mailcow/web/inc/functions.transports.inc.php
patching file mailcow/web/inc/init_db.inc.php
patching file mailcow/web/inc/sessions.inc.php
patching file mailcow/web/json_api.php
patching file mailcow/web/oauth/profile.php
patching file mailcow/web/oauth/token.php


$ patch  --strip 0 --input 10-mailcow.reduce-env-vars.patch
patching file mailcow/web/_rspamderror.php
patching file mailcow/web/autodiscover-json.php
patching file mailcow/web/autodiscover.php
patching file mailcow/web/debug.php
patching file mailcow/web/inc/ajax/dns_diagnostics.php
patching file mailcow/web/inc/functions.fail2ban.inc.php
patching file mailcow/web/inc/functions.inc.php
patching file mailcow/web/inc/functions.mailbox.inc.php
patching file mailcow/web/inc/header.inc.php
patching file mailcow/web/inc/init_db.inc.php
patching file mailcow/web/inc/prerequisites.inc.php
patching file mailcow/web/json_api.php
patching file mailcow/web/mailbox.php
patching file mailcow/web/sogo-auth.php

$ patch  --strip 0 --input 15-mailcow.disable-docker.patch
patching file mailcow/web/debug.php
patching file mailcow/web/inc/prerequisites.inc.php

$ patch  --strip 0 --input 20-mailcow.fix-hard-coded-path_1.patch
patching file mailcow/web/admin.php
patching file mailcow/web/debug.php
patching file mailcow/web/edit.php
patching file mailcow/web/inc/header.inc.php
patching file mailcow/web/inc/init_db.inc.php
patching file mailcow/web/inc/prerequisites.inc.php
patching file mailcow/web/inc/vars.inc.php
patching file mailcow/web/index.php
patching file mailcow/web/mailbox.php
patching file mailcow/web/qhandler.php
patching file mailcow/web/quarantine.php
patching file mailcow/web/queue.php
patching file mailcow/web/user.php

$ patch  --strip 0 --input 25-mailcow.fix-hard-coded-path_2.patch
patching file mailcow/web/admin.php
patching file mailcow/web/inc/functions.mailbox.inc.php
patching file mailcow/web/inc/functions.quarantine.inc.php
patching file mailcow/web/inc/functions.quota_notification.inc.php
patching file mailcow/web/inc/functions.rspamd.inc.php

$ patch  --strip 0 --input 30-mailcow.fix-hard-coded-hosts.patch
patching file mailcow/rspamd/local.d/greylist.conf
patching file mailcow/rspamd/local.d/metadata_exporter.conf
patching file mailcow/rspamd/lua/rspamd.local.lua
patching file mailcow/web/admin.php
```
