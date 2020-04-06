---
title: Zapisywanie do sklepu ustawień użytkownika | Dokumenty firmy Microsoft
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740364"
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika
Ustawienia użytkownika są zapisywalne ustawienia, takie jak te w **narzędzia / opcje** okna, właściwości okna i niektórych innych okien dialogowych. Rozszerzenia programu Visual Studio mogą używać ich do przechowywania niewielkich ilości danych. W tym przewodniku pokazano, jak dodać Notatnik do programu Visual Studio jako narzędzie zewnętrzne, odczytując i zapisując do magazynu ustawień użytkownika.

## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika

1. Utwórz projekt VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj niestandardowe polecenie o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia polecenia [niestandardowego,](../extensibility/creating-an-extension-with-a-menu-command.md) zobacz Tworzenie rozszerzenia za pomocą polecenia menu

2. W UserSettingsStoreCommand.cs dodaj następujące elementy za pomocą dyrektyw:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. W MenuItemCallback usuń treść metody i pobierz magazyn ustawień użytkownika w następujący sposób:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Teraz dowiedz się, czy Notatnik jest już ustawiony jako narzędzie zewnętrzne. Musisz iterować za pomocą wszystkich narzędzi zewnętrznych, aby ustalić, czy toolcmd ustawienie jest "Notatnik", w następujący sposób:

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

6. Przetestuj kod. Pamiętaj, że dodaje Notatnik jako narzędzie zewnętrzne, więc musisz wycofać rejestr przed uruchomieniem go po raz drugi.

7. Skompiluj kod i rozpocznij debugowanie.

8. W menu **Narzędzia** kliknij polecenie **Wywołaj userSettingsStoreCommand**. Spowoduje to dodanie Notatnika do menu **Narzędzia.**

9. Teraz powinieneś zobaczyć Notatnik w menu Narzędzia / Opcje, a kliknięcie **Notatnika** powinno wywołać wystąpienie Notatnika.
