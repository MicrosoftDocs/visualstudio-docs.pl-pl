---
title: Platformy .NET dla określonych platform
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b7c3c2b6b81f8f7793bda35c6b220e43caee9b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770445"
---
# <a name="framework-targeting-overview"></a>Omówienie określania celu platformy

W programie Visual Studio można określić wersję platformy .NET, dla której projekt ma być przeznaczony. Funkcja określania wartości docelowej platformy pomaga zagwarantować, że aplikacja będzie korzystać tylko z funkcji dostępnych w określonej wersji środowiska. Aby aplikacje .NET Framework działały na innym komputerze, wersja platformy, która jest przeznaczona dla aplikacji, musi być zgodna z wersją platformy zainstalowaną na komputerze.

Rozwiązanie programu Visual Studio może zawierać projekty przeznaczone dla różnych wersji platformy .NET.  Należy jednak pamiętać, że można kompilować tylko dla jednej wersji platformy .NET przy użyciu warunkowego odwołania dla pojedynczej kompilacji lub cyklicznie Kompiluj różne pliki binarne dla każdej wersji.  Aby uzyskać więcej informacji na temat platform docelowych, zobacz [Platformy docelowe](/dotnet/standard/frameworks).

> [!TIP]
> Możesz również docelować aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funkcje docelowej struktury

Funkcja określania wartości docelowej platformy obejmuje następujące funkcje:

- Po otwarciu projektu, który jest przeznaczony dla starszej wersji platformy, program Visual Studio może automatycznie uaktualnić projekt lub pozostawić element docelowy jako-is.

- Podczas tworzenia projektu .NET Framework można określić wersję .NET Framework, która ma być docelowa.

- Można [kierować wiele platform](/dotnet/standard/frameworks#how-to-specify-target-frameworks) w jednym projekcie.

- W każdym z kilku projektów w tym samym rozwiązaniu można wskazać inną wersję platformy .NET.

- Istnieje możliwość zmiany wersji platformy .NET, która ma projekt istniejący.

   W przypadku zmiany wersji platformy .NET, która jest przeznaczona dla projektu, program Visual Studio wprowadza wszelkie wymagane zmiany dotyczące odwołań i plików konfiguracji.

Podczas pracy nad projektem, który jest przeznaczony dla starszej wersji platformy, program Visual Studio dynamicznie zmienia środowisko programistyczne w następujący sposób:

- Filtruje elementy w oknie dialogowym **Dodaj nowy element** , okno dialogowe **Dodaj nowe odwołanie** i okno dialogowe **Dodaj odwołanie do usługi** , aby pominąć opcje, które nie są dostępne w wersji dostosowanej.

- Filtruje niestandardowe kontrolki w **przyborniku** , aby usunąć te, które nie są dostępne w wersji dostosowanej, i wyświetlić tylko najbardziej aktualne kontrolki, gdy dostępnych jest wiele kontrolek.

- Filtruje funkcję **IntelliSense** , aby pominąć funkcje języka, które nie są dostępne w wersji dostosowanej.

- Filtruje właściwości w oknie **Właściwości** , aby pominąć te, które nie są dostępne w wersji dostosowanej.

- Filtruje opcje menu, aby pominąć opcje, które nie są dostępne w wersji dostosowanej.

- W przypadku kompilacji używa wersji kompilatora i opcji kompilatora, które są odpowiednie dla wersji dostosowanej.

> [!NOTE]
> - Określanie wartości docelowej platformy nie gwarantuje, że aplikacja będzie działać poprawnie. Należy przetestować aplikację, aby upewnić się, że jest ona uruchamiana w porównaniu z wersją dodaną.
> - Nie można kierować wersji platformy poniżej .NET Framework 2,0.

## <a name="select-a-target-framework-version"></a>Wybierz docelową wersję platformy

Podczas tworzenia projektu .NET Framework można wybrać docelową wersję .NET Framework, po wybraniu szablonu projektu. Lista dostępnych platform obejmuje zainstalowane wersje Framework, które mają zastosowanie do wybranego typu szablonu. Dla szablonów projektów platformy non-.NET Framework, na przykład szablony platformy .NET Core, lista rozwijana **struktury** nie jest wyświetlana.

::: moniker range="vs-2017"

![Lista rozwijana platformy VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Lista rozwijana platformy w programie VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Zmień platformę docelową

W istniejącym projekcie Visual Basic, C# lub F # można zmienić docelową wersję platformy .NET w oknie dialogowym właściwości projektu. Aby uzyskać informacje o sposobie zmiany wersji docelowej dla projektów języka C++, zobacz [Jak zmodyfikować platformę docelową i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) .

1. W **Eksplorator rozwiązań**Otwórz menu dostępne po kliknięciu prawym przyciskiem myszy dla projektu, który chcesz zmienić, a następnie wybierz polecenie **Właściwości**.

1. W lewej kolumnie okna **Właściwości** wybierz kartę **aplikacja** .

   ![Karta aplikacji właściwości projektu](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Po utworzeniu aplikacji platformy UWP nie można zmienić dostosowanej wersji systemu Windows lub .NET.

1. Z listy **platforma docelowa** wybierz żądaną wersję.

1. W wyświetlonym oknie dialogowym weryfikacji wybierz przycisk **tak** .

   Projekt zostaje wyładowany Po ponownym załadowaniu jest on przeznaczony dla wybranej wersji platformy .NET.

> [!NOTE]
> Jeśli kod zawiera odwołania do innej wersji platformy .NET niż ta, której dotyczy, komunikaty o błędach mogą pojawić się podczas kompilowania lub uruchamiania kodu. Aby rozwiązać te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów dotyczących błędów docelowej platformy .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> W zależności od platformy docelowej można przedstawić następujące metody w pliku projektu:
>
> - W przypadku aplikacji .NET Core: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Dla aplikacji .NET Standard: `<TargetFramework>netstandard2.0</TargetFramework>`
> - Dla aplikacji .NET Framework: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Rozpoznaj odwołania do zestawów systemu i użytkownika

Aby określić wersję docelową platformy .NET, należy najpierw zainstalować odpowiednie odwołania do zestawu. Pakiety deweloperskie dla różnych wersji platformy .NET można pobrać na stronie [pliki do pobrania platformy .NET](https://www.microsoft.com/net/download/windows) .

W przypadku projektów .NET Framework okno dialogowe **Dodawanie odwołania** wyłącza Zestawy systemowe, które nie odnoszą się do wersji .NET Framework docelowej, tak że nie mogą zostać przypadkowo dodane do projektu. (Zestawy systemowe to pliki *dll* , które znajdują się w wersji .NET Frameworkej). Odwołania należące do wersji platformy, która jest wyższa niż wersja dostosowanej, nie zostaną rozpoznane i nie można dodać kontrolek, które zależą od tego odwołania. Jeśli chcesz włączyć takie odwołanie, zresetuj element docelowy .NET Framework projektu na taki, który zawiera odwołanie.

Aby uzyskać więcej informacji na temat odwołań do zestawów, zobacz temat [Rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Włącz LINQ

Jeśli obiektem docelowym jest .NET Framework 3,5 lub nowszy, odwołanie do **System. Core** i import na poziomie projektu dla <xref:System.Linq> (tylko w Visual Basic) są dodawane automatycznie. Jeśli chcesz używać funkcji LINQ, należy również włączyć opcję `Option Infer` (tylko w Visual Basic). Odwołanie i import są usuwane automatycznie w przypadku zmiany celu na wcześniejszą wersję .NET Framework. Aby uzyskać więcej informacji, zobacz [Work with LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Zobacz też

- [Platformy docelowe](/dotnet/standard/frameworks)
- [Wieloelementowe (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
