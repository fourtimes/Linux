## Remove Bulk Images using linux command

```sh
find /path/to/images -type f -name "*.jpg" -newermt "2023-01-01" ! -newermt "2024-01-01" -exec rm {} +

# forcefully delete the bulk image use this command
find /path/to/images -type f -name "*.jpg" -newermt "2023-01-01" ! -newermt "2024-01-01" -exec rm -f {} +

```

## Count the number of images inside the folder
```sh
ls -lrth /path-of-the-directory | wc -l
```
