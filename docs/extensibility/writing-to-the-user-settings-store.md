---
title: Zapisywanie Store ustawienia użytkownika | Dokumentacja firmy Microsoft
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe8187fe11f4818433aed847a7bc67d4a889ad3a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206884"
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika
Ustawienia użytkownika są zapisywalne ustawień, jak w powyższym **narzędzia / Opcje** okna dialogowego Właściwości systemu windows i niektórych innych oknach dialogowych. Rozszerzenia programu Visual Studio może użyć do przechowywania niewielkich ilości danych. W tym instruktażu przedstawiono sposób dodawania Notatnik w programie Visual Studio jako narzędzie zewnętrzne za odczytywanie z oraz zapisywanie w magazynie ustawień użytkownika.

## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika

1. Utwórz projekt VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj polecenie niestandardowe o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W UserSettingsStoreCommand.cs, Dodaj następujące instrukcje using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback Usuń treść metody i pobieranie użytkownika, które ustawienia są przechowywane, w następujący sposób:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Teraz Dowiedz się, czy program Notatnik jest już ustawiona jako zewnętrznego narzędzia. Musisz wykonać iterację wszystkich zewnętrznych narzędzi, aby ustalić, czy ustawienie ToolCmd "Notatnik", w następujący sposób:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Notatnik nie została ustawiona jako narzędzie zewnętrzne, ustaw go w następujący sposób:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Przetestuj kod. Należy pamiętać o tym, jego dodaje Notatnik jako zewnętrznego narzędzia, więc musisz wycofać rejestru przed jego uruchomieniem po raz drugi.

7. Skompilować kod i rozpocząć debugowanie.

8. Na **narzędzia** menu, kliknij przycisk **wywołania UserSettingsStoreCommand**. Spowoduje to dodanie Notatnika na potrzeby **narzędzia** menu.

9. Powinien zostać wyświetlony Notatnik w menu Narzędzia / Opcje menu, a następnie klikając polecenie **Notatnik** należy wywołać wystąpienie Notatnika.