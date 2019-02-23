---
title: Zapisywanie Store ustawienia użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a576c692ffb03f631aa0d85d02b99ad74cd4b9c1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705271"
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika
Ustawienia użytkownika są zapisywalne ustawień, jak w powyższym **narzędzia / Opcje** okna dialogowego Właściwości systemu windows i niektórych innych oknach dialogowych. Rozszerzenia programu Visual Studio może użyć do przechowywania niewielkich ilości danych. W tym instruktażu przedstawiono sposób dodawania Notatnik w programie Visual Studio jako narzędzie zewnętrzne za odczytywanie z oraz zapisywanie w magazynie ustawień użytkownika.

### <a name="backing-up-your-user-settings"></a>Tworzenie kopii zapasowej ustawień użytkownika

1.  Musi być możliwe zresetowanie ustawień zewnętrznych narzędzi, dzięki czemu można debugować i powtórz procedurę. Aby to zrobić, należy zapisać ustawienia oryginalne tak, aby można je przywrócić zgodnie z potrzebami.

2.  Open Regedit.exe.

3.  Przejdź do pozycji narzędzia HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.

    > [!NOTE]
    >  Upewnij się, że przeglądasz klucz, który zawiera \14.0Exp\ i nie \14.0\\. Po uruchomieniu doświadczalnym wystąpieniu programu Visual Studio, ustawień użytkownika znajdują się w gałęzi rejestru "14.0Exp".

4.  Kliknij prawym przyciskiem myszy podklucz \External Tools\, a następnie kliknij przycisk **wyeksportować**. Upewnij się, że **wybrana gałąź** jest zaznaczone.

5.  Zapisz plik wynikowy Tools.reg zewnętrznych.

6.  Później, gdy chcesz zresetować ustawienia zewnętrznych narzędzi, wybierz SDKs\Windows\v8.0a\bin\netfx HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External klucza rejestru i kliknij przycisk **Usuń** w menu kontekstowym.

7.  Gdy **Potwierdzanie usunięcia klucza** pojawi się okno dialogowe, kliknij przycisk **tak**.

8.  Kliknij prawym przyciskiem myszy plik Tools.reg zewnętrznego, który został wcześniej zapisany, kliknij przycisk **Otwórz za pomocą**, a następnie kliknij przycisk **Edytora rejestru**.

## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika

1.  Utwórz projekt VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj polecenie niestandardowe o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2.  W UserSettingsStoreCommand.cs, Dodaj następujące instrukcje using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3.  MenuItemCallback Usuń treść metody i pobieranie użytkownika, które ustawienia są przechowywane, w następujący sposób:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4.  Teraz Dowiedz się, czy program Notatnik jest już ustawiona jako zewnętrznego narzędzia. Musisz wykonać iterację wszystkich zewnętrznych narzędzi, aby ustalić, czy ustawienie ToolCmd "Notatnik", w następujący sposób:

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

5.  Notatnik nie została ustawiona jako narzędzie zewnętrzne, ustaw go w następujący sposób:

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

6.  Przetestuj kod. Należy pamiętać o tym, jego dodaje Notatnik jako zewnętrznego narzędzia, więc musisz wycofać rejestru przed jego uruchomieniem po raz drugi.

7.  Skompilować kod i rozpocząć debugowanie.

8.  Na **narzędzia** menu, kliknij przycisk **wywołania UserSettingsStoreCommand**. Spowoduje to dodanie Notatnika na potrzeby **narzędzia** menu.

9. Powinien zostać wyświetlony Notatnik w menu Narzędzia / Opcje menu, a następnie klikając polecenie **Notatnik** należy wywołać wystąpienie Notatnika.