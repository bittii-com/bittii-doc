# [Bittii.com](https://www.bittii.com) - Development environment as code, with a web based IDE

The most concise way of orchestrating and maintaining a development environment.

## Registration

Start by registering your organisation here: https://bittii.com/register

You can use the fully functioning system for 1 week free of charge.

## Environments

Development environments are our main service. Every environment has developers, and every developer is an user. 

![Environments](/environments.png)

![Developers](/developers.png)

By clicking the link, the user can start using the development environment via our web IDE, which is based on Eclipse Theia. But only if the user is added as a developer for that environment.

![IDE](/ide.png)

## Tokens

Tokens open up the world of development environment as code. First you need to create a tar.gz package with a sturcture that resembles this:

```bash
├── package.tar.gz
│   ├── init.sh
│   ├── sql
│   │   ├── tables.sql
```

On the root level there is a file called *init.sh* which is a normal shell script file. This is the script file that you can use to prepare your development environment, and it is the only file that is necessary.

On the root level there is also a directory called *sql* which includes a file called *tables.sql*. You can refer to this file in *init.sh* as *sql/tables.sql*. Naturally this is only an example, so you can include anything in your package and call it from *init.sh*.

Our environments are based on Alpine Linux (https://www.alpinelinux.org/). So, new packages are installed with *apk* and so on.

After that you need to create a token for your environment. Click the lock to see the actual token. You need to copy the whole string.

![IDE](/token.png)

After that you can use our REST API to deploy your development environment. This curl command demonstrates the method, but obviously you can and probably should use your favourite DevOps system to do this.

```bash
curl -F “token=YOUR_TOKEN_HERE” -F “file=@YOUR_PACKAGE.tar.gz” https://www.bittii.com/image
```

## Testing via proxy

You can use our tool and language agnostic proxy to test your back-end and front-end applications:

https://www.bittii.com/envport/:environmentId/:port/*anythingAfterRoot

Where :environmentId is the id of the environment and :port is the port you have chosen for your application. Please make sure that your application can handle proxy connections.

## Contact

Email us at hello@bittii.com