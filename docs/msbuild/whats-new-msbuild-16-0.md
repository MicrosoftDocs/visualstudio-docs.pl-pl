---
title: Co&#39;s Nowość w programie MSBuild 16.0 | Dokumentacja firmy Microsoft
ms.date: 03/11/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9fb23c8a48493056c9a37f510cefea3cc3374095
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57986990"
---
# <a name="whats-new-in-msbuild-160"></a>What's new in MSBuild 16.0

W tym artykule opisano funkcje zaktualizowane i właściwości w MSBuild 16.0. Aby uzyskać szczegółowe informacje o wersji dotyczące (tylko wersja robocza), zobacz [ MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest zainstalowany w *\Current* folder w każdej wersji programu Visual Studio. Na przykład *\Microsoft Visual Studio\Current\Enterprise\MSBuild C:\Program Files (x86)*. Można również użyć następujące modułu programu PowerShell, aby zlokalizować program MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Zmienionymi właściwościami

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` w przypadku tej wersji narzędzi jest "Current". Wersja zestawu jest taki sam jak w programie Visual Studio 2017, czyli 15.1.0.0.

- `VisualStudioVersion` w tej wersji narzędzi jest "16,0"

## <a name="updates"></a>Aktualizacje

Program MSBuild (i Visual Studio) jest teraz przeznaczony dla platformy .NET Framework 4.7.2. Jeśli chcesz używać nowych funkcji interfejsu API programu MSBuild, Twój zestaw również wymaga uaktualnienia, ale istniejący kod w dalszym ciągu będzie działać.

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
