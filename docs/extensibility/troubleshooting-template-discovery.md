---
title: Rozwiązywanie problemów z odnajdywania szablonów w programie Visual Studio | Dokumenty firmy Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698931"
---
# <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu

Jeśli napotkasz problemy z wdrażaniem szablonów projektu lub elementów, można włączyć rejestrowanie diagnostyczne.

::: moniker range="vs-2017"

1. Utwórz plik pkgdef w folderze *Common7\IDE\CommonExtensions* dla instalacji. Na przykład *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Utwórz plik pkgdef w folderze *Common7\IDE\CommonExtensions* dla instalacji. Na przykład *C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Dodaj następujące elementy do pliku pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Otwórz [wiersz polecenia dewelopera](/dotnet/framework/tools/developer-command-prompt-for-vs) dla `devenv /updateConfiguration`instalacji i uruchom program .

::: moniker range="vs-2017"

4. Otwórz program Visual Studio i uruchom okna dialogowe Nowy projekt i Nowy element, aby zainicjować oba drzewa szablonów.

   Dziennik szablonów jest teraz wyświetlany w **pliku %LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (identyfikator wystąpienia odpowiada identyfikatorowi instalacji wystąpienia programu Visual Studio). Każde inicjowanie drzewa szablonu dołącza wpisy do tego dziennika.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otwórz program Visual Studio i uruchom okno **dialogowe Tworzenie nowego projektu** i **Nowy element,** aby zainicjować oba drzewa szablonów.

   Dziennik szablonów jest teraz wyświetlany w **pliku %LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (identyfikator wystąpienia odpowiada identyfikatorowi instalacji wystąpienia programu Visual Studio). Każde inicjowanie drzewa szablonu dołącza wpisy do tego dziennika.

::: moniker-end

Plik dziennika zawiera następujące kolumny:

- **Płyta FullPathToTemplate,** która ma następujące wartości:

  - 1 dla wdrażania opartego na manifeście

  - 0 dla wdrażania na dysku

- **Nazwa pliku szablonu**

- Inne właściwości szablonu

> [!NOTE]
> Aby wyłączyć rejestrowanie, usuń plik pkgdef lub zmień `EnableTemplateDiscoveryLog` `dword:00000000`wartość na `devenv /updateConfiguration` , a następnie uruchom ponownie.

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
