---
title: Co&#39;nowego w programie MSBuild 15 | Microsoft Docs
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 49e248ee0e5537ae54957695ca698b041fc1ce8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567283"
---
# <a name="whats-new-in-msbuild-15"></a>Co nowego w programie MSBuild 15

Program MSBuild jest teraz dostępny jako część [zestaw .NET Core SDK](https://www.microsoft.com/net/download/core) i może tworzyć projekty platformy .NET Core w systemach Windows, MacOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest teraz zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. Możesz również użyć następującego modułu programu PowerShell, aby zlokalizować program MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

 Program MSBuild nie jest już zainstalowany w globalnej pamięci podręcznej zestawów. Aby programowo odwoływać się do programu MSBuild, użyj pakietów NuGet. Aby uzyskać więcej informacji, zobacz [Aktualizowanie istniejącej aplikacji dla programu MSBuild 15,0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` tej wersji narzędzi to 15,0. Wersja zestawu to 15.1.0.0.

- `MSBuildToolsPath` nie ma już stałej lokalizacji. Domyślnie znajduje się on w folderze *MSBuild\15.0\bin* względem lokalizacji instalacji programu Visual Studio, ale lokalizację instalacji programu Visual Studio można zmienić w czasie instalacji.

- wartości `ToolsVersion` nie są już ustawione w rejestrze.

- Właściwości `SDK35ToolsPath` i `SDK40ToolsPath` wskazują zestaw .NET Framework SDK, który jest opakowany z tą wersją programu Visual Studio (na przykład 10.0 A dla narzędzi 4. X).

## <a name="updates"></a>Aktualizacje
- [Element projektu](../msbuild/project-element-msbuild.md) ma nowy atrybut `SDK`. Ponadto atrybut `Xmlns` jest teraz opcjonalny. Aby uzyskać więcej informacji o atrybucie `SDK`, zobacz [How to: use Project SDK](../msbuild/how-to-use-project-sdk.md), [Packages, webpackages i platforms](/dotnet/core/packages) i [Dodatki do formatu csproj dla platformy .NET Core](/dotnet/core/tools/csproj).
- [Element Item](../msbuild/item-element-msbuild.md) poza elementami docelowymi ma nowy atrybut `Update`. Ponadto ograniczenie `Remove` atrybutu zostało wyeliminowane.
- *Directory. Build. props* to plik zdefiniowany przez użytkownika, który udostępnia dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft. Common. props* , chyba że właściwość `ImportDirectoryBuildTargets` jest ustawiona na **false**. *Katalog. Build. targets* został zaimportowany przez element *Microsoft. Common. targets*.
- Wszystkie metadane o nazwie, która nie powoduje konfliktu z bieżącą listą atrybutów, mogą być opcjonalnie wyrażone jako atrybut. Aby uzyskać więcej informacji, zobacz element [Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash` dodaje końcowy ukośnik do ścieżki, jeśli jeszcze nie istnieje.
- `NormalizePath` łączy elementy ścieżki i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogów dla bieżącego systemu operacyjnego.
- `NormalizeDirectory` łączy elementy ścieżki, zapewnia końcowy ukośnik i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogów dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove` zwraca ścieżkę pliku bezpośrednio poprzedzającego ten plik. Jest funkcjonalnym odpowiednikiem wywołania `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
