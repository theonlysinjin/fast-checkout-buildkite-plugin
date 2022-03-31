# Fast Checkout Buildkite Plugin

Fast checkouts a directory from Github.  
Based on https://buildkite.com/docs/plugins/writing

The point we are going for here with this plugin is the fastest possible way to accomplish a few things.
- Checkout a list of directories
- Checkout the whole repo as fast as possible
- Checkout submodules in the repo as fast as possible
## Example

Add the following to your `pipeline.yml`:

```yml
steps:
  - command: echo a fast checkout experience
    plugins:
      - theonlysinjin/fast-checkout#main:
          depth: 1
          sparse: "dir1 dir2"
          submodules: false
```

## Configuration

### `depth` (Optional, number)
The value to pass into `--depth` on checkout.  
If value is set to 0, do not perform a shallow clone.
Default: 1

### `sparse` (Optional, string)
List of directories to sparse checkout.  
Seperate directories with a space
Default: ""

### `submodules` (Optional, boolean)
If `true` it will do a shallow update with `depth` set to the same value above.
Default: false

## Developing

To run the tests:

```shell
docker-compose run --rm tests
```

## Contributing

I would love some assistance with any git-cloning speed-improving techniques people have discovered along the way.  

Tested PR's welcome.
