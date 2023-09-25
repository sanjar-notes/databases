# Setup
18 April 2022

> for latest settings, see [computer setup](https://gist.github.com/sanjarcode/3dc47b0d69526435753a199dfd60dcfc)
## MySQL
Install the following things:
1. MySQL - for SQL and relational database. On macOS, use [this article](https://flaviocopes.com/mysql-how-to-install/)
2. mycli - https://www.mycli.net/, syntax highlight and auto-completion of cli. Start this by running `mycli -u root -p mysql_password`.

As of now, running completely on CLI

## PostgreSQL
- Installation - https://gist.github.com/sanjarcode/3dc47b0d69526435753a199dfd60dcfc#databases
- Seeding the DB - https://gist.github.com/sanjarcode/7eed824aef573bf69b13df818944f96e

## MongoDB
I've not setup local, but it won't be too hard. TODO
### Cloud setup (Atlas)
1. Log in to mongodb website.
2. Create a project and a cluster
3. Click on 'Connect' and copy SRV. This is used by backend apps, where the password can be made an environment variable.
4. Go to the user and enable all permissions. **be careful**
5. Go to security/cluster and enable 'Access from any IP' address, so cloud deployments work. **be careful**