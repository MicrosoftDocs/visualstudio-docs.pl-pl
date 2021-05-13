---
title: Co nowego w programie MSBuild 15 | Microsoft Docs
description: Zobacz zmienione, zaktualizowane i nowe funkcje programu MSBuild 15 dostępne dla programu zestaw .NET Core SDK i tworzenia projektów .NET Core w systemach Windows, macOS i Linux.
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
ms.openlocfilehash: e0fe78e781af4f2fafa52a230036bc20b657fd8e
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848269"
---
# <a name="whats-new-in-msbuild-15"></a>Co nowego w programie MSBuild 15

Program MSBuild jest teraz dostępny w ramach usługi [zestaw .NET Core SDK](https://www.microsoft.com/net/download/core) i może kompilować projekty .NET Core w systemach Windows, macOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest teraz instalowany w folderze w poszczególnych wersjach Visual Studio. Na przykład *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild.* Aby zlokalizować program MSBuild, możesz również użyć następującego modułu programu PowerShell: [vssetup.powershell.](https://github.com/Microsoft/vssetup.powershell)

 Program MSBuild nie jest już zainstalowany w globalnej pamięci podręcznej zestawów. Aby programowo odwoływać się do programu MSBuild, użyj pakietów NuGet. Aby uzyskać więcej informacji, zobacz [Aktualizowanie istniejącej aplikacji dla programu MSBuild 15.0.](../msbuild/updating-an-existing-application.md)

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` Dla tej wersji narzędzi jest to 15.0. Wersja zestawu to 15.1.0.0.

- `MSBuildToolsPath` nie ma już stałej lokalizacji. Domyślnie znajduje się on w folderze *MSBuild\15.0\Bin* względem lokalizacji instalacji programu Visual Studio, ale lokalizację instalacji Visual Studio można zmienić podczas instalacji.

- `ToolsVersion` Wartości nie są już ustawione w rejestrze.

- Właściwości i wskazują zestaw SDK .NET Framework, który jest spakowany z tą wersją pakietu Visual Studio (na przykład `SDK35ToolsPath` `SDK40ToolsPath` 10.0A dla narzędzi 4.X).

## <a name="updates"></a>Aktualizacje

- [Element Project](../msbuild/project-element-msbuild.md) ma nowy `SDK` atrybut. Ponadto `Xmlns` atrybut jest teraz opcjonalny. Aby uzyskać więcej informacji na temat atrybutu, zobacz How `SDK` [to: Use MSBuild project SDKs](../msbuild/how-to-use-project-sdk.md), [Packages, metapackages, and frameworks,](/dotnet/core/packages) and Additions to the [csproj format for .NET Core (Jak](/dotnet/core/tools/csproj)używać zestawów SDK projektu MSBuild, pakietów, metapakiet i platform) oraz Dodatki do formatu csproj dla programu .NET Core.
- [Element item](../msbuild/item-element-msbuild.md) poza elementami docelowymi ma nowy `Update` atrybut. Ponadto ograniczenie atrybutu `Remove` zostało wyeliminowane.
- *Directory.Build.props to* plik zdefiniowany przez użytkownika, który zapewnia dostosowania projektów w katalogu. Ten plik jest automatycznie importowany z *pliku Microsoft.Common.props,* chyba że właściwość `ImportDirectoryBuildTargets` jest ustawiona na wartość **false**. *Directory.Build.targets* jest importowany przez *microsoft.common.targets.*
- Wszelkie metadane o nazwie, która nie jest w konflikcie z bieżącą listą atrybutów, można opcjonalnie wyrazić jako atrybut. Aby uzyskać więcej informacji, zobacz [Item, element](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash` Dodaje ukośnik na końcowej ścieżce, jeśli jeszcze nie istnieje.
- `NormalizePath` łączy elementy ścieżki i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `NormalizeDirectory` Łączy elementy ścieżki, zapewnia końcowe ukośnik i zapewnia, że ciąg wyjściowy ma poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove` Funkcja zwraca ścieżkę pliku bezpośrednio poprzedzającego ten plik. Jest funkcjonalnie odpowiednikiem wywołania `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
