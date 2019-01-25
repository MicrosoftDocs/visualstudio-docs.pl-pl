---
title: Kod testu jednostkowego | Dokumentacja firmy Microsoft
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2dfde0684e721b1ed4834d23fb9fc56363f9fb0b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782711"
---
# <a name="unit-test-your-code"></a>Testowanie jednostek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednostkowe pozwalają deweloperom i testerom w szybki sposób sprawdzić występowanie błędów logicznych w metodach klas w [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)], i [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] projektów.  
  
 Narzędzia do testów jednostkowych obejmują:  
  
1. **Test Explorer.** Eksplorator testów pozwala uruchomić testy jednostkowe i obejrzeć ich wyniki. Eksplorator testów może użyć dowolnego środowiska testów jednostkowych, włączając w to środowiska innych producentów, które posiadają adapter dla Eksploratora.  
  
2. **Testów jednostkowych Microsoft framework dla kodu zarządzanego.** Środowisko testów jednostkowych Microsoft dla kodu zarządzanego jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu środowiska .NET.  
  
3. **Środowisko testów jednostkowych Microsoft dla języka C++.** Środowisko testów jednostkowych Microsoft dla języka C++ jest instalowane z programem Visual Studio i zapewnia platformę do testowania kodu natywnego.  
  
4. **Narzędzia pokrycia kodu.** Można określić ilość kodu produktu, jaką bada test jednostkowy jednym poleceniem w Eksploratorze testów.  
  
5. **Środowisko izolacji Microsoft Fakes.** Środowisko izolacji Microsoft Fakes może stworzyć zastępcze klasy i metody dla kodu produkcyjnego i systemowego, który tworzy zależności w testowanym kodzie. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.  
  
   Można również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) aby eksplorować kod .NET w celu wygenerowania danych testu i pakietów testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. W przypadku każdego rozgałęzienia warunkowego w kodzie jest wykonywana analiza przypadku.  
  
## <a name="key-tasks"></a>Główne zadania  
 Należy skorzystać z następujących tematów, aby lepiej zrozumieć i z łatwością tworzyć testy jednostkowe:  
  
|Zadania|Skojarzone tematy|  
|-----------|-----------------------|  
|**Przewodniki Szybki Start i przewodniki dotyczące:** Użyj poniższych tematów, aby dowiedzieć się, testowanie jednostek w programie Visual Studio z przykładów kodu.|-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Szybki Start: Programowanie sterowane za pomocą narzędzia Eksplorator testów testami](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Testy jednostkowe kodu natywnego za pomocą narzędzia Eksplorator testów](http://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Testowanie jednostek za pomocą narzędzia Eksplorator testów:** Dowiedz się, jak Eksplorator testów może pomóc w tworzeniu bardziej wydajnych i efektywnych testów jednostkowych.|-   [O teście jednostkowym](../test/unit-test-basics.md)<br />-   [Tworzenie projektu testu jednostkowego](../test/create-a-unit-test-project.md)<br />-   [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)<br />-   [Aktualizowanie testów jednostkowych z Visual Studio 2010](http://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Testy jednostkowe kodu zarządzanego:**|-   [Pisanie testów jednostkowych dla .NET Framework za pomocą Frameworka testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Testy jednostkowe kodu C++**|-   [Pisanie testów jednostkowych dla języka C/C++ za pomocą Frameworka testów jednostkowych firmy Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Izolowanie testów jednostkowych**|-   [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Korzystanie z pokrycia kodu do identyfikacji, jaka część kodu projektu jest testowana za pomocą testów jednostkowych:** Dowiedz się więcej o funkcjonalności pokrycia kodu z [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] narzędzia do testowania.|-   [Korzystanie z pokrycia kodu, aby określić, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Wykonaj analizy wytrzymałościowej i wydajnościowej przez użycie testów obciążeniowych dla testów jednostkowych:** Można utworzyć test obciążenia i dodać testy jednostkowe do niej, aby pomóc wyizolować problemy wytrzymałościowe i wydajnościowe w aplikacji. **Uwaga:**  Tworzenie i używanie testów obciążeniowych wymaga programu Visual Studio Enterprise.|-   [Tworzenie i edytowanie testów obciążenia](http://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Jak: Dodaj testy wydajności sieci Web i testy jednostek do scenariusza testu obciążenia](http://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Jak: Usuń testy sieci Web i testów jednostkowych w scenariuszu testu obciążenia](http://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Ustawianie i wymuszanie bram jakości:** Można utworzyć bramki jakości, aby wymusić Uruchamianie testów przed zaewidencjonowaniem kodu pomagają zapewnić jakość kodu.|-   [Ustawianie i wymuszanie bram jakości](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Rozszerzenie typu testu jednostkowego:** Można dodawać funkcjonalność do testów, które mogą nie być w środowisku testów jednostkowych. Na przykład można dodać właściwość testu, która określa, czy test powinien być uruchomiony w kontekście zwykłego użytkownika. Można również rozszerzyć środowisko o dodanie atrybutów wiersza do metody i użyć danych w tym wierszu wewnątrz testu.|Przykładowy kod sposobu rozszerzenia środowiska testów jednostkowych, zobacz następującą [witrynie internetowej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Ustawianie opcji testowania:** Na przykład można określić, gdzie są przechowywane wyniki testu.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Zadania powiązane  
 [Sprawdzanie wyników testów w programie Microsoft Test Manager](http://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Opisuje wyniki testów i sposoby pracy z nimi, włączając w to sposób ich wyświetlania, zapisywania i usuwania.  
  
 [Trwa uruchamianie testów systemowych przy użyciu programu Microsoft Visual Studio](http://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 Zawiera łącza do informacji o używaniu programu Visual Studio, w przeciwieństwie do używania [!INCLUDE[TCMext](../includes/tcmext-md.md)] do uruchamiania testów automatycznych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Zawiera opis przestrzeni nazw UnitTesting, obejmujący atrybuty, wyjątki, potwierdzenia i inne klasy, które obsługują testy jednostkowe.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Opisuje przestrzeń unittesting.Web z przestrzeni nazw, która rozszerza przestrzeń nazw UnitTesting przez zapewnienie obsługi dla środowiska [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] i testów jednostkowych usług sieci Web.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Witryna Channel 9: Jednostki testowania aplikacji Windows Store utworzone przy użyciu XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fora  
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Tematy pomocy  
 [Indeks zawartości dla testów jednostkowych](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawianie jakości kodu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
