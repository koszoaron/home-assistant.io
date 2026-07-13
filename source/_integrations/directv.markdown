---
title: DirecTV
description: Instructions on how to integrate DirecTV receivers into Home Assistant.
ha_category:
  - Media player
  - Remote
ha_release: 0.25
ha_iot_class: Local Polling
ha_domain: directv
ha_config_flow: true
ha_ssdp: true
ha_platforms:
  - media_player
  - remote
ha_integration_type: hub
---

The **DirecTV** {% term integration %} allows you to control a [DirecTV](https://www.directv.com) receiver and its client devices.

## Requirements

For proper integration with Home Assistant, your DirecTV device settings should allow "External Access".

This is done via series of settings found via **Menu** > **Settings & Help** > **Settings** > **Whole Home** > **External Device**:

- External Access: Allow
- Current Program: Allow
- Recordings: Allow

{% include integrations/config_flow.md %}

## Remote

The DirecTV remote platform allows you to send remote control buttons to a DirecTV receiver. It is automatically set up when a DirecTV receiver is configured.

### Changing channels in automations

To change the channel on a DirecTV receiver, use the [**Play specified media**](/actions/media_player.play_media/) action and select the DirecTV media player as the target.

To change a DirecTV channel from an automation or a script:

1. Go to {% my automations title="**Settings** > **Automations & scenes**" %}.
2. Open an existing automation or script, or select **Create automation** > **Create new automation**.
3. If you are setting up a new automation, add a trigger in the **When** section. Scripts do not need a trigger. They run when something else calls them.
4. In the **Then do** section, select **Add action**.
5. Select what you want to control. Under **By target**, select the DirecTV media player.
6. From the actions shown for that target, select **Play specified media**.
7. Enter the channel number as the **Media content ID** and use `channel` as the **Media content type**.
8. Select **Save**.

In YAML, refer to this action as `media_player.play_media`:

```yaml
action: media_player.play_media
target:
  entity_id: media_player.directv_receiver
data:
  media_content_id: "202"
  media_content_type: channel
```

### Sending remote commands in automations

To send remote control button commands to a DirecTV receiver, use the [**Send remote command**](/actions/remote.send_command/) action and select the DirecTV remote as the target.

To send a DirecTV remote command from an automation or a script:

1. Go to {% my automations title="**Settings** > **Automations & scenes**" %}.
2. Open an existing automation or script, or select **Create automation** > **Create new automation**.
3. If you are setting up a new automation, add a trigger in the **When** section. Scripts do not need a trigger. They run when something else calls them.
4. In the **Then do** section, select **Add action**.
5. Select what you want to control. Under **By target**, select the DirecTV remote.
6. From the actions shown for that target, select **Send remote command**.
7. Enter a command, or enter a list of commands.
8. Select **Save**.

In YAML, refer to this action as `remote.send_command`:

```yaml
action: remote.send_command
target:
  entity_id: remote.directv_receiver
data:
  command:
    - left
    - left
    - menu
    - select
```

The commands available to you depend on the DirecTV receiver. Supported commands include:

- `power`
- `poweron`
- `poweroff`
- `format`
- `pause`
- `rew`
- `replay`
- `stop`
- `advance`
- `ffwd`
- `record`
- `play`
- `guide`
- `active`
- `list`
- `exit`
- `back`
- `menu`
- `info`
- `up`
- `down`
- `left`
- `right`
- `select`
- `red`
- `green`
- `yellow`
- `blue`
- `chanup`
- `chandown`
- `prev`
- `0`
- `1`
- `2`
- `3`
- `4`
- `5`
- `6`
- `7`
- `8`
- `9`
- `dash`
- `enter`
