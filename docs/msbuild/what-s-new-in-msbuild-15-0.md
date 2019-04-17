---
title: Co&#39;s Nowość w wersji programu MSBuild 15 | Dokumentacja firmy Microsoft
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 718ef14fda76df87dc4627dc518e993058896471
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2019
ms.locfileid: "59584301"
---
# <a name="whats-new-in-msbuild-15"></a>What's new in MSBuild 15

Program MSBuild jest teraz dostępny jako część [zestawu .NET Core SDK](https://www.microsoft.com/net/download/core) i tworzyć projektów .NET Core w Windows, macOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild został zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład *\Microsoft Visual Studio\2017\Enterprise\MSBuild C:\Program Files (x86)*. Można również użyć następujące modułu programu PowerShell, aby zlokalizować program MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Program MSBuild nie jest już zainstalowane w globalnej pamięci podręcznej zestawów. Aby programowo odwołują się do programu MSBuild, należy użyć pakietów NuGet. Aby uzyskać więcej informacji, zobacz [aktualizowanie istniejącej aplikacji dla programu MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Zmienionymi właściwościami

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` w przypadku tej wersji narzędzi jest 15.0. Wersja zestawu jest 15.1.0.0.

- `MSBuildToolsPath` nie ma już stałej lokalizacji. Domyślnie znajduje się w *MSBuild\15.0\Bin* folderu względem lokalizacji instalacji programu Visual Studio, ale lokalizacja instalacji programu Visual Studio można zmienić w czasie instalacji.

- `ToolsVersion` wartości nie są już ustawione w rejestrze.

- `SDK35ToolsPath` i `SDK40ToolsPath` właściwości wskaż .NET Framework SDK, który jest spakowany w tej wersji programu Visual Studio (na przykład 10.0A narzędzi 4.X).

## <a name="updates"></a>Aktualizacje
- [Project — element](../msbuild/project-element-msbuild.md) ma nową `SDK` atrybutu. Również `Xmlns` atrybutu jest teraz opcjonalny. Aby uzyskać więcej informacji na temat `SDK` atrybutów, zobacz [jak: Korzystanie z zestawów SDK projektu MSBuild](../msbuild/how-to-use-project-sdk.md), [pakiety, metapakiety i struktury](/dotnet/core/packages) i [ma zostać dodany do pliku csproj formatowania dla platformy .NET Core](/dotnet/core/tools/csproj).
- [Item — element](../msbuild/item-element-msbuild.md) poza cele ma nową `Update` atrybutu. Ponadto ograniczeń dotyczących `Remove` atrybut został wyeliminowany.
- *Directory.Build.props* jest plikiem zdefiniowanych przez użytkownika zawiera dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft.Common.props* chyba że właściwość `ImportDirectoryBuildTargets` ustawiono **false**. *Directory.Build.targets* zaimportowanych przez *Microsoft.Common.targets*.
- Wszystkie metadane o nazwie, który jest zgodny z bieżącą listę atrybutów opcjonalnie może być wyrażona jako atrybut. Aby uzyskać więcej informacji, zobacz [elementu](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash` dodaje znaku ukośnika na końcu ścieżki, jeśli jeszcze nie istnieje.
- `NormalizePath` łączy elementy ścieżki i gwarantuje, że ciąg wyjściowy ma znaki separatora katalogu poprawny w bieżącym systemie operacyjnym.
- `NormalizeDirectory` łączy elementy ścieżki, zapewnia znaku ukośnika na końcu i gwarantuje, że ciąg wyjściowy ma znaki separatora katalogu poprawny w bieżącym systemie operacyjnym.
- `GetPathOfFileAbove` zwraca ścieżkę do pliku bezpośrednio po tym. Jest funkcjonalnym odpowiednikiem wywołania `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
