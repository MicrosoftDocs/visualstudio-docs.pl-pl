---
title: Co &apos; nowego w programie MSBuild 16,0 | Microsoft Docs
description: Dowiedz się więcej na temat zmienionych i zaktualizowanych funkcji oraz właściwości programu MSBuild 16,0 i Utwórz link do informacji o wersji.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 24b106442456f8bfbd415c4559cba71e463418d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933794"
---
# <a name="whats-new-in-msbuild-160"></a>Co nowego w programie MSBuild 16.0

W tym artykule opisano zaktualizowane funkcje i właściwości w programie MSBuild 16,0. Aby uzyskać szczegółowe informacje o wersji, zobacz [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest zainstalowany w folderze *\Current* w każdej wersji programu Visual Studio, a pliki wykonywalne znajdują się w podfolderze *\Bin* . Na przykład ścieżka do *MSBuild.exe* zainstalowana z programem visual Studio 2019 Community to *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* można również użyć następującego modułu programu PowerShell do zlokalizowania programu MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` dla tej wersji narzędzi jest "Current". Wersja zestawu jest taka sama jak w programie Visual Studio 2017, który jest 15.1.0.0.

- `VisualStudioVersion` dla tej wersji narzędzi jest "16,0"

## <a name="change-waves"></a>Fale zmian

Począwszy od programu MSBuild 16,8, można wybiórczo wybrać, czy zrezygnować z pewnych potencjalnych zmian w programie MSBuild. Zobacz [zmiana fal](change-waves.md).

## <a name="updates"></a>Aktualizacje

Program MSBuild (i Visual Studio) jest teraz przeznaczony dla platformy .NET Framework 4.7.2. Jeśli chcesz używać nowych funkcji interfejsu API programu MSBuild, Twój zestaw również wymaga uaktualnienia, ale istniejący kod w dalszym ciągu będzie działać.

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
