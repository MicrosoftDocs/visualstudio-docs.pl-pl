---
title: Co nowego w programie MSBuild 16.0 | Microsoft Docs
description: Dowiedz się więcej o zmienionych i zaktualizowanych funkcjach i właściwościach programu MSBuild 16.0 oraz linki do informacji o wersji.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848256"
---
# <a name="whats-new-in-msbuild-160"></a>Co nowego w programie MSBuild 16.0

W tym artykule opisano zaktualizowane funkcje i właściwości w programie MSBuild 16.0. Aby uzyskać szczegółowe informacje o wersji, [zobacz MSBuild 16.0.](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest instalowany w *folderze \Current* w każdej wersji Visual Studio, a pliki wykonywalne znajdują się w podfolderze *\Bin.* Na przykład ścieżka do programu *MSBuild.exe* zainstalowanego z programem Visual Studio 2019 Community to *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* Aby zlokalizować program MSBuild, można również użyć następującego modułu programu PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` Dla tej wersji narzędzi jest to "Current". Wersja zestawu jest taka sama jak w Visual Studio 2017, czyli 15.1.0.0.

- `VisualStudioVersion` Dla tej wersji narzędzi jest to "16.0"

## <a name="change-waves"></a>Fale zmian

Począwszy od programu MSBuild 16.8, można selektywnie wybrać, czy zrezygnować z niektórych potencjalnie zakłócających zmian w programie MSBuild. Zobacz [Zmienianie fal](change-waves.md).

## <a name="updates"></a>Aktualizacje

Program MSBuild (i Visual Studio) jest teraz przeznaczony dla platformy .NET Framework 4.7.2. Jeśli chcesz używać nowych funkcji interfejsu API programu MSBuild, Twój zestaw również wymaga uaktualnienia, ale istniejący kod w dalszym ciągu będzie działać.

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
