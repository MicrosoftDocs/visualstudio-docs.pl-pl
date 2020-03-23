---
title: Co&#39;nowego w MSBuild 15 | Dokumenty firmy Microsoft
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 2503040e074a62422d4c7c904f5ad3a2bd84d6c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631032"
---
# <a name="whats-new-in-msbuild-15"></a>Co nowego w MSBuild 15

Program MSBuild jest teraz dostępny jako część [sdk .NET Core SDK](https://www.microsoft.com/net/download/core) i może tworzyć projekty .NET Core w systemach Windows, macOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 MsBuild jest teraz zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Do zlokalizowania programu MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)można również użyć następującego modułu programu PowerShell.

 MSBuild nie jest już zainstalowany w globalnej pamięci podręcznej zestawów. Aby odwołać się do programu MSBuild, należy użyć pakietów NuGet. Aby uzyskać więcej informacji, zobacz [Aktualizowanie istniejącej aplikacji dla MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion`dla tej wersji narzędzi jest 15.0. Wersja montażowa to 15.1.0.0.

- `MSBuildToolsPath`nie ma już stałej lokalizacji. Domyślnie znajduje się w folderze *MSBuild\15.0\Bin* względem lokalizacji instalacji programu Visual Studio, ale lokalizację instalacji programu Visual Studio można zmienić w czasie instalacji.

- `ToolsVersion`wartości nie są już ustawione w rejestrze.

- Właściwości `SDK35ToolsPath` `SDK40ToolsPath` i wskazują na zestaw SDK programu .NET Framework, który jest dostarczany z tą wersją programu Visual Studio (na przykład 10.0A dla narzędzi 4.X).

## <a name="updates"></a>Aktualizacje

- [Element projektu](../msbuild/project-element-msbuild.md) ma `SDK` nowy atrybut. Również `Xmlns` atrybut jest teraz opcjonalny. Aby uzyskać więcej `SDK` informacji na temat atrybutu, zobacz [Jak: Korzystanie z SDK projektu MSBuild](../msbuild/how-to-use-project-sdk.md), [Pakiety, metapakiety oraz struktury i](/dotnet/core/packages) [dodatki do formatu csproj dla .NET Core](/dotnet/core/tools/csproj).
- [Element elementu](../msbuild/item-element-msbuild.md) poza obiekty `Update` docelowe ma nowy atrybut. Ponadto wyeliminowano ograniczenie `Remove` atrybutu.
- *Directory.Build.props* to plik zdefiniowany przez użytkownika, który zapewnia dostosowania projektów w katalogu. Ten plik jest automatycznie importowany z *witryny Microsoft.Common.props,* chyba że właściwość `ImportDirectoryBuildTargets` jest ustawiona na **false**. *Directory.Build.targets* jest importowany przez *firmę Microsoft.Common.targets*.
- Wszelkie metadane o nazwie, która nie jest w konflikcie z bieżącą listą atrybutów, mogą być opcjonalnie wyrażone jako atrybut. Aby uzyskać więcej informacji, zobacz [Element towaru](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash`dodaje końcowe ukośnik do ścieżki, jeśli jeszcze nie istnieje.
- `NormalizePath`łączy elementy ścieżki i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `NormalizeDirectory`łączy elementy ścieżki, zapewnia końcowe ukośnik i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove`zwraca ścieżkę pliku bezpośrednio poprzedzającego ten. Jest to funkcjonalnie równoważne`<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
