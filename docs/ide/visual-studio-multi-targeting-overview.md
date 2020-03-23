---
title: Ukierunkowane struktury platformy .NET
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec81b38ab68c327f25c9f94b6329a700e2662383
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303422"
---
# <a name="framework-targeting-overview"></a>Omówienie kierowania na ramy

W programie Visual Studio można określić wersję platformy .NET, która ma być kierowana do projektu. Określanie wartości docelowych platformy pomaga zagwarantować, że aplikacja używa tylko funkcje, które są dostępne w określonej wersji framework. Dla aplikacji .NET Framework do uruchomienia na innym komputerze, wersja struktury, że obiekty docelowe aplikacji musi być zgodna z wersją struktury, która jest zainstalowana na komputerze.

Rozwiązanie programu Visual Studio może zawierać projekty przeznaczone dla różnych wersji platformy .NET.

Aby uzyskać więcej informacji na temat struktur docelowych, zobacz [struktury docelowe](/dotnet/standard/frameworks).

> [!TIP]
> Można również kierować aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funkcje kierowania na ramy

Kierowanie na ramy ma na celu:

- Po otwarciu projektu, który jest przeznaczony dla wcześniejszej wersji struktury, Visual Studio można automatycznie uaktualnić projekt lub pozostawić obiekt docelowy, jak jest.

- Podczas tworzenia projektu .NET Framework można określić wersję programu .NET Framework, który ma być skierowany na obiekt.

- Można [kierować wiele struktur](/dotnet/standard/frameworks#how-to-specify-target-frameworks) w jednym projekcie.

- Można kierować inną wersję platformy .NET w każdym z kilku projektów w tym samym rozwiązaniu.

- Można zmienić wersję platformy .NET, która jest docelowa dla istniejącego projektu.

   Po zmianie wersji platformy .NET, która jest przeznaczona dla projektu, program Visual Studio wprowadza wszelkie wymagane zmiany w odwołaniach i plikach konfiguracyjnych.

Podczas pracy nad projektem, który jest przeznaczony dla wcześniejszej wersji struktury, Visual Studio dynamicznie zmienia środowisko programistyczne, w następujący sposób:

- Filtruje elementy w oknie dialogowym **Dodawanie nowego elementu,** oknie dialogowym **Dodawanie nowego odwołania** i oknie dialogowym Dodawanie odwołania do **usługi,** aby pominąć opcje, które nie są dostępne w wersji docelowej.

- Filtruje niestandardowe formanty w **przyborniku,** aby usunąć te, które nie są dostępne w wersji docelowej i wyświetlić tylko najbardziej aktualne formanty, gdy dostępnych jest wiele formantów.

- Filtruje **intellisense,** aby pominąć funkcje języka, które nie są dostępne w wersji docelowej.

- Filtruje właściwości w oknie **Właściwości,** aby pominąć te, które nie są dostępne w wersji docelowej.

- Filtruje opcje menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.

- W przypadku kompilacji używa wersji kompilatora i opcji kompilatora, które są odpowiednie dla wersji docelowej.

> [!NOTE]
> - Kierowanie na platformę nie gwarantuje, że aplikacja będzie działać poprawnie. Należy przetestować aplikację, aby upewnić się, że działa w stosunku do wersji docelowej.
> - Nie można kierować wersji struktury poniżej .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Wybieranie docelowej wersji struktury

Podczas tworzenia projektu .NET Framework można wybrać docelową wersję programu .NET Framework po wybraniu szablonu projektu. Lista dostępnych struktur zawiera zainstalowane wersje struktury, które mają zastosowanie do wybranego typu szablonu. W przypadku szablonów projektów non-.NET Framework, na przykład szablonów .NET Core, lista rozwijana **Framework** nie jest wyświetlana.

::: moniker range="vs-2017"

![Rozwijanie ram w vs 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Rozwijanie ram w vs 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Zmienianie struktury docelowej

W istniejącym projekcie języka Visual Basic, C#lub F# należy zmienić docelową wersję platformy .NET w oknie dialogowym właściwości projektu. Aby uzyskać informacje na temat jak zmienić wersję docelową dla projektów Języka C++, zobacz [Jak zmodyfikować platformę docelową i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) zamiast tego.

1. W **Eksploratorze rozwiązań**otwórz menu po kliknięciu prawym przyciskiem myszy dla projektu, który chcesz zmienić, a następnie wybierz polecenie **Właściwości**.

1. W lewej kolumnie okna **Właściwości** wybierz kartę **Aplikacja.**

   ![Karta Właściwości projektu Aplikacja](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Po utworzeniu aplikacji platformy uniwersalnej systemu Windows nie można zmienić docelowej wersji systemu Windows lub platformy NET.

1. Na liście **Struktura docelowa** wybierz odpowiednią wersję.

1. W wyświetlonym oknie dialogowym weryfikacji wybierz przycisk **Tak.**

   Projekt zostaje wyładowany Po ponownym załadowaniu jest przeznaczona dla wersji .NET, którą właśnie wybrałeś.

> [!NOTE]
> Jeśli kod zawiera odwołania do innej wersji platformy .NET niż ta, na którą kierowano, komunikaty o błędach mogą być wyświetlane podczas kompilowania lub uruchamiania kodu. Aby rozwiązać te błędy, zmodyfikuj odwołania. Zobacz [Rozwiązywanie problemów z błędami kierowania .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> W zależności od struktury docelowej może być reprezentowana w następujący sposób w pliku projektu:
>
> - W przypadku aplikacji .NET Core:`<TargetFramework>netcoreapp2.1</TargetFramework>`
> - W przypadku aplikacji .NET Standard:`<TargetFramework>netstandard2.0</TargetFramework>`
> - Dla aplikacji .NET Framework:`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Rozwiązywanie odwołań do zestawu systemowego i użytkownika

Aby kierować na wersję .NET, należy najpierw zainstalować odpowiednie odwołania do zestawu. Pakiety deweloperskie dla różnych wersji platformy .NET można pobrać na stronie [pliki do pobrania .NET.](https://www.microsoft.com/net/download/windows)

W przypadku projektów programu .NET Framework okno dialogowe **Dodawanie odwołania** wyłącza zestawy systemowe, które nie odnoszą się do docelowej wersji programu .NET Framework, dzięki czemu nie można ich przypadkowo dodać do projektu. (Zestawy systemowe to pliki *dll* zawarte w wersji programu .NET Framework). Odwołania, które należą do wersji framework, która jest wyższa niż wersja docelowa nie rozwiąże i formanty, które zależą od takiego odwołania nie można dodać. Jeśli chcesz włączyć takie odwołanie, należy zresetować obiekt docelowy programu .NET Framework projektu do takiego, który zawiera odwołanie.

Aby uzyskać więcej informacji na temat odwołań do złożenia, zobacz [Rozwiązywanie problemów z złożeniami w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Włącz linq

Gdy jest kierowana na platformę .NET Framework 3.5 lub nowszą, automatycznie dodawane jest odwołanie do **systemu System.Core** i importu na <xref:System.Linq> poziomie projektu (tylko w języku Visual Basic). Jeśli chcesz używać funkcji LINQ, musisz `Option Infer` również włączyć (tylko w języku Visual Basic). Odwołanie i import są usuwane automatycznie po zmianie obiektu docelowego na wcześniejszą wersję programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Praca z LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Zobacz też

- [Platformy docelowe](/dotnet/standard/frameworks)
- [Wielotargowe (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Jak: Modyfikowanie zestawu narzędzi struktury docelowej i platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
