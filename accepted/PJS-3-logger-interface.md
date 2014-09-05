Logger Interface
================

This document describes a common interface for logging libraries. Yes, really, LOGGING gets its own PJS.

The main goal is to allow libraries to receive a `Pjs\Log\LoggerInterface`
object and write logs to it in a simple and universal way. Frameworks
and CMSs that have custom needs MAY extend the interface for their own
purpose, but SHOULD remain compatible with this document. This ensures
that the third-party libraries an application uses can write to the
centralized application logs. Holy fuck I'm bored already please kill me now...
