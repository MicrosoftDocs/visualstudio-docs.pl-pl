---
title: Przegląd wielowersyjności kodu w programie MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 543fde0c09d97d0001210c401fdc4cf81f48a698
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800383"
---
# <a name="msbuild-multitargeting-overview"></a>Przegląd wielowersyjności kodu w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Korzystając z programu MSBuild, można kompilować aplikację do uruchamiania na jednym z kilku różnych wersji programu .NET Framework i na jednym z różnych platform system. Na przykład można kompilować aplikację do uruchamiania na .NET Framework 2.0 na platformie 32-bitowej i kompilacji tej samej aplikacji do uruchamiania na .NET Framework 4.5 na platformie 64-bitowej.  
  
> [!IMPORTANT]
>  Niezależnie od nazwy "wielowersyjność" projektu mogą określać docelową framework tylko jeden i tylko w jednej platformie w danym momencie.  
  
 Oto niektóre funkcje przeznaczone dla programu MSBuild:  
  
-   Można opracować aplikację, która jest przeznaczony dla starszej wersji programu .NET Framework, na przykład wersji 2.0, 3.5 i 4.  
  
-   Można wskazać framework innych niż .NET Framework, na przykład Silverlight Framework.  
  
-   Możesz wybrać docelową *profil framework*, czyli uprzednio zdefiniowany podzbiór platformy docelowej.  
  
-   Jeśli z dodatkiem Service pack dla bieżącej wersji programu .NET Framework jest zwalniana, można go wykorzystać.  
  
-   Przeznaczone dla programu MSBuild gwarantuje, że aplikacja używa tylko funkcjonalności, która jest dostępna w docelowej platformy framework i platformy.  
  
## <a name="target-framework-and-platform"></a>Platforma  
 A *platformę docelową* jest wersją .NET Framework, projekt został opracowany pod kątem uruchamiania na i *platformę docelową* czy projekt jest kompilowany do uruchamiania na Platforma systemu.  Na przykład możesz chcieć aplikacji .NET Framework 2.0, do uruchamiania na 32-bitowej platformie, która jest zgodna z rodziny procesorów 802 x 86 (x86) docelowej. Kombinacja wartości docelowej i platforma docelowa jest znany jako *kontekstu docelowej*. Aby uzyskać więcej informacji, zobacz [platformy docelowej i platformy docelowej](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Zestaw narzędzi (ToolsVersion)  
 Zestaw narzędzi umożliwia zbieranie informacji o razem narzędzia, zadania i elementy docelowe, które są używane do tworzenia aplikacji. Zestaw narzędzi obejmuje kompilatory, takie jak csc.exe i vbc.exe, wspólnego pliku docelowego (microsoft.common.targets) i typowe zadania dotyczące plików (microsoft.common.tasks). 4.5 narzędzi może służyć do docelowej wersji systemu .NET Framework 2.0, 3.0, 3.5, 4 i 4.5. Jednak 2.0 zestawu narzędzi można używać tylko pod kątem programu .NET Framework w wersji 2.0. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Zestawy referencyjne  
 Zestawy odwołań, które są określone w zestawie narzędzi ułatwiają projektowanie i tworzenie aplikacji. Te zestawy odwołań nie tylko włączyć kompilacji określonego celu, ale również ograniczyć składniki i funkcje w środowisku IDE programu Visual Studio do tych, które są zgodne z obiektem docelowym. Aby uzyskać więcej informacji, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md)  
  
## <a name="configuring-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań  
 Można skonfigurować elementów docelowych MSBuild oraz zadań do wykonania poza procesem za pomocą narzędzia MSBuild, dzięki czemu możliwe jest określanie kontekstach, które różnią się znacznie od jednego są uruchomione na.  Na przykład mogą kierować aplikacją 32-bitowy, .NET Framework 2.0 jest uruchomiona na komputerze deweloperskim na platformie 64-bitowym z .NET Framework 4.5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Mogą wystąpić błędy, jeśli zostanie podjęta próba odwołanie do zestawu, który nie jest częścią kontekstu docelowego. Aby uzyskać więcej informacji dotyczących tych błędów i co należy zrobić o nich, zobacz [Rozwiązywanie problemów z celem błędy programu .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
