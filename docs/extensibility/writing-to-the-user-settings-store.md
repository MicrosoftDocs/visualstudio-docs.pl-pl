---
title: Zapisywanie do magazynu ustawień użytkownika | Microsoft Docs
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec4d9cdda975d0f80e9d8523ec18a19c24c9418a
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906210"
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika
Ustawienia użytkownika to ustawienia do zapisu, takie jak te w oknie dialogowym **Narzędzia/Opcje** , okna właściwości i niektóre inne okna dialogowe. Rozszerzenia programu Visual Studio mogą ich używać do przechowywania małych ilości danych. W tym instruktażu pokazano, jak dodać Notatnik do programu Visual Studio jako zewnętrzne narzędzie, odczytując z i zapisując do magazynu ustawień użytkownika.

## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika

1. Utwórz projekt VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj polecenie niestandardowe o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W UserSettingsStoreCommand.cs Dodaj następujące dyrektywy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. W MenuItemCallback Usuń treść metody i Pobierz magazyn ustawień użytkownika w następujący sposób:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Teraz Dowiedz się, czy Notatnik został już ustawiony jako narzędzie zewnętrzne. Należy wykonać iterację wszystkich zewnętrznych narzędzi, aby określić, czy ustawienie ToolCmd ma wartość "Notepad" w następujący sposób:

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

5. Jeśli Notatnik nie został ustawiony jako narzędzie zewnętrzne, ustaw go w następujący sposób:

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

6. Przetestuj kod. Należy pamiętać, że dodaje Notatnik jako narzędzie zewnętrzne, dlatego należy wycofać rejestr przed uruchomieniem go po raz drugi.

7. Skompiluj kod i Rozpocznij debugowanie.

8. W menu **Narzędzia** kliknij polecenie **Wywołaj UserSettingsStoreCommand**. Spowoduje to dodanie Notatnika do menu **Narzędzia** .

9. Teraz powinien zostać wyświetlony Notatnik w menu Narzędzia/Opcje, a kliknięcie przycisku **Notatnik** powinno spowodować wystąpienie Notatnika.
