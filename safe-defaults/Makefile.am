do_subst = sed \
	-e 's|@DATAROOTDIR[@]|$(datarootdir)|g' \
	-e 's|@SBINDIR[@]|$(sbindir)|g' \
	-e 's|@SYSCONFDIR[@]|$(sysconfdir)|g' \
	-e 's|@FLATPAK_ARCH[@]|$(flatpak_arch)|g' \
	$(NULL)

eos-safe-defaults: eos-safe-defaults.in Makefile
	$(AM_V_GEN) $(do_subst) $< >$@.tmp && mv $@{.tmp,}
	$(AM_V_at) chmod +x $@

eos-safe-defaults.service: eos-safe-defaults.service.in Makefile
	$(AM_V_GEN) $(do_subst) $< >$@.tmp && mv $@{.tmp,}

tmpfiles-disable.conf: tmpfiles-disable.conf.in Makefile
	$(AM_V_GEN) $(do_subst) $< >$@.tmp && mv $@{.tmp,}

tmpfiles-enable.conf: tmpfiles-enable.conf.in Makefile
	$(AM_V_GEN) $(do_subst) $< >$@.tmp && mv $@{.tmp,}

sbin_SCRIPTS = \
	eos-safe-defaults \
	$(NULL)

dist_systemdunit_DATA = \
	eos-safe-defaults.service \
	$(NULL)

generated_tmpfiles = \
	tmpfiles-disable.conf \
	tmpfiles-enable.conf \
	$(NULL)

safe_defaultsdir = $(datadir)/eos-safe-defaults
safe_defaults_DATA = \
	dnsmasq-opendns-family-shield.conf \
	nm-use-dnsmasq.conf \
	$(generated_tmpfiles) \
	$(NULL)

safe_defaults_chrome_policy_safe_searchdir = \
	$(datadir)/eos-safe-defaults/chrome/policies/managed
safe_defaults_chrome_policy_safe_search_DATA = \
	dns-over-https.json \
	chrome-safe-search.json \
	$(NULL)

EXTRA_DIST = \
	dns-over-https.json \
	dnsmasq-opendns-family-shield.conf \
	chrome-safe-search.json \
	eos-safe-defaults.in \
	eos-safe-defaults.service.in \
	nm-use-dnsmasq.conf \
	tmpfiles-disable.conf.in \
	tmpfiles-enable.conf.in \
	$(NULL)

CLEANFILES = \
	$(dist_systemdunit_DATA) \
	$(generated_tmpfiles) \
	$(sbin_SCRIPTS) \
	$(NULL)
