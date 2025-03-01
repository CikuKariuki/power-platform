---
title: Notify function in Power Apps
description: Reference information including syntax and examples for the Notify function in Power Apps.
author: gregli-msft

ms.topic: reference
ms.custom: canvas
ms.reviewer: mkaur
ms.date: 02/28/2020
ms.subservice: power-fx
ms.author: gregli
search.audienceType:
  - maker
search.app:
  - PowerApps
contributors:
  - gregli-msft
  - mduelae
---

# Notify function in Power Apps

Displays a banner message to the user.

## Description

The **Notify** function displays a banner message to the user at the top of the screen. The notification will remain until the user dismisses it or the timeout expires which defaults to 10 seconds.

An appropriate color and icon are used depending on the type of the message. The type is specified by the second argument to the function:

> [!NOTE]
> The character limit for **Notify** function is 500 characters.

| NotificationType Argument                  | Description                            |
| ------------------------------------------ | -------------------------------------- |
| **NotificationType.Error**                 | Displays the message as an error.      |
| **NotificationType.Information** (Default) | Displays the message as informational. |
| **NotificationType.Success**               | Displays the message as success.       |
| **NotificationType.Warning**               | Displays the message as a warning.     |

Messages are shown both when authoring your app and when end users are using your app.

**Notify** can only be used in [behavior formulas](/power-apps/maker/canvas-apps/working-with-formulas-in-depth).

**Notify** can be paired with the [**IfError**](function-iferror.md) function to detect and report errors with a custom error message.

Power Apps can also send push notifications using an entirely different mechanism from **Notify**. For more information see [Send a notification in Power Apps](/power-apps/maker/canvas-apps/add-notifications).

**Notify** always returns _true_.

Note: This function was previously named **ShowError** when it could only display error messages.

## Syntax

**Notify**( _Message_ [, _NotificationType_ [ , *Timeout* ] ] )

- _Message_ – Required. Message to display to the user.
- _NotificationType_ – Optional. Type of the message to display from the table above. The default is **NotificationType.Information**.
- _Timeout_ – Optional. Number of milliseconds to wait before automatically dismissing the notification. The default is 10 seconds (or 10,000 milliseconds). The notification will be displayed indefinitely with a _Timeout_ of 0.

## Examples

### Step by step

1. Add a **Button** control to your screen.

2. Set the **OnSelect** property of the **Button** to the formula:

   ```powerapps-dot
   Notify( "Hello, World" )
   ```

3. Click or press the button.

   Each time the button is clicked, the message **Hello, World** is displayed to the user as informational. It will dismiss automatically in 10 seconds (default timeout) if the user does not dismiss it or press the button again.

   ![In the authoring environment, showing Button.OnSelect calling Notify and displaying the resulting Hello, World message as a blue banner message for the user.](media/function-showerror/hello-world.png)

4. Change the type of message to indicate an error. Add a second argument to our formula:

   ```powerapps-dot
   Notify( "Hello, World", NotificationType.Error )
   ```

5. Click or press the button.

   Now each time the button is clicked, the message **Hello, World** is displayed to the user as an error. It will dismiss automatically in 10 seconds (default timeout) if the user does not dismiss it or press the button again.

   ![In the authoring environment, showing Button.OnSelect calling Notify and displaying the resulting Hello, World message as a red banner message for the user.](media/function-showerror/hello-world-error.png)

6. Change the type of message to indicate a warning. Change the second argument in our formula:

   ```powerapps-dot
   Notify( "Hello, World", NotificationType.Warning, 4000 )
   ```

7. Click or press the button.

   Now each time the button is clicked, the message **Hello, World** is displayed to the user as a warning. It will dismiss automatically in 4 seconds (4,000 milliseconds) if the user does not dismiss it or press the button again.

   ![In the authoring environment, showing Button.OnSelect calling Notify and displaying the resulting Hello, World message as an orange banner message for the user.](media/function-showerror/hello-world-warning.png)

8. Change the type of message to indicate success. Change the second argument in our formula:

   ```powerapps-dot
   Notify( "Hello, World", NotificationType.Success, 0 )
   ```

9. Click or press the button.

   Now each time the button is clicked, the message **Hello, World** is displayed to the user as success. With a **0** timeout, the notification will only be dismissed by the user or by pressing the button again.

   ![In the authoring environment, showing Button.OnSelect calling Notify and displaying the resulting Hello, World message as a green banner message for the user.](media/function-showerror/hello-world-success.png)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
