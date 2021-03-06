# What is irssi?

Irssi is a terminal based IRC client for UNIX systems. It also supports SILC and ICB protocols via plugins. Some people refer to it as 'the client of the future'.

> [irssi.org](http://irssi.org)

%%LOGO%%

# How to use this image

Because it is unlikely any two irssi users have the same configuration preferences, this image does not include an irssi configuration. To configure irssi to your liking, please refer to [upstream's excellent (and comprehensive) +documentation](http://irssi.org/documentation).

Be sure to also checkout the [awesome scripts](https://github.com/irssi/scripts.irssi.org) you can download to customize your irssi configuration.

## Directly via bind mount

On a Linux system, build and launch a container named `my-running-irssi` like this:

	docker run -it --name my-running-irssi -e TERM -u $(id -u):$(id -g) \
	    -v $HOME/.irssi:/home/user/.irssi:ro \
	    -v /etc/localtime:/etc/localtime:ro \
	    irssi

On a Mac OS X system, run the same image using:

	docker run -it --name my-running-irssi -e TERM -u $(id -u):$(id -g) \
	    -v $HOME/.irssi:/home/user/.irssi:ro \
	    irssi

You omit `/etc/localtime` on Mac OS X because `boot2docker` doesn't use this file.

Of course, you can name your image anything you like. In Docker 1.5 you can also use the `--read-only` mount flag. For example, on Linux:

	docker run -it --name my-running-irssi -e TERM -u $(id -u):$(id -g) \
	    --read-only -v $HOME/.irssi:/home/user/.irssi \
	    -v /etc/localtime:/etc/localtime \
	    irssi
