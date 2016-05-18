# Discord Elixir

Discord library for Elixir. I needed it and figured I'd share.

This library is useful for making calls and implementing a bot as well.

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add discord_elixir to your list of dependencies in `mix.exs`:

        def deps do
          [{:discord_elixir, "~> 1.0.0"}]
        end

  2. Ensure discord_elixir is started before your application:

        def application do
          [applications: [:discord_elixir]]
        end

  3. Look at the examples/echo_bot.ex file and you should honestly be
     good to go.

## REST Client Usage

The easy way to use discord resources is by doing the following.

	# alias the resource you wish to use to make it easy on yourself

	alias DiscordElixir.RestClient.Resources.User

	# Establish a connection
	{:ok, connection} = User.login("<username>","<password>")

	# Call on the resource and reap the results

	User.guilds(connection)

If you like going the longer route and obtained your token already - you can use resources like this:

	# Create a connection
	token = "<your-token>"
	{:ok, conn} = DiscordElixir.RestClient.start_link(%{token: token})

	# Get to using the resource function for the rest client
	DiscordElixir.RestClient.resource(conn, :get, "users/@me/channels")

	# You can also user other method resources like 'post':
	DiscordElixir.RestClient.resource(conn, :post, "users/@me/channels", %{recipient_id: <recipient_id>})

The 'resource' function makes it a lot easier to use the library. The following methods are supported.

	DiscordElixir.RestClient.resource(conn, :get, <url>)
	DiscordElixir.RestClient.resource(conn, :post, <url>, <map-of-data>)
	DiscordElixir.RestClient.resource(conn, :put, <url>, <map-of-data>)
	DiscordElixir.RestClient.resource(conn, :patch, <url>, <map-of-data>)
	DiscordElixir.RestClient.resource(conn, :delete, <url>)


** The following Resources are supported - you can look at their docs for examples and more information: **
  ----

  	alias DiscordElixir.RestClient.Resources.Channel

	Channel.bulk_delete_messages/3
	Channel.create_invite/3
	Channel.delete/2
	Channel.delete_message/3
	Channel.delete_permissions/3
	Channel.edit_permissions/4
	Channel.get/2
	Channel.get_invites/2
	Channel.messages/2
	Channel.modify/3
	Channel.send_file/3
	Channel.send_message/3
	Channel.trigger_typing/2
	Channel.update_message/4
	
[channel-resource-doc](DiscordElixir.RestClient.Resources.Channel.html)

  ----

	alias DiscordElixir.RestClient.Resources.Image

  	Image.avatar_url/2
  	Image.icon_url/2

[image-resource-doc](DiscordElixir.RestClient.Resources.Image.html)

  ----

  	alias DiscordElixir.RestClient.Resources.Invite

	Invite.accept/2
	Invite.delete/2
	Invite.get/2

[invite-resource-doc](DiscordElixir.RestClient.Resources.Invite.html)

  ----

  	alias DiscordElixir.RestClient.Resources.User

	User.connections/1
	User.create_dm_channel/2
	User.current/1
	User.dm_channels/1
	User.get/2
	User.guilds/1
	User.leave_guild/2
	User.login/2
	User.logout/1
	User.modify/2
	User.query/3

[user-resource-doc](DiscordElixir.RestClient.Resources.User.html)


