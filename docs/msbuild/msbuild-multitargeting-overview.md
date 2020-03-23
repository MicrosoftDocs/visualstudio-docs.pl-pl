---
title: Przegląd multitargetingu MSBuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af7649a75fbf3ded0cf5d09e9063b49f4fcab1b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633333"
---
# <a name="msbuild-multitargeting-overview"></a>Omówienie multitargetingu MSBuild

Za pomocą MSBuild, można skompilować aplikację do uruchomienia na jednej z kilku wersji programu .NET Framework i na dowolnej z kilku platform systemowych. Na przykład można skompilować aplikację do uruchomienia na platformie .NET Framework 2.0 na platformie 32-bitowej i skompilować tę samą aplikację do uruchomienia na platformie .NET Framework 4.5 na platformie 64-bitowej.

> [!IMPORTANT]
> Pomimo nazwy "multitargeting", projekt może być skierowany tylko do jednej struktury i tylko jednej platformy naraz.

 Oto niektóre z funkcji kierowania MSBuild:

- Można opracować aplikację, która jest przeznaczona dla wcześniejszej wersji programu .NET Framework, na przykład wersje 2.0, 3.5 lub 4.

- Można kierować na platformę inną niż .NET Framework, na przykład Silverlight Framework.

- Można kierować *profil struktury*, który jest wstępnie zdefiniowany podzbiór struktury docelowej.

- Jeśli dodatek Service Pack dla bieżącej wersji programu .NET Framework zostanie wydany, można go kierować.

- MSBuild targeting gwarantuje, że aplikacja używa tylko funkcje, które są dostępne w ramach docelowej i platformy.

## <a name="target-framework-and-platform"></a>Docelowa struktura i platforma

 *Struktura docelowa* jest wersją programu .NET Framework, na których projekt jest zbudowany do uruchomienia, a *platforma docelowa* jest platformą systemową, na którą projekt jest zbudowany do uruchomienia.  Na przykład można kierować aplikację .NET Framework 2.0 do uruchomienia na platformie 32-bitowej, która jest zgodna z rodziną procesorów 802x86 (x86). Połączenie struktury docelowej i platformy docelowej jest znane jako *kontekst docelowy.* Aby uzyskać więcej informacji, zobacz [Platforma docelowa i platforma docelowa](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Zestaw narzędzi (ToolsVersion)

 Zestaw narzędzi zbiera razem narzędzia, zadania i obiekty docelowe, które są używane do tworzenia aplikacji. Zestaw narzędzi zawiera kompilatory, takie jak *csc.exe* i *vbc.exe*, wspólny plik docelowy (*microsoft.common.targets*) i typowy plik zadań (*microsoft.common.tasks*). Zestaw narzędzi 4.5 może służyć do kierowania .NET Framework wersje 2.0, 3.0, 3.5, 4 i 4.5. Jednak zestaw narzędzi 2.0 może służyć tylko do kierowania na .NET Framework w wersji 2.0. Aby uzyskać więcej informacji, zobacz [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Odwoływanie się do zestawów

 Zestawy odwołań, które są określone w Toolset pomóc w projektowaniu i tworzeniu aplikacji. Te zestawy odwołań nie tylko włączyć kompilacji określonego obiektu docelowego, ale także ograniczyć składniki i funkcje w programie Visual Studio IDE do tych, które są zgodne z obiektu docelowego. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z złożeniami w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań

 Można skonfigurować obiekty docelowe i zadania MSBuild do uruchamiania poza procesem za pomocą usługi MSBuild, dzięki czemu można kierować konteksty, które znacznie różnią się od tego, na których jest uruchomiona.  Na przykład można kierować 32-bitową aplikację .NET Framework 2.0, gdy komputer deweloperski jest uruchomiony na platformie 64-bitowej z programem .NET Framework 4.5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

 Mogą wystąpić błędy, jeśli spróbujesz odwołać się do zestawu, który nie jest częścią kontekstu docelowego. Aby uzyskać więcej informacji na temat tych błędów i co z nimi zrobić, zobacz [Rozwiązywanie problemów z błędami kierowania programu .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
