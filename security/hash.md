# Hash

- attackers don't need to necessarily know one's password
- they can use a list of commonly used hashes and attempt to use them to authN, known as collision
- using a pre-computed set of hashes for a password search is known as `lookup-table attack`
- great anecdote about why we need more characters for a secure password

> If a password is insecure (let's say someone uses a password 5 characters long), it can be relatively easily cracked. For example, a password of 5 lowercase characters can only be used to create 11,881,376 different passwords (26^5).

- rainbow tables offer the ability to search for a precomputed hash and their equivalent password
- this makes it easy to find commonly used passwords as the tables are shared amongst the internet and are easily available
- data can be protected by not only hashing them but using a salt, which is a random set of characters. This removes the ability for pre-computed tables to determine hashes as they wouldn't be able to guess the salt (it's random! and different for each piece of data!)
- one additional layer of protection is to randomize the amount of rounds performed for the hashing and salting of data, this makes it more difficult for the attacker to determine how the data was protected
- although this solution of rounds is not totally failsafe as an attacker could still obtain the salt value and the number of rounds if they are stored with the hashed data
- there's the concept of using a `pepper` to store a secret value to hash data and not make it easily available to a hacker

## Sources

- [Why a little salt can be great for your passwords (but not pepper!)](https://www.freecodecamp.org/news/why-a-little-salt-can-be-great-for-your-passwords/)
