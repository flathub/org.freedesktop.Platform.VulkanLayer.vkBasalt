# org.freedesktop.Platform.VulkanLayer.vkBasalt

This is the [vkBasalt](https://github.com/DadSchoorse/vkBasalt/) flatpak.

In the documentation below, `$APP_ID` will be referred to the application ID. Steam's ID for example is `com.valvesoftware.Steam`, however this differs per application.

## Temporarily enable vkBasalt on an application
To temporarily enable vkBasalt on an application, run the following command:
```bash
flatpak run --env=ENABLE_VKBASALT=1 $APP_ID
```

## Permanently enable vkBasalt on an application
To permanently enable vkBasalt on an application, run the following command:
```bash
flatpak override --env=ENABLE_VKBASALT=1 $APP_ID
```

You may have to add `--user` if the application in question was installed per user.

## Enable vkBasalt per game on Steam
To enable vkBasalt per game on Steam, edit the launch option of a game and add:

```ini
ENABLE_VKBASALT=1 %command%
```

## Custom configurations
By default, games will utilize the vkBasalt configuration from [config/vkBasalt.conf](https://github.com/DadSchoorse/vkBasalt/blob/master/config/vkBasalt.conf), which is located in `/var/lib/flatpak/runtime/org.freedesktop.Platform.VulkanLayer.vkBasalt/[...]/active/files/etc/vkBasalt/vkBasalt.conf` if installed for the system or `$HOME/.local/share/flatpak/runtime/org.freedesktop.Platform.VulkanLayer.vkBasalt/[...]/active/files/etc/vkBasalt/vkBasalt.conf` if installed per user.

You can create a custom `vkBasalt.conf` file at `$HOME/.var/app/$APP_ID/config/vkBasalt`, where games will utilize this configuration file instead:

```bash
mkdir $HOME/.var/app/$APP_ID/config/vkBasalt
curl https://raw.githubusercontent.com/DadSchoorse/vkBasalt/master/config/vkBasalt.conf -o $HOME/.var/app/$APP_ID/config/vkBasalt/vkBasalt.conf
$EDITOR $HOME/.var/app/$APP_ID/config/vkBasalt/vkBasalt.conf
```

