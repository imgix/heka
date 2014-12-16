
======
Inputs
======

Common Input Parameters
=======================

There are some configuration options that are universally available to all
Heka input plugins. These will be consumed by Heka itself when Heka
initializes the plugin and do not need to be handled by the plugin-specific
initialization code.

- decoder (string, optional):
	Decoder to be used by the input. This should refer to the name of a
	decoder plugin section that is specified elsewhere in the TOML
	configuration. If supplied, messages will be decoded before being passed
	on to the router when the InputRunner's `Deliver` method is called.
- synchronous_decode (bool, optional):
	If `synchronous_decode` is false, then any specified decoder plugin will
	be run by a DecoderRunner in its own goroutine and messages will be passed
	in to the decoder over a channel, freeing the input to start processing
	the next chunk of incoming or available data. If true, then any decoding
	will happen synchronously and message delivery will not return control to
	the input until after decoding has completed. Defaults to false.
- send_decode_failures (bool, optional):
	If false, then if an attempt to decode a message fails then Heka will log
	an error message and then drop the message. If true, then in addition to
	logging an error message, decode failure will cause the original,
	undecoded message to be tagged with a `decode_failure` field (set to true)
	and delivered to the router for possible further processing.

.. include:: /config/inputs/amqp.rst

.. include:: /config/inputs/docker_log.rst

.. include:: /config/inputs/file_polling.rst

.. include:: /config/inputs/http.rst

.. include:: /config/inputs/httplisten.rst

.. include:: /config/inputs/kafka.rst

.. include:: /config/inputs/logstreamer.rst

.. include:: /config/inputs/process.rst

.. include:: /config/inputs/processdir.rst

.. include:: /config/inputs/stataccum.rst

.. include:: /config/inputs/statsd.rst

.. include:: /config/inputs/tcp.rst

.. include:: /config/inputs/udp.rst

