---
title: v2 Modes
---

## InspIRCd Modes

InspIRCd supports five types of mode:

Type      | Parameter when adding?       | Parameter when removing?     | Can be set multiple times?       | Description
--------- | ---------------------------- | ---------------------------- | -------------------------------- | -----------
Switch    | No                           | No                           | No                               | Toggles the behaviour of a feature on a channel or user.
Parameter | Yes                          | No                           | No                               | Enables and configures the behaviour of a feature on a channel or user.
ParamBoth | Yes                          | Yes                          | No                               | The same as a Parameter mode only the parameter must be specified to remove it.
Prefix    | Yes; channel member nickname | Yes; channel member nickname | Yes; once per channel member     | Grants/revokes a status rank to the user specified in the parameter.
List      | Yes                          | Yes                          | Yes; up to the maximum list size | Adds/removes entries from a list.

### Channel Modes

This page only lists core channel modes. For details on the channel modes of a specific module please refer to [the appropriate page for that module](/2/modules).

Name       | Character | Type      | Parameter Syntax | Description
---------- | --------- | --------- | ---------------- | -----------
ban        | b         | List      | `<mask>`         | Bans users matching &lt;mask&gt; from joining the channel.
inviteonly | i         | Switch    | *None*           | Prevents users from joining the channel without an invite.
key        | k         | ParamBoth | `<key>`          | Prevents users from joining the channel who have not specified the &lt;key&gt; password.
limit      | l         | Parameter | `<count>`        | Allows no more than &lt;count&gt; users to join the channel.
moderated  | m         | Switch    | *None*           | Prevents users without a prefix rank from messaging the channel.
noextmsg   | n         | Switch    | *None*           | Prevents users who are not in the channel from messaging the channel.
op         | o         | Prefix    | `<nick>`         | Grants channel operator status to &lt;nick&gt;.
private    | p         | Switch    | *None*           | Hides the channel in `/WHOIS` from people who are not a member. You probably want the `s` (secret) channel mode rather than this.
secret     | s         | Switch    | *None*           | Hides the channel in `/WHOIS` and `/LIST` from people who are not a member.
topiclock  | t         | Switch    | *None*           | Prevents non-channel operators from changing the channel topic.
voice      | v         | Prefix    | `<nick>`         | Grants channel voice status to &lt;nick&gt;.

#### Example Usage

Bans users matching `*!*@example.com` from joining \#channel:

```plaintext
/MODE #channel +b *!*@example.com
```

Sets the channel key for \#cheese to "cheddar":

```plaintext
/MODE #channel +k cheddar
```

Removes the channel key for \#cheese:

```plaintext
/MODE #channel -k cheddar
```

Limits \#channel to 100 users:

```plaintext
/MODE #channel +l 100
```

Grants channel operator status to Sadie in \#channel:

```plaintext
/MODE #channel +o Sadie
```

Removes channel operator status from Sadie in \#channel:

```plaintext
/MODE #channel -o Sadie
```

Grants channel voice status to Sadie in \#channel:

```plaintext
/MODE #channel +v Sadie
```

Removes channel voice status from Sadie in \#channel:

```plaintext
/MODE #channel -v Sadie
```

### User Modes

This page only lists core user modes. For details on the user modes of a specific module please refer to [the appropriate page for that module](/2/modules).

Name      | Character | Type      | Parameter Syntax  | Description
--------- | --------- | --------- | ----------------- | -----------
invisible | i         | Switch    | *None*            | Marks the user as invisible.
oper      | o         | Switch    | *None*            | Marks the user as a server operator (can only be set by the server).
snomask   | s         | Parameter | `(+|-)<snomasks>` | Enables receiving the specified types of [server operator notice](/2/snomasks).
wallops   | w         | Switch    | *None*            | Enables receiving `/WALLOPS` messages from server operators.

#### Example Usage

Enables snomasks `l` (LINK) and `L` (REMOTELINK) and disables snomask `d` (DEBUG):

```plaintext
/MODE YourNick +s +lL-d
```

Enables all available snomasks:

```plaintext
/MODE YourNick +s +*
```

Disables all enabled snomasks:

```plaintext
/MODE YourNick -s
```
