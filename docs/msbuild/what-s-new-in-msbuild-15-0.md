---
title: Co &apos; nowego w programie MSBuild 15 | Microsoft Docs
description: Zobacz zmienione, zaktualizowane i nowe funkcje programu MSBuild 15 dostępne dla zestaw .NET Core SDK i do kompilowania projektów .NET Core w systemach Windows, macOS i Linux.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: a7bbf46a1677a31726bdd7f2749f5ef3006e34f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933846"
---
# <a name="whats-new-in-msbuild-15"></a>Co nowego w programie MSBuild 15

Program MSBuild jest teraz dostępny jako część [zestaw .NET Core SDK](https://www.microsoft.com/net/download/core) i może tworzyć projekty platformy .NET Core w systemach Windows, MacOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest teraz zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. Możesz również użyć następującego modułu programu PowerShell, aby zlokalizować program MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

 Program MSBuild nie jest już zainstalowany w globalnej pamięci podręcznej zestawów. Aby programowo odwoływać się do programu MSBuild, użyj pakietów NuGet. Aby uzyskać więcej informacji, zobacz [Aktualizowanie istniejącej aplikacji dla programu MSBuild 15,0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` dla tej wersji narzędzi jest 15,0. Wersja zestawu to 15.1.0.0.

- `MSBuildToolsPath` nie ma już stałej lokalizacji. Domyślnie znajduje się on w folderze *MSBuild\15.0\bin* względem lokalizacji instalacji programu Visual Studio, ale lokalizację instalacji programu Visual Studio można zmienić w czasie instalacji.

- `ToolsVersion` wartości nie są już ustawione w rejestrze.

- `SDK35ToolsPath`Właściwości i `SDK40ToolsPath` wskazują zestawowi .NET Framework SDK, który jest spakowany z tą wersją programu Visual Studio (na przykład 10.0 a dla narzędzi 4. X).

## <a name="updates"></a>Aktualizacje

- [Element projektu](../msbuild/project-element-msbuild.md) ma nowy `SDK` atrybut. Ponadto `Xmlns` atrybut jest teraz opcjonalny. Aby uzyskać więcej informacji na temat `SDK` atrybutu, zobacz [How to: use Project SDK](../msbuild/how-to-use-project-sdk.md), [Packages, webpackages i platforms](/dotnet/core/packages) i [Dodatki do formatu csproj dla platformy .NET Core](/dotnet/core/tools/csproj).
- [Element Item](../msbuild/item-element-msbuild.md) poza elementami docelowymi ma nowy `Update` atrybut. Ponadto ograniczenie dla `Remove` atrybutu zostało wyeliminowane.
- *Directory. Build. props* to plik zdefiniowany przez użytkownika, który udostępnia dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft. Common. props* , chyba że właściwość `ImportDirectoryBuildTargets` ma wartość **false**. *Katalog. Build. targets* został zaimportowany przez element *Microsoft. Common. targets*.
- Wszystkie metadane o nazwie, która nie powoduje konfliktu z bieżącą listą atrybutów, mogą być opcjonalnie wyrażone jako atrybut. Aby uzyskać więcej informacji, zobacz element [Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash` dodaje końcowy ukośnik do ścieżki, jeśli jeszcze nie istnieje.
- `NormalizePath` łączy elementy ścieżki i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `NormalizeDirectory` łączy elementy ścieżki, zapewnia końcowy ukośnik i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove` zwraca ścieżkę pliku bezpośrednio poprzedzającego ten plik. Jest on funkcjonalnie równoważny z wywołaniem `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
