# Snap Tips

## <https://snapcraft.io/docs/getting-started>


## QUICKSTART GUIDE

- `snap version`
- `snap find "media player"`
- `snap info vlc`
- `snap install vlc`
- `snap switch --channel=edge vlc` or
- `snap switch --channel=stable vlc`
- `which vlc`
- `/snap/bin/vlc` absolute path to the binary
- `snap list`
- `snap refresh vlc`
- `snap refresh --channel=beta vlc`

### Version vs Revision

- Versions are assigned by the developer
- Revisions are assigned by the snap store
- Neither enforce which to install.

- `snap revert vlc`
- `snap list --all vlc`
- `snap enable vlc`
- `snap disable vlc`
- `snap remove vlc`


## WORKING WITH SNAPS

### Channels

Channel name is made up of 3 parts:

    `<track>/<risk>/<branch>`

risk = stable/candidate/beta/edge
track = A way to add heirachies to the channels/risk, e.g. insider/stable, insider/edge
branch = finer sub division that is normally short lived for bug fixing, auto closed after 30 days.

### Control Updates

To hold refreshing snaps when on a metered connection:
    `sudo snap set system refresh.metered=hold`

### Connect Interfaces

- `snap connections vlc` prints a list of interfaces it can use.
- It shows a list of plugs and slots.
- `PLUG (consumer) --- Interface --- SLOT (provider)`
- `core` and `system` are synonymous when talking about plugs/slots
- Manual connections can be made `snap connect <snap>:<plug interface> <snap>:<slot interface>`
- e.g.
    - `sudo snap connect vlc:audio-record :audio-record`
    - `sudo snap disconnect vlc:audio-record :audio-record`
- A slot and a plug can only be connected if they have the same interface name.

### Configure Snaps

- Some snaps expose configuration options. Use `snap get` to list them, and `snap set` to set:
    ```
    $ sudo snap get nextcloud
    Key        Value
    mode       production
    nextcloud  {...}
    php        {...}
    ports      {...}
    private    {...}
    ```
- `{...}` indicate sub options, which can be explored with `sudo snap get nextcloud ports`
- `snap set nextcloud ports.http=81`
- `snap unset nextcloud ports.http` to revert a value to its default.
- `snap set nextcloud ports.http!` does the same, but can be mixed with other values:
- `snap set nextcloud ports.https! ports.http=81`

## MANAGING SNAPS

### Apps and Aliases

- Apps can be GUI or CLI.
- `snap aliases lxd`
- `snap unalias lxd`
- `snap prefer lxd`
- Can create own aliases:
    - `snap alias vlc my-vlc`
    - `snap aliases vlc`
    - `snap unalias my-vlc`

### Control Running Services

- Snaps can be started from GUI, CLI, or automatically.
- Snaps manage their own services, but admins may wish to tweak them, hence they provide their own commands to allow them to be inspected and their status changed.
- `snap services`
- `snap services vlc`
    - The output states whether it auto starts at startup, and whether it is currently active
- `snap start <snap name>`
- `snap stop <snap name>` # May cause the snap to malfunction, consider disable/enable
- `snap start --enable <snap name>` # Re-enable automatic starting from the next boot
- `snap stop --disable <snap name>` # Prevents it from running from the next boot
- `snap restart <snap name>` to restart a service
- Restart all services for `vlc`:
    - `sudo snap restart vlc`
- Restart a certain `vlc` service
    - `sudo snap restart vlc.daemon`
- Can inspect logs of services:
- `snap logs vlc`
- `snap logs vlc.daemon`
- `snap logs -f vlc.daemon` - Follow new options as they occur

### Create Data Snapshots

- A `snapshot` is a copy of the user, system and configuration data stored by snapd for one or more snaps.
- `snap save` to create a snapshot
- `snap check-snapshot`
- `snap restore 30`
- `snap forget 30`
- When a snapshot is removed it is automatically kept for `snapshots.automatic.retention` time:
    - `snap set system snapshots.automatic.retention=30h`
- Snapshots are stored in a zip, each zip contains the following `meta.json/archive.tgz/user/<username>.tgz`
- On ubuntu they are stored at `/var/lib/snapd/snapshots`

### Set system Options

- Can set some system wide options also with the `set` and `get` commands, but target `system`
- `snap set system some.option="some value"`
- `snap get system some.option`
- `system` covers `system`, `core`, and `snapd`
    - If the options is part of the system snap, will have two instances of the `word` system:
    - e.g. `snap set system system.timezone="Europe/London"`
- ...

### Inside App confinement

- strict/classic/devmode
- `snap info --verbose vlc` to get the see the `confinement` and `devmode` attributes.

## Publishing

- `snapcraft init` to create a `snap/snapcraft.yaml` file.
- The build process consists of iterating over configuration of `parts`, `plugins`, and `interfaces`
    - parts = building blocks, used to collect and build binaries
    - plugins = used within parts to parts for integration (e.g. python plugin)
    - interfaces = enable resource sharing between snaps and the host
- Process algorithm:
    1. Describe the meta data
    2. Add parts metadata to integrate applications using specific languages and frameworks:
        - Incorporate plugins with parts to integrate languages/or binaries
        - Use plugin metadata to locate your project, or sync with a remote repo
        - Set build dependencies, if required, and any runtime dependencies.
    3. Add interface metadata
- After a snap has been built, it can be installed locally with:
    - `sudo snap install my-snap-name_0.1_amd64.snap --dangerous --devmode`

## Build Apps with Parts

- Parts describe your application, where various components can be found, and build dependencies.
- A snap always has one or more parts
- Example:
    parts:
    my-part:
        # See 'snapcraft plugins'
        plugin: nil
    - plugin = Example python / go / java
    - sources = location of files requires to build your project
        - dir tree, or compress archive or a repo
        - e.g. `.`, `https://github.com/coderholic/pyradio.git`, `gnu-hello.tar.gz`
    - build-packages = A list of packages required to *build* the part, in the OS, not plugin, e.g. [`apt`, `sed`]
    - stage-packages = A list of packages required to *run* the page, also in the OS, not plugin.
- As per yaml spec can specify a list in either of these ways:
    ```
    build-packages: [g++, make, git, sed]

    build-packages:
    - g++
    - make
    - git
    - sed
    ```
