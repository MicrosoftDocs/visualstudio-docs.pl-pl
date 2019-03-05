---
title: Rozwiązywanie problemów z odnajdywania szablonów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324003"
---
# <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu

Jeśli napotkasz problemy z wdrażania szablonów projektu lub elementu, można włączyć rejestrowanie diagnostyczne.

::: moniker range="vs-2017"

1. Tworzenie pliku pkgdef *Common7\IDE\CommonExtensions* folderze instalacji. Na przykład *\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef C:\Program Files (x86)*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Tworzenie pliku pkgdef *Common7\IDE\CommonExtensions* folderze instalacji. Na przykład *\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef C:\Program Files (x86)*.

::: moniker-end

2. Dodaj następujący element do pliku pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Otwórz [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) instalacji i uruchomienia `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Uruchom program Visual Studio i uruchamiaj oknach dialogowych nowy projekt i nowy element, aby zainicjować obu drzewach szablonu.

   Pojawia się w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid odpowiada identyfikator instalacji wystąpienia programu Visual Studio). Każdy szablon drzewa inicjowania dołącza wpisy w tym dzienniku.

::: moniker-end

::: moniker range=">=vs-2019"

4. Uruchom program Visual Studio i uruchamiaj oknach dialogowych nowy projekt i nowy element, aby zainicjować obu drzewach szablonu.

   Pojawia się w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid odpowiada identyfikator instalacji wystąpienia programu Visual Studio). Każdy szablon drzewa inicjowania dołącza wpisy w tym dzienniku.

::: moniker-end

Plik dziennika zawiera następujące kolumny:

- **FullPathToTemplate**, która zawiera następujące wartości:

    - 1 w przypadku wdrażania w manifeście

    - 0 w przypadku wdrożenia na dysku

- **TemplateFileName**

- Inne właściwości szablonu

> [!NOTE]
> Aby wyłączyć rejestrowanie, usuń plik pkgdef lub zmień wartość właściwości `EnableTemplateDiscoveryLog` do `dword:00000000`, a następnie uruchom `devenv /updateConfiguration` ponownie.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)