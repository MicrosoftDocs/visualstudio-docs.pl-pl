---
title: Docelowej platformy .NET
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cb7af190ac7fc5d4d5ce547029689f6c902a6e4f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747623"
---
# <a name="framework-targeting-overview"></a>Framework celem — omówienie

W programie Visual Studio można określić wersji platformy .NET, dla której projekt do obiektu docelowego. W przypadku aplikacji .NET Framework do uruchamiania na innym komputerze, na wersję, która celów aplikacji musi być zgodny z wersją framework, który jest zainstalowany na komputerze.

Aby uzyskać więcej informacji na temat platform docelowych, zobacz [ustalać platformy docelowe](/dotnet/standard/frameworks).

Można również utworzyć rozwiązanie, które zawiera projekty tego kierują do różnych wersji programu .NET. Adresowanie pomaga zagwarantować, że aplikacja używa tylko te funkcje, które są dostępne w wersji określonej struktury.

> [!TIP]
> Można również przeznaczać aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz [Wielowersyjność](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Framework przeznaczonych dla funkcji

Adresowanie obejmuje następujące funkcje:

- Po otwarciu projektu, który jest przeznaczony dla starszej wersji framework, programu Visual Studio może automatycznie zaktualizować projekt lub pozostaw element docelowy jako-to.

- Kiedy tworzysz projekt programu .NET Framework, można określić wersji programu .NET Framework, która ma pod kątem.

- Możesz [wielu platform docelowych](/dotnet/standard/frameworks#how-to-specify-target-frameworks) w jednym projekcie.

- Można wskazać inną wersję platformy .NET w każdym z kilku projektów w tym samym rozwiązaniu.

- Można zmienić wersję platformy .NET, która istniejący projektu elementów docelowych.

   Po zmianie wersji programu .NET, że projekt jest ukierunkowany, Visual Studio sprawia, że wszystkie wymagane zmiany dotyczące odwołań i plików konfiguracji.

Podczas pracy nad projektem, który jest przeznaczony dla starszej wersji framework, programu Visual Studio dynamicznie zmienia środowisko programistyczne, w następujący sposób:

- Filtruje elementy w **Dodaj nowy element** okno dialogowe **Dodaj nowe odwołanie** okno dialogowe i **Dodaj odwołanie do usługi** okno dialogowe, aby pominąć wybory, które nie są dostępne w Docelowa wersja.

- Filtruje niestandardowe formanty w **przybornika** Aby usunąć te, które nie są dostępne w wersji docelowej i pokazać tylko najbardziej aktualne formanty, gdy będzie dostępnych jest kilka formantów.

- Filtruje **IntelliSense** Aby pominąć funkcje językowe, które nie są dostępne w wersji docelowej.

- Filtruje właściwości w **właściwości** okna, aby pominąć te, które nie są dostępne w wersji docelowej.

- Filtruje opcje menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.

- W przypadku kompilacji wykorzystuje wersję kompilatora i opcje kompilatora, które są odpowiednie dla wersji docelowej.

> [!NOTE]
> - Adresowanie nie gwarantuje, że Twoja aplikacja będzie działać poprawnie. Należy przetestować aplikację w taki sposób, aby upewnić się, że jest uruchamiana w wersji docelowej.
> - Nie można wskazywać wersji struktury, poniżej .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Wybieranie wersji platformy docelowej

Kiedy tworzysz projekt programu .NET Framework, możesz wybrać docelową wersję platformy .NET, po wybraniu szablonu projektu. Lista dostępnych platform obejmuje wersje zainstalowanych framework, które mają zastosowanie do typu wybranego szablonu. Dla szablonów projektu — .NET Framework, na przykład szablony platformy .NET Core, **Framework** listy rozwijanej nie pojawia się.

::: moniker range="vs-2017"

![W ramach listy rozwijanej w programie VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menu rozwijanego platform w 2019 programu VS](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

W istniejącym projekcie można zmienić wersji docelowej platformy .NET w oknie dialogowym właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja programu .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Rozwiązać odwołania do zestawów systemu i użytkownika

Aby skierować je do określonej wersji oprogramowania .NET, należy najpierw zainstalować odpowiednie odwołania do zestawów. Możesz pobrać developer Pack dla różnych wersji programu .NET na [pobiera .NET](https://www.microsoft.com/net/download/windows) strony.

Dla projektów programu .NET Framework **Dodaj odwołanie** okno dialogowe wyłącza zestawy systemowe, które odnoszą się do .NET Framework w wersji docelowej, aby nie mogą zostać przypadkowo dodany do projektu. (Zestawy systemowe to *.dll* plików znajdujących się w wersji programu .NET Framework.) Odwołania, które należą do wersji szablonu, która jest wyższa niż wersja docelowa nie zostanie rozwiązany, a nie można dodać formanty, które są zależne od takiego odwołania. Jeśli chcesz włączyć takie odwołanie, zresetuj docelowego .NET Framework projektu na taki, który zawiera odwołanie. Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Aby uzyskać więcej informacji na temat odwołań do zestawów, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Włączenia zapytań LINQ

Jeśli platformą docelową jest program .NET Framework 3.5 lub nowszy, odniesienie do **System.Core** i importu poziomu projektu, aby uzyskać <xref:System.Linq> (tylko w Visual Basic) są automatycznie dodawane. Jeśli chcesz korzystać z funkcji LINQ, należy również włączyć `Option Infer` na (tylko w Visual Basic). Odwołanie i import są usuwane automatycznie, jeśli zmienisz element docelowy do wcześniejszej wersji systemu .NET Framework. Aby uzyskać więcej informacji, zobacz [pracować z LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Zobacz także

- [Platformy docelowe](/dotnet/standard/frameworks)
- [Wielowersyjność (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Instrukcje: Modyfikowanie docelowego framework i zestaw narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)