---
title: Rozwiązywanie problemów z odnajdywania szablonów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1ea74d3c5f3fed961a956e9a55a4930d009d530
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790228"
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

4. Otwórz program Visual Studio, a następnie uruchom okna dialogowego Nowy projekt i nowy element do zainicjowania obu drzewach szablonu.

   Pojawia się w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid odpowiada identyfikator instalacji wystąpienia programu Visual Studio). Każdy szablon drzewa inicjowania dołącza wpisy w tym dzienniku.

::: moniker-end

::: moniker range=">=vs-2019"

4. Otwórz program Visual Studio, a następnie uruchom **Utwórz nowy projekt** i **nowy element** oknach dialogowych, aby zainicjować obu drzewach szablonu.

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