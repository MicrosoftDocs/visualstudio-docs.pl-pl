---
title: Korzystanie z ustawień magazynu | Microsoft Docs
description: Dowiedz się, jak odczytywać dane z magazynu ustawień konfiguracji, które są tylko do odczytu, Visual Studio i vsPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898386"
---
# <a name="using-the-settings-store"></a>Korzystanie z magazynu ustawień
Istnieją dwa rodzaje magazynów ustawień:

- Ustawienia konfiguracji, które są ustawieniami tylko do Visual Studio i vsPackage. Visual Studio scala ustawienia ze wszystkich znanych plików pkgdef w tym magazynie.

- Ustawienia użytkownika, które są ustawieniami zapisywalnymi, takimi  jak te, które są wyświetlane na stronach w oknie dialogowym Opcje, na stronach właściwości i niektórych innych oknach dialogowych. Visual Studio rozszerzenia mogą używać ich do lokalnego przechowywania małych ilości danych.

  W tym przewodniku pokazano, jak odczytywać dane z magazynu ustawień konfiguracji. Zobacz [Zapisywanie w magazynie ustawień użytkownika,](../extensibility/writing-to-the-user-settings-store.md) aby uzyskać wyjaśnienie, jak zapisywać w magazynie ustawień użytkownika.

## <a name="creating-the-example-project"></a>Tworzenie przykładowego projektu
 W tej sekcji przedstawiono sposób tworzenia prostego projektu rozszerzenia za pomocą polecenia menu w celu prezentacji.

1. Każde Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX o nazwie `SettingsStoreExtension` . Szablon projektu VSIX można znaleźć w oknie **dialogowym Nowy** projekt w obszarze **Visual C# / Extensibility**.

2. Teraz dodaj szablon niestandardowego elementu polecenia o **nazwie SettingsStoreCommand**. W **oknie dialogowym Dodawanie** nowego elementu przejdź do **pozycji Visual C# /Rozszerzalność** i wybierz pozycję **Polecenie niestandardowe.** W **polu** Nazwa w dolnej części okna zmień nazwę pliku polecenia na **SettingsStoreCommand.cs.** Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz Creating an Extension with a Menu Command (Tworzenie [rozszerzenia za pomocą polecenia menu).](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Korzystanie z magazynu ustawień konfiguracji
 W tej sekcji przedstawiono sposób wykrywania i wyświetlania ustawień konfiguracji.

1. W pliku SettingsStorageCommand.cs dodaj następujące dyrektywy using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. W pliku usuń treść metody i dodaj następujące wiersze, aby `MenuItemCallback` pobrać magazyn ustawień konfiguracji:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    To <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> zarządzana klasa pomocnika w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> usłudze.

3. Teraz dowiedz się, Windows Phone zainstalowano narzędzia. Kod powinien wyglądać tak:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Przetestuj kod. Skompilowanie projektu i rozpoczęcie debugowania.

5. W wystąpieniu eksperymentalnym w menu **Narzędzia** kliknij polecenie Wywołaj **ustawieniaStoreCommand**.

    Powinno zostać wyświetlony komunikat Microsoft **Windows Phone Narzędzia deweloperskie:** true (prawda) **lub** **false (fałsz).**

   Visual Studio przechowuje ustawienia w rejestrze systemowym.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Aby zweryfikować ustawienia konfiguracji za pomocą edytora rejestru

1. Otwórz Regedit.exe.

2. Przejdź do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Upewnij się, że używasz klucza zawierającego element \14.0Exp_Config\, a nie \14.0_Config \\ . Po uruchomieniu eksperymentalnego wystąpienia usługi Visual Studio ustawienia konfiguracji znajdują się w gałęzi rejestru "14.0Exp_Config".

3. Rozwiń węzeł \Installed Products\. Jeśli komunikat w poprzednich krokach to **Microsoft Windows Phone Narzędzia deweloperskie Zainstalowane: True,** to folder \Installed Products\ powinien zawierać węzeł microsoft Windows Phone Narzędzia deweloperskie węźle. Jeśli komunikat to **Microsoft Windows Phone Narzędzia deweloperskie Zainstalowane: False**, to \Installed Products\ nie powinien zawierać węzła microsoft Windows Phone Narzędzia deweloperskie węzła.
