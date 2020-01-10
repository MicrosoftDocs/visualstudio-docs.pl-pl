---
title: Zwiększanie jakości kodu dzięki zasadom zaewidencjonowania projektu zespołowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eaf95bdba84d116198bf332e3cf2725f5e95e614
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848229"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z Kontrola wersji serwera Team Foundation (TFVC), można utworzyć zasady ewidencjonowania dla projektów zespołowych. Aby wymusić praktyki, które prowadzą do lepszego kodu i wydajniejszego opracowywania grup. Zasady ewidencjonowania są regułami ustawionymi na poziomie projektu zespołowego i wymuszanymi na komputerach deweloperskich, zanim kod będzie mógł zostać zaewidencjonowany.

 Można określić następujące zasady ewidencjonowania projektu zespołowego:

- **Kompilacje**: wymaga, aby podziały kompilacji, które zostały utworzone podczas kompilacji, musiały zostać naprawione przed nowym zaewidencjonowania.

- **Komentarze grupy zmian**: wymaga, aby użytkownicy mogli podawać komentarze podczas ewidencjonowania zmian.

- **Analiza kodu**: wymaga uruchomienia analizy kodu przed zaewidencjonowaniem.

- **Elementy robocze**: wymaga, aby co najmniej jeden element roboczy był skojarzony z zaewidencjonowania.

> [!IMPORTANT]
> Aby korzystać z zasad ewidencjonowania, musisz mieć połączenie z [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Tworzenie i Używanie zasad ewidencjonowania:** Zasady ewidencjonowania można tworzyć za pomocą ustawień projektu zespołowego [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Ustawianie i wymuszanie bram jakości](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie** z nich: Można wybrać spośród standardowego zestawu reguł analizy kodu lub utworzyć zestaw niestandardowy.|[Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Powiązane zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Skonfiguruj środowisko programistyczne:** Aby można było utworzyć lub zmodyfikować kod, należy skonfigurować środowiska deweloperskie i testowe przy użyciu odpowiedniego kodu źródłowego. Jeśli pracujesz z bazami danych, musisz również mieć dostęp do ich reprezentacji w trybie offline.|[Konfigurowanie środowisk programistycznych](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**Użyj analizy kodu w procesie tworzenia:** Członkowie zespołu uruchamiają analizę kodu na swoich komputerach deweloperskich. W programie Visual Studio deweloperzy konfigurują i uruchamiają analizę kodu dla poszczególnych projektów kodu, wyświetlają i analizują problemy znalezione w ramach przebiegów oraz tworzą elementy robocze dla ostrzeżeń.|[Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Utwórz i uruchom testy jednostkowe:** Testy jednostkowe umożliwiają deweloperom i testerom szybkie wyszukiwanie błędów logicznych w metodach klas w C#, Visual Basic .NET i C++ projektach. Test jednostkowy można utworzyć jednorazowo i uruchomić za każdym razem, gdy kod źródłowy zostanie zmieniony, aby upewnić się, że nie zostały wprowadzone żadne błędy.|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|
|**Śledź elementy robocze i wady:** Elementy robocze umożliwiają śledzenie i zarządzanie pracy oraz informacjami o projekcie zespołowym. Element roboczy jest rekordem bazy danych, który [!INCLUDE[esprfound](../includes/esprfound-md.md)] używa do śledzenia przydziału i postępu prac. Można użyć różnych typów elementów roboczych do śledzenia różnych typów pracy, takich jak wymagania klienta, usterki produktów i zadania programistyczne.|[Śledzenie pracy i zarządzanie przepływem pracy &#91;przekierowane&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)
