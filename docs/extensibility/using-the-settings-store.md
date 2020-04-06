---
title: Korzystanie z Sklepu ustawień | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698517"
---
# <a name="using-the-settings-store"></a>Korzystanie z magazynu ustawień
Istnieją dwa rodzaje sklepów ustawień:

- Ustawienia konfiguracji, które są tylko do odczytu Visual Studio i VSPackage ustawienia. Program Visual Studio scala ustawienia ze wszystkich znanych plików pkgdef do tego magazynu.

- Ustawienia użytkownika, które są ustawieniami zapisywalnymi, takimi jak te, które są wyświetlane na stronach w oknie dialogowym **Opcje,** na stronach właściwości i niektórych innych oknach dialogowych. Rozszerzenia programu Visual Studio mogą używać ich do lokalnego przechowywania małych ilości danych.

  W tym przewodniku pokazano, jak odczytać dane z magazynu ustawień konfiguracji. Zobacz [Zapisywanie do magazynu ustawień użytkownika, aby](../extensibility/writing-to-the-user-settings-store.md) uzyskać wyjaśnienie sposobu zapisu w magazynie ustawień użytkownika.

## <a name="creating-the-example-project"></a>Tworzenie przykładowego projektu
 W tej sekcji pokazano, jak utworzyć prosty projekt rozszerzenia z poleceniem menu do demonstracji.

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierał zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX o nazwie `SettingsStoreExtension`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C# / Extensibility**.

2. Teraz dodaj niestandardowy szablon elementu polecenia o nazwie **SettingsStoreCommand**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji Visual **C# / Extensibility** i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na **SettingsStoreCommand.cs**. Aby uzyskać więcej informacji na temat tworzenia polecenia [niestandardowego,](../extensibility/creating-an-extension-with-a-menu-command.md) zobacz Tworzenie rozszerzenia za pomocą polecenia menu

## <a name="using-the-configuration-settings-store"></a>Korzystanie z magazynu ustawień konfiguracji
 W tej sekcji pokazano, jak wykrywać i wyświetlać ustawienia konfiguracji.

1. W pliku SettingsStorageCommand.cs dodaj następujące elementy za pomocą dyrektyw:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. W `MenuItemCallback`programie usuń treść metody i dodaj te wiersze, aby uzyskać magazyn ustawień konfiguracji:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Jest <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> zarządzaną klasą pomocnika <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> za pomocą usługi.

3. Teraz dowiedz się, czy narzędzia windows phone są zainstalowane. Kod powinien wyglądać następująco:

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

4. Przetestuj kod. Skompiluj projekt i rozpocznij debugowanie.

5. W przypadku wystąpienia eksperymentalnego w menu **Narzędzia** kliknij polecenie **Wywołaj polecenie Wywołaj pozycję UstawieniaStoreCommand**.

    Powinno zostać wyświetlone okno komunikatu z napisem **Microsoft Windows Phone Developer Tools:** następuje **prawda** lub **fałsz**.

   Visual Studio przechowuje magazyn ustawień w rejestrze systemowym.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Aby zweryfikować ustawienia konfiguracji za pomocą edytora rejestru

1. Otwórz regedit.exe.

2. Przejdź do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.

    > [!NOTE]
    > Upewnij się, że patrzysz na klucz, który zawiera \14.0Exp_Config\, a nie\\\14.0_Config . Po uruchomieniu eksperymentalnego wystąpienia programu Visual Studio ustawienia konfiguracji znajdują się w gałęzi rejestru "14.0Exp_Config".

3. Rozwiń węzeł \Zainstalowane produkty\. Jeśli komunikat w poprzednich krokach jest **Zainstalowany program Microsoft Windows Phone Narzędzia deweloperskie: True**, a następnie \Zainstalowane produkty\ powinien zawierać węzeł Microsoft Windows Phone Developer Tools. Jeśli komunikat jest **zainstalowanymi narzędziami deweloperskimi systemu Microsoft Windows Phone: False**, a następnie \Zainstalowane produkty\ nie powinny zawierać węzła Microsoft Windows Phone Developer Tools.
