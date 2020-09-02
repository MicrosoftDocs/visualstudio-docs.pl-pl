---
title: Rozwiązywanie problemów z odnajdywaniem szablonów w programie Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89ff5b9974f20841378f367c3cb631a8d4cf7787
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235046"
---
# <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu

Jeśli wystąpią problemy z wdrażaniem szablonów projektu lub elementów, możesz włączyć rejestrowanie diagnostyczne.

::: moniker range="vs-2017"

1. Utwórz plik pkgdef w folderze *Common7\IDE\CommonExtensions* dla instalacji. Na przykład *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Utwórz plik pkgdef w folderze *Common7\IDE\CommonExtensions* dla instalacji. Na przykład *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Dodaj następujący plik do pliku pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Otwórz [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) instalacji i uruchom system `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Otwórz program Visual Studio i Uruchom okna dialogowe Nowy projekt i nowy element, aby zainicjować drzewa szablonów.

   Dziennik szablonu jest teraz wyświetlany w **%LocalAppData%\Microsoft\VisualStudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (identyfikator wystąpienia odpowiada identyfikatorowi instalacji wystąpienia programu Visual Studio). Każde inicjowanie drzewa szablonów dołącza wpisy do tego dziennika.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otwórz program Visual Studio i Uruchom okna dialogowe **Utwórz nowy projekt** i **nowy element** , aby zainicjować drzewa szablonów.

   Dziennik szablonu jest teraz wyświetlany w **%LocalAppData%\Microsoft\VisualStudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (identyfikator wystąpienia odpowiada identyfikatorowi instalacji wystąpienia programu Visual Studio). Każde inicjowanie drzewa szablonów dołącza wpisy do tego dziennika.

::: moniker-end

Plik dziennika zawiera następujące kolumny:

- **FullPathToTemplate**, który ma następujące wartości:

  - 1 dla wdrożenia opartego na manifeście

  - 0 w przypadku wdrożenia opartego na dyskach

- **TemplateFileName**

- Inne właściwości szablonu

> [!NOTE]
> Aby wyłączyć rejestrowanie, usuń plik pkgdef lub zmień wartość `EnableTemplateDiscoveryLog` na `dword:00000000` , a następnie uruchom `devenv /updateConfiguration` ponownie.

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
