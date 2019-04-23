---
title: Poprawa jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c7b95155db18e9aa879b11cadf21b33cb0189ff9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103371"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy używasz Team Foundation Version Control (TFVC), można utworzyć zasady ewidencjonowania dla projektów zespołowych. Aby wymusić rozwiązań, które zachęcają do lepszego kodu i bardziej skutecznego rozwoju oprogramowania. Zasady ewidencjonowania to reguły, które są ustawiane na poziomie projektu zespołu i wymuszane na komputerach deweloperów, zanim będzie mógł zostać zaewidencjonowany kod.  
  
 Można określić te zespołu projektu zasad ewidencjonowania:  
  
- **Kompilacje**: Wymaga się, że błędy kompilacji, które zostały utworzone podczas kompilacji muszą zostać usunięte przed zaewidencjonowaniem.  
  
- **Komentarzy do zestawu zmian**: Wymaga od użytkowników podania komentarz podczas ewidencjonowania zmiany.  
  
- **Analiza kodu**: Wymaga, uruchamiania analizy kodu przed zaewidencjonowaniem.  
  
- **Elementy robocze**: Wymaga co najmniej jednego elementu roboczego skojarzonego z ewidencjonowanym.  
  
> [!IMPORTANT]
>  Aby użyć zasad ewidencjonowania, musisz mieć połączenie do [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Tworzenie i używanie zasad ewidencjonowania:** Utwórz zasady ewidencjonowania w przy użyciu ustawień projektu zespołowego [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Ustawianie i wymuszanie bram jakości](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Tworzenie i używanie zasad ewidencjonowania analizy kodu:** Można wybrać ze standardowego zestawu reguł analizy kodu lub można utworzyć niestandardowy zestaw.|[Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Skonfiguruj swoje Środowisko deweloperskie:** Zanim można utworzyć lub zmodyfikować kod, należy skonfigurować do tworzenia i środowisk testowych przy użyciu odpowiedniego kodu źródłowego. Jeśli pracujesz z bazami danych, musi również mieć dostęp do ich reprezentacji w trybie offline.|[Konfigurowanie środowisk](http://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Użyj analizy kodu w procesie tworzenia:** Członkowie zespołu, uruchamiania analizy kodu na swoich komputerach roboczych. W programie Visual Studio deweloperzy skonfigurować i uruchamiają analizę kodu dla poszczególnych projektów kodu, wyświetlanie oraz analizować problemy znalezione przez przebiegi i Utwórz elementy robocze dla ostrzeżeń.|[Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Tworzenie i Uruchamianie testów jednostkowych:** Testy jednostkowe pozwalają deweloperom i testerom w szybki sposób sprawdzić występowanie błędów logicznych w metodach klas w C#, Visual Basic .NET i projektów w języku C++. Test jednostkowy można utworzyć jeden raz i uruchamiany za każdym razem zmianie kodu źródłowego, aby upewnić się, że zostały wprowadzone żadne błędy.|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|  
|**Śledzenie elementów roboczych i defektów:** Elementy robocze można użyć do śledzenia i zarządzania pracą i informacjami o projekcie zespołowym. Element roboczy jest bazy danych rekord [!INCLUDE[esprfound](../includes/esprfound-md.md)] używa do śledzenia przypisania i postępu prac. Można użyć różnych rodzajów elementów roboczych do śledzenia różnych typów pracy takich jak wymagań klientów, błędów produktu i zadań programistycznych.|[Śledzenie pracy i zarządzanie przepływem pracy &#91;przekierowanie&#93;](http://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)
