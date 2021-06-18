---
title: Wersja Visual Studio 2019 podczas tworzenia rozszerzenia w programie Visual Studio 2022 (wersja zapoznawcza)
description: Dowiedz się, jak sprawić, aby rozszerzenie Visual Studio działało z programem Visual Studio 2019, jeśli tworzysz projekt przy użyciu programu Visual Studio 2022 (wersja zapoznawcza).
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308821"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Kierowanie poprzedniej wersji podczas tworzenia rozszerzenia w programie Visual Studio 2022 (wersja zapoznawcza)

[!INCLUDE [preview-note](../includes/preview-note.md)]

Podczas tworzenia nowego projektu VSIX przy użyciu programu Visual Studio 2022 (wersja zapoznawcza) projekt jest tworzony na podstawie szablonu, który jest przeznaczony Visual Studio 2022 r. Jeśli chcesz wybrać wersję docelową Visual Studio 2019 lub wcześniejszą, musisz zmodyfikować utworzony projekt.

Rozważ użycie [udostępnionych projektów](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) do Visual Studio 2019 i Visual Studio 2022, jednocześnie udostępniając większość lub cały kod w rozszerzeniu.

Wykonaj następujące kroki w projekcie VSIX, który powinien być Visual Studio 2019 r.:

1. Edytuj plik `source.extension.vsixmanifest` , aby usunąć element i zakres `ProductArchitecture` wersji:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Zaktualizuj również wymagania wstępne:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Przejrzyj plik, aby uzyskać informacje o innych aktualizacjach, które mogą być konieczne.

1. Zmień wersje pakietów zestawu VS SDK, do których odwołujesz się w pliku projektu:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
