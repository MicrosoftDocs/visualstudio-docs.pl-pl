---
title: Co&#39;s Nowy w MSBuild 16.0 | Dokumenty firmy Microsoft
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652810"
---
# <a name="whats-new-in-msbuild-160"></a>Co nowego w MSBuild 16.0

W tym artykule opisano zaktualizowane funkcje i właściwości w msbuild 16.0. Szczegółowe informacje o wersji zobacz [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Zmieniona ścieżka

 MSBuild jest zainstalowany w folderze *\Current* w każdej wersji programu Visual Studio, a pliki wykonywalne znajdują się w podfolderze *\Bin.* Na przykład ścieżką do *pliku MSBuild.exe zainstalowanego* w programie Visual Studio 2019 Community jest *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* Można również użyć następującego modułu programu PowerShell do zlokalizowania programu MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion`dla tej wersji narzędzi jest "Prąd". Wersja zestawu jest taka sama jak w programie Visual Studio 2017, który jest 15.1.0.0.

- `VisualStudioVersion`dla tej wersji narzędzi jest "16.0"

## <a name="updates"></a>Aktualizacje

Program MSBuild (i Visual Studio) jest teraz przeznaczony dla platformy .NET Framework 4.7.2. Jeśli chcesz używać nowych funkcji interfejsu API programu MSBuild, Twój zestaw również wymaga uaktualnienia, ale istniejący kod w dalszym ciągu będzie działać.

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
