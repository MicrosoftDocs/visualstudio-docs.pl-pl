---
title: Co&#39;nowego w programie MSBuild 16,0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3e6ecfc1c08f30eb0232f230d955967d95bc32ee
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566972"
---
# <a name="whats-new-in-msbuild-160"></a>Co nowego w programie MSBuild 16,0

W tym artykule opisano zaktualizowane funkcje i właściwości w programie MSBuild 16,0. Aby uzyskać szczegółowe informacje o wersji (tylko wersja robocza), zobacz [MSBuild 16,0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild jest zainstalowany w folderze *\Current* w każdej wersji programu Visual Studio. Na przykład *C:\Program Files (x86) \Microsoft Visual Studio\Current\Enterprise\MSBuild*. Możesz również użyć następującego modułu programu PowerShell, aby zlokalizować program MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Zmienione właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` tej wersji narzędzi to "Current". Wersja zestawu jest taka sama jak w programie Visual Studio 2017, który jest 15.1.0.0.

- `VisualStudioVersion` tej wersji narzędzi to "16,0"

## <a name="updates"></a>Aktualizacje

Program MSBuild (i Visual Studio) jest teraz przeznaczony dla platformy .NET Framework 4.7.2. Jeśli chcesz używać nowych funkcji interfejsu API programu MSBuild, Twój zestaw również wymaga uaktualnienia, ale istniejący kod w dalszym ciągu będzie działać.

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
