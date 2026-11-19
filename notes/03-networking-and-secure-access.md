# Networking and Secure Access

The Bandit progression gradually moved from local files into network services and secure remote access.

## SSH

SSH was the main access mechanism throughout the game.

The work reinforced:

- remote authentication;
- non-default ports;
- command execution over SSH;
- private-key authentication;
- file transfer over SSH-based protocols.

Representative concepts:

```bash
ssh -p <port> user@host
ssh -i <private-key> user@host -p <port>
scp -P <port> user@host:<remote-file> .
```

## SSH Private Keys

One level returned an SSH private key instead of a password.

The workflow required:

```bash
chmod 600 <key>
ssh -i <key> user@host -p <port>
```

This made the permission requirement around private keys very concrete.

## Port and Service Discovery

A later level required identifying a service hidden within a local port range.

Representative approach:

```bash
nmap -sV -p <range> localhost
```

The important idea was:

```text
Known host
  ↓
Unknown service location
  ↓
Scan defined range
  ↓
Identify service
  ↓
Interact using correct protocol
```

## TLS / SSL Connections

The progression included connecting to TLS-enabled local services.

Representative tools included:

```bash
openssl s_client -connect localhost:<port>
ncat --ssl localhost <port>
```

This helped separate:

- plain TCP connection;
- encrypted TCP connection;
- application behavior on top of the connection.

## Netcat and Local Services

Netcat-style tools were used to:

- create listeners;
- send data;
- connect to local services;
- understand simple client/server communication.

This was useful for understanding that network communication can happen entirely inside one host through localhost.

## Security Relevance

A security analyst or engineer often needs to answer:

- What is listening?
- Which protocol is in use?
- Is encryption expected?
- What identity is authenticating?
- Is the connection local or remote?
- Which service receives the data?

Bandit made those questions practical rather than theoretical.

## Main Takeaway

> Networking becomes easier when you stop thinking only in terms of commands and start thinking in terms of endpoints, protocols, and trust.
