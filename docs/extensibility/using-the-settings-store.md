---
title: Korzystanie z magazynu ustawień | Microsoft Docs
description: Dowiedz się, jak odczytywać dane z magazynu ustawień konfiguracji, które są ustawieniami programu Visual Studio i pakietu VSPackage tylko do odczytu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a84fa551a4a3ea10b212832c0891fb0d7d19b2f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060188"
---
# <a name="using-the-settings-store"></a>Korzystanie z magazynu ustawień
Istnieją dwa rodzaje magazynów ustawień:

- Ustawienia konfiguracji, które są tylko do odczytu i są ustawieniami programu Visual Studio i pakietu VSPackage. Program Visual Studio scala ustawienia ze wszystkich znanych plików. pkgdef w tym magazynie.

- Ustawienia użytkownika, które są zapisywalne ustawienia, takie jak te, które są wyświetlane na stronach w oknie dialogowym **Opcje** , strony właściwości i niektóre inne okna dialogowe. Rozszerzenia programu Visual Studio mogą ich używać do lokalnego przechowywania niewielkich ilości danych.

  W tym instruktażu przedstawiono sposób odczytywania danych z magazynu ustawień konfiguracji. Zapoznaj się z artykułem [Zapisywanie w magazynie ustawień użytkownika,](../extensibility/writing-to-the-user-settings-store.md) aby dowiedzieć się, jak pisać do magazynu ustawień użytkownika.

## <a name="creating-the-example-project"></a>Tworzenie przykładowego projektu
 W tej sekcji przedstawiono sposób tworzenia prostego projektu rozszerzenia z poleceniem menu dla demonstracji.

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt VSIX o nazwie `SettingsStoreExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.

2. Teraz Dodaj niestandardowy szablon elementu polecenia o nazwie **SettingsStoreCommand**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na **SettingsStoreCommand. cs**. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Korzystanie z magazynu ustawień konfiguracji
 W tej sekcji przedstawiono sposób wykrywania i wyświetlania ustawień konfiguracji.

1. W pliku SettingsStorageCommand. cs Dodaj następujące dyrektywy using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. W programie `MenuItemCallback` Usuń treść metody, a następnie Dodaj następujące wiersze do magazynu ustawień konfiguracji:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>Jest zarządzaną klasą pomocnika za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> usługi.

3. Teraz Dowiedz się, czy zainstalowano narzędzia Windows Phone. Kod powinien wyglądać następująco:

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

4. Przetestuj kod. Skompiluj projekt i Rozpocznij debugowanie.

5. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj SettingsStoreCommand**.

    Powinno zostać wyświetlone okno komunikatu z informacją, że **firma Microsoft Windows Phone narzędzia deweloperskie:**  po którym następuje **wartość true** lub **false**.

   Program Visual Studio utrzymuje magazyn ustawień w rejestrze systemowym.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Aby sprawdzić ustawienia konfiguracji przy użyciu Edytora rejestru

1. Otwórz Regedit.exe.

2. Przejdź do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Upewnij się, że przeglądasz klucz zawierający \ 14.0Exp_Config \ i nie \ 14.0_Config \\ . Po uruchomieniu eksperymentalnego wystąpienia programu Visual Studio ustawienia konfiguracji znajdują się w gałęzi rejestru "14.0Exp_Config".

3. Rozwiń węzeł \Installed Productss \. Jeśli komunikat w poprzednich krokach to **Microsoft Windows Phone narzędzia deweloperskie zainstalowany: true**, a następnie \Installed Products \ powinien zawierać węzeł Narzędzia deweloperskie Windows Phone firmy Microsoft. Jeśli wiadomość jest **zainstalowaną przez firmę microsoft Windows Phone narzędzia deweloperskie: false**, \Installed produkty \ nie powinny zawierać węzła narzędzia deweloperskie Windows Phone firmy Microsoft.
