---
title: Rozwiązywanie problemów z odnajdywania szablonów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e84ff96381fb29a1728ad43df4ff558abd17243
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689841"
---
# <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu

Jeśli napotkasz problemy z wdrażania szablonów projektu lub elementu, można włączyć rejestrowanie diagnostyczne.

1. Utwórz plik pkgdef w folderze Common7\IDE\CommonExtensions instalacji (np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) z następującą zawartością:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Otwórz "wiersz polecenia dla deweloperów" dla instalacji przez wyszukiwanie w Windows search, a następnie uruchom `devenv /updateConfiguration`.

1. Uruchom program Visual Studio i uruchamiaj oknach dialogowych nowy projekt i nowy element, aby zainicjować obu drzewach szablonu. Pojawia się w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid odpowiada identyfikator instalacji wystąpienia programu Visual Studio). Każdy szablon drzewa inicjowania dołącza wpisy w tym dzienniku.

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