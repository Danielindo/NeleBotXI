# Classes and functions

- [NeleBotX](#nelebotx)
- [AntiFlood](#antiflood)
- [Database](#database)
- [Variables](#variables)
- [TelegramBot](#telegrambot)

# NeleBotX

This is the class that start the Framework.

### NeleBotX::__construct

Start the NeleBotX class: virify the token, start other classes and load user and group or channel.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$configs](./variables.md#configs) | Array | Yes | Contains all variables for the Framework |

### NeleBotX::loadUser

Return an array of current user automatically generated from the update or load from database if available.

### NeleBotX::loadGroup

Return an array of current group automatically generated from the update or load from database if available.

### NeleBotX::loadChannel

Return an array of current channel automatically generated from the update or load from database if available.

# AntiFlood

### AntiFlood::__construct

Calculate the flood via Redis. 

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$database](#Database) | Class | Yes | Contains Database class |
| $id | Integer | Yes | Contains Telegram ID |

# Database

### Database::__construct

Start connection to SQLite/MySQL/PostrgeSQL or/and Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$configs](./variables.md#configs) | Array | Yes | Contains all variables for the Framework |

### Database::redisConnect

Try to connect to the Redis server.

### Database::rget

Try to [get](https://github.com/phpredis/phpredis#get) value of a key from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |

### Database::rset

Try to [set](https://github.com/phpredis/phpredis#set) the string value as value of key.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |
| [$value](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Value |
| [$time](https://github.com/phpredis/phpredis#set) | Number or Array | Optional | Timeout or Options Array |

### Database::rdel

Try to [delete](https://github.com/phpredis/phpredis#del-delete-unlink) a key from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |

### Database::rkeys

Try to get [keys](https://github.com/phpredis/phpredis#keys-getkeys) that match a certain pattern from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |

### Database::rladd

Try to [lpush](https://github.com/phpredis/phpredis#lpush): adds one or more values to the head of a LIST from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |
| [$value](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Value |

### Database::rlget

Try to get the [list](https://github.com/phpredis/phpredis#lrange-lgetrange) by key from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |
| [$offset](https://github.com/phpredis/phpredis#lrange-lgetrange) | Integer | Optional | Start of the range |
| [$offset](https://github.com/phpredis/phpredis#lrange-lgetrange) | Integer | Optional | End of the range |

### Database::rldel

Try to [remove](https://github.com/phpredis/phpredis#lrem-lremove) values from list by key and value from Redis.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$key](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Key |
| [$value](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Value |
| [$count](https://github.com/phpredis/phpredis#lrange-lgetrange) | Integer | Optional | Count of values to remove |

### Database::dbConnect

Start SQLite/MySQL/PostgreSQL database connection by configs. Require [PDO class](https://www.php.net/manual/en/book.pdo.php).

### Database::sqliteConnect

Start SQLite database connection. Require [PDO_SQLITE](https://www.php.net/manual/en/ref.pdo-sqlite.php) driver.

### Database::mysqlConnect

Start MySQL database connection. Require [PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php) driver.

### Database::mysqlConnect

Start PostgreSQL database connection. Require [PDO_PGSQL](https://www.php.net/manual/en/ref.pdo-pgsql.php) driver.

### Database::query

Custom general unique query with prepare on PDO connection.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$query](https://www.php.net/manual/en/class.pdostatement.php) | String | Yes | SQL statement |
| [$args](https://www.php.net/manual/en/pdostatement.execute) | Array | Optional | An array of values with as many elements as there are bound parameters in the SQL statement being executed. |
| $return | Integer | Optional | Return of contents can be 0 to return only true on success, 1 to [fetch](https://www.php.net/manual/en/pdostatement.fetch) with FETCH_ASSOC, or 2 to [fetchAll](https://www.php.net/manual/en/pdostatement.fetchall.php) |

### Database::limit

Create the LIMIT SQL statement. Return as String that contain the limit-offset SQL statement.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$limit](https://github.com/phpredis/phpredis#keys-and-strings) | <code>ALL</code> or Integer | Optional | Start of the range |
| [$offset](https://github.com/phpredis/phpredis#keys-and-strings) | Integer | Optional | End of the range |

### Database::setup

Create default Framework tables. Return an Array of query results.

### Database::createTemplateTable

Get the SQL Statement tamplate of a Framework table.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$table](https://github.com/phpredis/phpredis#keys-and-strings) | String | Yes | Table name |

### Database::getUser

Get user variables and automatically insert it in the database if not exists.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$user](https://core.telegram.org/bots/api#user) | Array | Yes | Telegram User informations |

### Database::getGroup

Get group variables and automatically insert it in the database if not exists.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$chat](https://core.telegram.org/bots/api#chat) | Array | Yes | Telegram Chat informations |

### Database::getChannel

Get channel variables and automatically insert it in the database if not exists.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$chat](https://core.telegram.org/bots/api#chat) | Array | Yes | Telegram Chat informations |

### Database::getChatsByAdmin

Get groups and channels variables by a Telegram User ID that is an administrator in it.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $user_id | Integer | Yes | Telegram User ID |
| $limit | Integer | Optional | Limit for the query |

### Database::ban

Ban a chat from the Bot. Bot's admins excluded.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Yes | Chat ID |

### Database::unban

Unban a chat from the Bot.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Yes | Chat ID |

### Database::isBanned

Check if a chat has been banned. Return an array with ban for table.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Yes | Chat ID |

### Database::getLanguage

Get the user language.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Yes | User ID |

### Database::setStatus

Set user status on database.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Yes | User ID |
| $status | String | Optional | Status of a user on your Bot |

# Variables

For all var functions see the Telegram [Available types](https://core.telegram.org/bots/api#available-types).

### Variables::__construct

Create all variables that can exists in the update.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$configs](./variables.md#configs) | Array | Yes | Contains all variables for the Framework |
| [$update](https://core.telegram.org/bots/api#update) | Array | Yes | Contains all variables from the Telegram update |

### Variables::isAdmin

Check if the user is an administrator of the Bot by configs.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $id | Integer | Optional | User ID |

### Variables::getUser

Get the current user by the update variables. Return *null* if not found.

### Variables::getGroup

Get the current group by the update variables. Return *null* if not found.

### Variables::getChannel

Get the current channel by the update variables. Return *null* if not found.

### Variables::getGroupsPerms

Get the default Telegram [permissions](https://core.telegram.org/bots/api#chatpermissions) for only groups.

### Variables::getChannelsPerms

Get the default [Telegram permissions](https://core.telegram.org/bots/api#chatpermissions) for only channels.

# TelegramBot

To see API functions docs you can check the Telegram [methods](https://core.telegram.org/bots/api#available-methods) and TelegramBot class!

### TelegramBot::__construct

Start the class to make requests.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| [$configs](./variables.md#configs) | Array | Yes | Contains all variables for the Framework |

### TelegramBot::editConfigs

It only changes the script configurations, not the file. 

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $key | Array | Yes | [$configs](./variables#configs) key |
| $value | All | Yes | Value |

### TelegramBot::getConfigs

Get the current script configurations. Return [$configs](./variables#configs).

### TelegramBot::sendLog

Send logs to the logs chat.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $message | String | Yes | Error message |

### TelegramBot::request

Make cURL requests. See how can you make [requests](https://core.telegram.org/bots/faq#how-can-i-make-requests-in-response-to-updates) in response to Telegram updates.

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $url | String | Yes | Request url |
| $args | Array | Optional | Arguments for the request |
| $post | Boolean or <code>def</code> | Optional | *True* to post, *false* to get or <code>def</code> by default from configs |

### TelegramBot::getUpdate

Return the current [update](https://core.telegram.org/bots/api#update).

### TelegramBot::api

Create the Telegram Bot API url for any method. 
See the [Local API Server](https://core.telegram.org/bots/api#do-i-need-a-local-bot-api-server) to have [features](https://core.telegram.org/bots/api#using-a-local-bot-api-server).

| Parameters    | Type          | Required  | Description    |
|:-------------:|:-------------:|:---------:|:--------------:|
| $method | String | Yes | Telegram Bot API [method](https://core.telegram.org/bots/api#available-methods) |

## The other methods are similar to the Bot API methods, explore the class on the TelegramBot.php file to find out!

If you don't understand something try asking for support on our Telegram support group!
