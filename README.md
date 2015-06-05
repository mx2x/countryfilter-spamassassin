# countryfilter-spamassassin
Spamassassin Plugin to score messages based which countries a message is
sent from or relays through

Site:
https://github.com/alasdairkeyes/countryfilter-spamassassin



Installation
- Copy the country_filter.cf file into your SpamAssassin config folder
  (Usually /etc/mail/spamassassin/ or /etc/spamassassin/)
- Copy the CountryFilter.pm file into your SpamAssassin plugin folder
  (Usually /usr/lib/perl5/vendor_perl/5.8.8/Mail/SpamAssassin/Plugin/ or
   /usr/share/perl5/Mail/SpamAssassin/Plugin/)
- Restart SpamAssassin



Notes
- Example country codes in the config file are codes that are not in
  general use no countries are whitelisted or blacklisted by default
  in the config file
- Plugin is similar to SpamAssassin::Plugin::RelayCountry which inserts
  metadata on relays into the message headers, this differs in respect
  to scoring based on user black/whitelist.



License
- See included license file - Released under this license to be as
  compatible with SpamAssassin as possible



Dependencies
- GeoIP library
- Geo::IP Perl Module
- Preferably an up-to-date copy of the GeoIP database fom
  http://dev.maxmind.com/geoip/legacy/geolite/



Potential Issues
- Only tested with IPv4 addresses. Some tweaking very probably required to
  work with IPv6
- New Geo::IP object instantiated for each lookup, no caching setup, this
  might cause sub-par performance on very busy SpamAssassin hosts.




Future work
- Implement caching for Geo::IP object
- Get IP/Country Code reporting into the X-Spam-Report Header
  From
    *    1.0 BLACKLIST_RELAY_COUNTRY Email was relayed through a country in
    *    config blacklist
  To
    *    1.0 BLACKLIST_RELAY_COUNTRY Email was relayed through a country in
    *    config blacklist (1.2.3.4|XX)

Author
- Alasdair Keyes - https://akeyes.co.uk/
