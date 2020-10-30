---
title: Omówienie funkcji wieloadresowych programu MSBuild | Microsoft Docs
description: Dowiedz się, jak używać programu MSBuild do kompilowania aplikacji do uruchamiania w jednej z kilku wersji .NET Framework oraz na jednej z kilku platform systemowych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b4ba2c27e130580af961216739289c6c7e9585
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046304"
---
# <a name="msbuild-multitargeting-overview"></a>Przegląd wielowersyjności kodu w programie MSBuild

Za pomocą programu MSBuild można skompilować aplikację do uruchamiania w jednej z kilku wersji .NET Framework i na jednej z kilku platform systemowych. Na przykład można skompilować aplikację do uruchamiania na .NET Framework 2,0 na platformie 32-bitowej i skompilować tę samą aplikację do uruchamiania na .NET Framework 4,5 na platformie 64-bitowej.

> [!IMPORTANT]
> Pomimo nazwy "wiele obiektów docelowych" projekt może wskazywać tylko jedną strukturę i tylko jedną platformę naraz.

 Oto niektóre z funkcji docelowych programu MSBuild:

- Można opracować aplikację, która jest przeznaczona dla starszej wersji .NET Framework, na przykład w wersji 2,0, 3,5 lub 4.

- Można wskazać platformę inną niż .NET Framework, na przykład platformę Silverlight.

- Można wskazać *Profil platformy* , który jest wstępnie zdefiniowanym podzbiorem platformy docelowej.

- Jeśli dodatek Service Pack dla bieżącej wersji .NET Framework jest wydawany, można go wskazać.

- Program MSBuild określa gwarancję, że aplikacja używa tylko funkcji dostępnych w docelowej architekturze i platformie.

## <a name="target-framework-and-platform"></a>Struktura docelowa i platforma

 Platforma *docelowa* to wersja .NET Framework, do której projekt został skompilowany, a *platforma docelowa* to platforma systemowa, na której jest zbudowany projekt.  Na przykład możesz chcieć użyć aplikacji .NET Framework 2,0 na platformie 32-bitowej, która jest zgodna z rodziną procesorów 80x86 (x86). Kombinacja struktury docelowej i platformy docelowej jest znana jako *kontekst docelowy* . Aby uzyskać więcej informacji, zobacz [Target Framework i Target platform](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Zestaw narzędzi (ToolsVersion)

 Zestaw narzędzi zbiera narzędzia, zadania i elementy docelowe, które są używane do tworzenia aplikacji. Zestaw narzędzi zawiera kompilatory, takie jak *csc.exe* i *vbc.exe* , plik wspólnych obiektów docelowych ( *Microsoft. Common. targets* ) i plik wspólnych zadań ( *Microsoft. Common. Tasks* ). Zestaw narzędzi 4,5 może służyć do kierowania .NET Framework wersjami 2,0, 3,0, 3,5, 4 i 4,5. Jednak zestaw narzędzi 2,0 może być używany tylko do .NET Framework wersji 2,0. Aby uzyskać więcej informacji, zobacz zestaw [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Odwoływanie się do zestawów

 Zestawy odwołań, które są określone w zestawie narzędzi, ułatwiają projektowanie i kompilowanie aplikacji. Te zestawy referencyjne nie tylko włączają konkretną kompilację docelową, ale również ograniczają składniki i funkcje w środowisku IDE programu Visual Studio do tych, które są zgodne z elementem docelowym. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań

 Można skonfigurować elementy docelowe i zadania programu MSBuild do uruchamiania poza procesem przy użyciu programu MSBuild, aby można było używać kontekstów, które są znacznie inne niż te, które są używane.  Można na przykład określić 32-bitową .NET Framework 2,0 aplikacji, gdy komputer deweloperski działa na platformie 64-bitowej z .NET Framework 4,5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie elementów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

 Jeśli próbujesz odwołać się do zestawu, który nie jest częścią kontekstu docelowego, mogą wystąpić błędy. Aby uzyskać więcej informacji o tych błędach i o tym, co należy zrobić, zobacz [Rozwiązywanie problemów .NET Framework określania błędów](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
