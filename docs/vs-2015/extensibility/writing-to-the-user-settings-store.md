---
title: Zapisywanie do magazynu ustawień użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821289"
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia użytkownika to ustawienia do zapisu, takie jak te w oknie dialogowym **Narzędzia/Opcje** , okna właściwości i niektóre inne okna dialogowe. Rozszerzenia programu Visual Studio mogą ich używać do przechowywania małych ilości danych. W tym instruktażu pokazano, jak dodać Notatnik do programu Visual Studio jako zewnętrzne narzędzie, odczytując z i zapisując do magazynu ustawień użytkownika.  
  
### <a name="backing-up-your-user-settings"></a>Tworzenie kopii zapasowej ustawień użytkownika  
  
1. Musisz mieć możliwość zresetowania ustawień zewnętrznych narzędzi, aby można było debugować i powtarzać procedurę. W tym celu należy zapisać oryginalne ustawienia, aby można je było przywrócić zgodnie z potrzebami.  
  
2. Otwórz Regedit.exe.  
  
3. Przejdź do HKEY_CURRENT_USER narzędzia \Software\Microsoft\VisualStudio\14.0Exp\External \\ .  
  
    > [!NOTE]
    > Upewnij się, że przeglądasz klucz, który zawiera \14.0Exp\, a nie \ 14,0 \\ . Po uruchomieniu eksperymentalnego wystąpienia programu Visual Studio ustawienia użytkownika znajdują się w gałęzi rejestru "14.0 EXP".  
  
4. Kliknij prawym przyciskiem myszy pozycję \External Tools \ podklucz, a następnie kliknij pozycję **Eksportuj**. Upewnij się, że wybrana **gałąź** jest zaznaczona.  
  
5. Zapisz plik reg z wynikiem zewnętrznym.  
  
6. Później, jeśli chcesz zresetować ustawienia zewnętrznych narzędzi, wybierz klucz rejestru HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ Registry i kliknij przycisk **Usuń** w menu kontekstowym.  
  
7. Gdy pojawi się okno dialogowe **Potwierdzanie usunięcia klucza** , kliknij przycisk **tak**.  
  
8. Kliknij prawym przyciskiem myszy plik. reg zewnętrznych narzędzi, który został zapisany wcześniej, kliknij polecenie **Otwórz za pomocą**, a następnie kliknij przycisk **Edytor rejestru**.  
  
## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawień użytkownika  
  
1. Utwórz projekt VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj polecenie niestandardowe o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. W UserSettingsStoreCommand.cs Dodaj następujące instrukcje using:  
  
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
