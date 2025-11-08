# 🧰 Mongo Tools Docker Setup

This setup provides a simple way to use **MongoDB command-line tools** (`mongodump`, `mongorestore`, etc.) inside a Docker container — without needing MongoDB installed locally.

You can use it to:
- **Backup (dump)** MongoDB databases from **MongoDB Atlas** or local servers.
- **Restore** databases back to Atlas or other MongoDB instances.
- Save all dump files in a local folder accessible from your host machine.

---

## Run docker compose

docker compose up -d

## Enter inside of container terminal

docker exec -it mongo-tools bash


## Run the commands

mongodump --uri="mongodb+srv://[user]:[pass]@[my-mongodb].mongodb.net/[dbname]" \
  --out=/data/backup/[dbname]-dump

mongorestore --uri="mongodb+srv://[user]:[pass]@[my-mongodb].mongodb.net/" \
  --nsInclude=[dbname].* /data/backup/[dbname]-dump

## Summary

| Purpose          | Command                                                      |
| ---------------- | ------------------------------------------------------------ |
| Start container  | `docker compose up -d`                                       |
| Open shell       | `docker exec -it mongo-tools bash`                           |
| Dump from Atlas  | `mongodump --uri="..." --out=/data/backup/...`               |
| Restore to Atlas | `mongorestore --uri="..." --nsInclude=db.* /data/backup/...` |
