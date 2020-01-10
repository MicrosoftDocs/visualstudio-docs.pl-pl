---
title: Testowanie jednostkowe kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851256"
---
# <a name="unit-test-your-code"></a>Testowanie jednostek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednostkowe umożliwiają deweloperom i testerom szybkie wyszukiwanie błędów logicznych w metodach klas w projektach [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]i [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].

 Narzędzia do testów jednostkowych obejmują:

1. **Test Explorer.** Eksplorator testów pozwala uruchomić testy jednostkowe i obejrzeć ich wyniki. Eksplorator testów może użyć dowolnego środowiska testów jednostkowych, włączając w to środowiska innych producentów, które posiadają adapter dla Eksploratora.

2. **Środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego.** Środowisko testów jednostkowych Microsoft dla kodu zarządzanego jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu środowiska .NET.

3. **Środowisko testów jednostkowych firmy C++Microsoft dla programu.** Środowisko testów jednostkowych Microsoft dla języka C++ jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu natywnego.

4. **Narzędzia pokrycia kodu.** Można określić ilość kodu produktu, jaką bada test jednostkowy jednym poleceniem w Eksploratorze testów.

5. **Struktura izolacji sztucznej firmy Microsoft.** Środowisko izolacji Microsoft Fakes może stworzyć zastępcze klasy i metody dla kodu produkcyjnego i systemowego, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

   Można również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) aby eksplorować kod .NET w celu wygenerowania danych testu i pakietów testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. W przypadku każdego rozgałęzienia warunkowego w kodzie jest wykonywana analiza przypadku.

## <a name="key-tasks"></a>Główne zadania
 Należy skorzystać z następujących tematów, aby lepiej zrozumieć i z łatwością tworzyć testy jednostkowe:

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Przewodniki Szybki Start i przewodniki:** Użyj poniższych tematów, aby dowiedzieć się, testowanie jednostek w programie Visual Studio z przykładów kodu.|[przewodnik -   : Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Dodawanie testów jednostkowych do C++ istniejących aplikacji](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [testy jednostkowe kodu natywnego za pomocą Eksploratora testów](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Testowanie jednostek za pomocą narzędzia Eksplorator testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i efektywnych testów jednostkowych.|[podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md) -   <br />-   [Tworzenie projektu testu jednostkowego](../test/create-a-unit-test-project.md)<br />-   [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)<br />-   [uaktualnić testy jednostkowe z programu Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Testowanie jednostkowe kodu zarządzanego:**|-   [pisania testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Testy jednostkowe kodu C++**|-   [pisać testy jednostkowe dla CC++ /za pomocą struktury testów jednostkowych C++ firmy Microsoft dla](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Izolowanie testów jednostkowych**|-   [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md) elementów sztucznych firmy Microsoft|
|**Użyj pokrycia kodu, aby określić, jaka część kodu projektu jest testowana przy użyciu testów jednostkowych:** Dowiedz się więcej o funkcji pokrycia kodu narzędzi do testowania [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)].|-   [przy użyciu pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Wykonaj analizę obciążeniową i wydajnościową, używając testów obciążeniowych dla testów jednostkowych:** Można utworzyć test obciążeniowy i dodać do niego testy jednostkowe, aby ułatwić odizolowanie problemów z wydajnością i obciążeniem w aplikacji. **Uwaga:**  Tworzenie i używanie testów obciążenia wymaga Visual Studio Enterprise.|-   [tworzenia i edytowania testów obciążenia](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [: Dodawanie testów wydajności sieci Web i testów jednostkowych do scenariusza testu obciążenia](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [: usuwanie testów sieci Web i testów jednostkowych z scenariusza testu obciążenia](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Ustawianie i wymuszanie bram jakości:** Można utworzyć bramy jakości, aby wymusić, że testy są uruchamiane przed zaewidencjonowaćm kod, aby zapewnić jakość kodu.|-   [Ustawianie i wymuszanie bram jakości](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Poszerzenie typu testu jednostkowego:** Możesz dodać funkcję do testów, które mogą nie znajdować się w środowisku testów jednostkowych. Na przykład można dodać właściwość testu, która określa, czy test powinien być uruchomiony w kontekście zwykłego użytkownika. Można również rozszerzyć środowisko o dodanie atrybutów wiersza do metody i użyć danych w tym wierszu wewnątrz testu.|Przykładowy kod dotyczący sposobu rozbudowania struktury testów jednostkowych można znaleźć w następującej [witrynie sieci Web firmy Microsoft](https://msdn.microsoft.com/vstudio/ff420671.aspx).|
|**Ustawianie opcji testowania:** na przykład określić, gdzie są przechowywane wyniki testu.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>Zadania powiązane
 [Przeglądanie Wyniki testów w Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Opisuje wyniki testów i sposoby pracy z nimi, włączając w to sposób ich wyświetlania, zapisywania i usuwania.

 [Uruchamianie testów systemowych przy użyciu Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Zawiera łącza do informacji dotyczących korzystania z programu Visual Studio, a nie przy użyciu [!INCLUDE[TCMext](../includes/tcmext-md.md)] do uruchamiania testów automatycznych.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> opisuje przestrzeń nazw UnitTesting, która udostępnia atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> opisuje przestrzeń nazw UnitTesting. Web, która rozszerza przestrzeń nazw UnitTesting przez zapewnienie wsparcia dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] i testów jednostkowych usług sieci Web.

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="videos"></a>Wideo
 [Channel 9: testowanie jednostkowe aplikacji ze sklepu Windows skompilowanych przy użyciu języka XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Fora
 [Visual Studio Unit Testing](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Tematy pomocy
 [Indeks zawartości dla testów jednostkowych](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>Zobacz też
 [Ulepsz testowanie jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [w aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
