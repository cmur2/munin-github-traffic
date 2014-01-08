munin-github-traffic
====================

Creates Munin graphs from the traffic data that [GitHub](https://github.com) [now tracks](https://github.com/blog/1672-introducing-github-traffic-analytics)
for each of your repositories via an unofficial JSON API that uses the scheme
`https://github.com/<user>/<project>/graphs/traffic-data`. It only works for
repositories that you own or are contributer of.

Install
-------

Clone this repository or download the github-traffic_ file and create a
symlink as *root* in /etc/munin/plugins by using e.g.:

	cd /etc/munin/plugins; ln -s /path/to/github-traffic_ github-traffic_<user:::project>

where <user:::project> encodes the user and project to monitor.
They should be delimited by a triple colon ::: in order to be parsed correctly.

Additionally this script needs (in this first naive version) your
user_session cookie from your browser that is logged in into GitHub
in order to retrieve that information. This should be provided by the
`user_session` environment variable, in Munin this can be configured like this:

	[github-traffic_*]
	env.user_session blahblubmanycharacters

in the respective file, e.g. in /etc/munin/plugin-conf.d/munin-node.y

**Don't forget to restart your munin-node deamon.**
