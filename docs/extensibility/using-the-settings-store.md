---
title: Za pomocą Store ustawienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59f26e4e8972f02740db45760e5b2e876c300bd1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045404"
---
# <a name="using-the-settings-store"></a>Korzystanie z magazynu ustawień
Istnieją dwa rodzaje ustawień magazynów:

- Ustawienia konfiguracji, które są tylko do odczytu ustawień programu Visual Studio i pakietu VSPackage. Program Visual Studio scala ustawienia ze wszystkich wygenerowanych plików znanych .pkgdef tego magazynu.

- Ustawienia użytkownika, które są zapisywalne ustawienia takie jak te, które są wyświetlane na stronach **opcje** okno dialogowe strony właściwości i niektórych innych oknach dialogowych. Rozszerzenia programu Visual Studio może użyć lokalnego przechowywania niewielkich ilości danych.

  W tym instruktażu pokazano, jak można odczytać danych z magazynu ustawień konfiguracji. Zobacz [zapisywania Store ustawienia użytkownika](../extensibility/writing-to-the-user-settings-store.md) opis zapisu w magazynie ustawień użytkownika.

## <a name="creating-the-example-project"></a>Tworzenie projektu w przykładzie
 W tej sekcji pokazano, jak utworzyć projekt proste rozszerzenie za pomocą polecenia menu celów demonstracyjnych.

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od Projekt wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Tworzenie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu VSIX, o nazwie `SettingsStoreExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.

2. Teraz Dodaj polecenie niestandardowe szablon elementu o nazwie **SettingsStoreCommand**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowego**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **SettingsStoreCommand.cs**. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Za pomocą Store ustawień konfiguracji
 W tej sekcji pokazano, jak wykrywać i wyświetlanie ustawień konfiguracji.

1. W pliku SettingsStorageCommand.cs, Dodaj następujące instrukcje using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. W `MenuItemCallback`, Usuń treść metody i dodaj następujące wiersze Pobierz z magazynu ustawień konfiguracji:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Jest klasą pomocnika zarządzane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> usługi.

3. Teraz Dowiedz się, czy są zainstalowane narzędzia Windows Phone. Kod powinien wyglądać następująco:

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

4. Przetestuj kod. Skompiluj projekt, a następnie rozpocząć debugowanie.

5. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania SettingsStoreCommand**.

    Powinny zostać wyświetlone okno komunikatu powiedzenie **Microsoft Windows Phone Developer Tools:** następuje **True** lub **False**.

   Visual Studio przechowuje magazynu ustawień w rejestrze systemowym.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Aby sprawdzić ustawienia konfiguracji za pomocą Edytora rejestru

1. Open Regedit.exe.

2. Przejdź do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.

    > [!NOTE]
    >  Upewnij się, że przeglądasz klucz, który zawiera \14.0Exp_Config\ i nie \14.0_Config\\. Po uruchomieniu doświadczalnym wystąpieniu programu Visual Studio, ustawienia konfiguracyjne znajdują się w gałęzi rejestru "14.0Exp_Config".

3. Rozwiń węzeł \Installed Products\. Jeśli komunikat w poprzednich krokach jest **zainstalowane narzędzia dla deweloperów do programu Microsoft Windows Phone: Wartość true,**, a następnie \Installed Products\ powinien zawierać węzeł Microsoft Windows Phone Developer Tools. Jeśli komunikat jest **zainstalowane narzędzia dla deweloperów do programu Microsoft Windows Phone: FALSE**, a następnie \Installed Products\ nie może zawierać węzeł Microsoft Windows Phone Developer Tools.