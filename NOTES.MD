# Redis Basics Documentation

## Storing Data in Redis

### Set Command

**Syntax:**

```
SET <key> <value>
```

**Example:**

```
SET user:1 Mahid
SET user:2 Hasan
```

- `user:1` means the key is `user:1` and its value is `Mahid`.
- Keys with similar prefixes form a logical group.

### SETNX Command

**Description:** Sets a value only if the key does not already exist.
**Syntax:**

```
SETNX <key> <value>
```

**Example:**

```
SETNX user:1 Hasan
```

### MSET Command

**Description:** Sets multiple key-value pairs in a single command.
**Syntax:**

```
MSET <key1> <value1> <key2> <value2> ...
```

**Example:**

```
MSET user:1 Hasan user:2 Usha
```

## Retrieving Data from Redis

### GET Command

**Syntax:**

```
GET <key>
```

**Example:**

```
GET user:1
```

### MGET Command

**Description:** Retrieves multiple values by their keys.
**Syntax:**

```
MGET <key1> <key2> ...
```

**Example:**

```
MGET user:1 user:2 user:3
```

## Incrementing and Decrementing Values

### INCR Command

**Description:** Increments the value of a key by 1.
**Syntax:**

```
INCR <key>
```

**Example:**

```
SET count 0
INCR count
```

### DECR Command

**Description:** Decrements the value of a key by 1.
**Syntax:**

```
DECR <key>
```

**Example:**

```
DECR count
```

### INCRBY Command

**Description:** Increments the value of a key by a specified amount.
**Syntax:**

```
INCRBY <key> <amount>
```

**Example:**

```
INCRBY count 100
```

## Redis Lists

**Description:** Lists are ordered collections of strings.

### Core Commands

- **LPUSH**: Adds an element to the head of a list.
- **RPUSH**: Adds an element to the tail of a list.
- **LPOP**: Removes and returns the first element of a list.
- **RPOP**: Removes and returns the last element of a list.
- **LLEN**: Returns the length of a list.
- **LMOVE**: Atomically moves elements from one list to another.
- **LRANGE**: Retrieves a range of elements from a list.
- **LTRIM**: Reduces a list to the specified range of elements.

**Examples:**

```
LPUSH mylist A
RPUSH mylist B
LRANGE mylist 0 -1
```

## Redis Sets

**Description:** Sets are unordered collections of unique strings.

### Core Commands

- **SADD**: Adds one or more members to a set.
- **SREM**: Removes one or more members from a set.
- **SISMEMBER**: Checks if a value exists in a set.

**Examples:**

```
SADD myset A B C
SREM myset B
SISMEMBER myset A
```

## Redis Hashes

**Description:** Hashes are collections of field-value pairs, similar to objects.

### Core Commands

- **HSET**: Sets one or more fields in a hash.
- **HGET**: Retrieves the value of a specific field.
- **HMGET**: Retrieves values of multiple fields.
- **HINCRBY**: Increments a field value by a specified amount.
- **HGETALL**: Retrieves all fields and values in a hash.
- **HEXPIRE** / **HPEXPIRE**: Sets a TTL for specific fields.
- **HTTL** / **HPTTL**: Gets the remaining TTL for specific fields.
- **HPERSIST**: Removes the expiration for specific fields.

**Examples:**

```
HSET user:1 name Hasan age 10 id 10
HGET user:1 name
HMGET user:1 name age id
HINCRBY user:1 age 20
HGETALL user:1
```

## Redis Streams

**Description:** Streams are append-only logs for event-based data.

### Core Commands

- **XADD**: Appends a new entry to a stream.
- **XREAD**: Reads entries from streams.
- **XRANGE**: Retrieves entries within a range of IDs.
- **XLEN**: Returns the number of entries in a stream.
- **XREADGROUP**: Reads entries using a consumer group.
- **XACK**: Acknowledges the processing of a message.
- **XGROUP**: Manages consumer groups.

**Examples:**

```
XADD mystream * temperature 22 humidity 60
XREAD COUNT 2 STREAMS mystream 0
XRANGE mystream - +
```

## Redis Sorted Sets

**Description:** Sorted sets are collections of unique strings ordered by a score.

### Core Commands

- **ZADD**: Adds or updates members with scores.
- **ZRANGE**: Retrieves members in ascending order by score.
- **ZREVRANGE**: Retrieves members in descending order by score.
- **ZINCRBY**: Increments a member's score.
- **ZRANK**: Gets the rank of a member (ascending).
- **ZREMRANGEBYSCORE**: Removes members within a score range.

**Examples:**

```
ZADD leaderboard 100 Alice
ZRANGE leaderboard 0 -1 WITHSCORES
ZINCRBY leaderboard 50 Alice
```

## Redis Pub/Sub

**Description:** Pub/Sub enables message communication between publishers and subscribers.

### Core Commands

- **SUBSCRIBE**: Subscribes to one or more channels.
- **UNSUBSCRIBE**: Unsubscribes from one or more channels.
- **PUBLISH**: Publishes a message to a channel.
- **PSUBSCRIBE**: Subscribes to channels matching a pattern.

**Examples:**

```
SUBSCRIBE news sports
PUBLISH news "Breaking News: Redis Rocks!"
PSUBSCRIBE news.*
```

---


# Redis Data Types and Example Use Cases

| **Data Type**   | **Example Use Case**                     |
|------------------|-----------------------------------------|
| **Strings**      | API rate limiting, session storage.     |
| **Hashes**       | User profiles, product details.         |
| **Lists**        | Task queues, chat messages.             |
| **Sets**         | Unique tags, common friends.            |
| **Sorted Sets**  | Leaderboards, ranking systems.          |
| **Pub/Sub**      | Real-time notifications, live updates.  |
| **Streams**      | Event logs, telemetry data, pipelines.  |



This document provides an overview of Redis basics, covering core data structures and commands. For more advanced use cases, refer to the official Redis documentation.
