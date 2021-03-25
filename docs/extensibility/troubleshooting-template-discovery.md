---
title: Rozwiązywanie problemów z odnajdywaniem szablonów w programie Visual Studio | Microsoft Docs
description: Dowiedz się, jak włączyć rejestrowanie diagnostyczne, aby rozwiązać problemy z wdrażaniem projektów niestandardowych i szablonów w Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82b7b3f5eced4c8e24830fba34e47d224186949d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072952"
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

3. Otwórz [wiersz polecenia dla deweloperów](../ide/reference/command-prompt-powershell.md) instalacji i uruchom system `devenv /updateConfiguration` .

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
