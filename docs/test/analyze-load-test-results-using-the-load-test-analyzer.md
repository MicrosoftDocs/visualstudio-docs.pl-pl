---
title: Analizowanie wyników testów obciążenia w programie Visual Studio
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 92685b4ed7f3ea9bfbaaad70d3bb61786bcc82a0
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896669"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia za pomocą analizatora testu obciążenia

Znajdź wąskie gardła, identyfikowanie błędów i zmierzyć ulepszenia w aplikacji, korzystając z **analizatora testu obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analizowanie wyników testów obciążenia w następujący sposób:

-   Badania obciążenia należy monitorować wtedy, gdy jest uruchomiona.

-   Analizuj badania obciążenia po jego ukończeniu.

-   Wyświetlanie wyników z poprzedniego testu obciążenia.

Można również tworzyć raporty, pozwalające porównać dwa lub więcej raportów dla analizy trendu udostępnić zainteresowanym osobom. Zobacz [testy obciążenia raportowanie wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).

Możesz wykonać te zadania, czy uruchomić test obciążenia z Visual Studio Enterprise lub z wiersza polecenia i tego, czy uruchomić test obciążenia na jednym komputerze lub na komputerze zdalnym.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Różnice między analizowanie uruchomione i zakończonego testu obciążenia

 Po uruchomieniu testu obciążenia, **analizatora testu obciążenia** wyświetlane na osobnej karcie wraz z nazwą testu obciążenia i czas uruchomienia testu (na przykład **LoadTest1 [godzina 12:40]**). Po uruchomieniu testu obciążenia mniejszy zestaw danych licznika wydajności jest utrzymywany w pamięci. Ten zestaw danych można monitorować po uruchomieniu testu obciążenia. Po zakończeniu testu obciążenia można analizować pełny zestaw danych z bazy danych. Istnieją różnice w jaki dane są wyświetlane podczas wykonywania testu obciążeniowego i danych, które mogą występować po załadowaniu testów zostało zakończone. Na przykład procent 90 i 95 procent danych czasu odpowiedzi nie jest obliczana, dopóki nie zakończy się test obciążenia. Pewne różnice również wystąpić funkcjonalności, narzędzi, które są dostępne do analizowania danych.

 Po uruchomieniu testu obciążenia, dostępne są dwa widoki: **wykresów** widoku i **tabel** widoku. **Wykresów** widoku umożliwia liczniki wydajności programu graph, które są zbierane. **Tabel** widok udostępnia informacje o poszczególnych testach, strony, transakcji i żądania, które są zbierane. Możesz także uzyskać tabelę, która zawiera błędy.

 Domyślnie, po zakończeniu przebiegu testu obciążeniowego **Podsumowanie** wyświetlany jest widok. Możesz przełączać się między **Podsumowanie**, **wykresów**, **tabel**, i **szczegóły** widoków przy użyciu paska narzędzi. **Analizatora testu obciążenia** zadokowany lub ustawić na float przy użyciu zwykłych technik manipulacji okna Visual Studio. Podczas analizowania przebiegów testów obciążeniowych ukończone może mieć wiele **załadować testów analizatory** otwarte w tym samym czasie, aby porównać przebiegi testów różne obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uzyskiwanie dostępu do wyników testu obciążenia:** po uruchomieniu testu obciążenia z edytora testu obciążenia, automatycznego otwierania wyników testów obciążenia, i uruchamianie testu obciążenia jest wyświetlana w **analizatora testu obciążenia**.|-   [Porady: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Dodaj notatki analizy do testu obciążeniowego:** Dodawanie komentarzy do testu obciążeniowego podczas przeprowadzania analizy. Komentarze są przechowywane trwale, wraz z wynikiem testu obciążenia. Wyświetla opis, który możesz również wprowadzić **opis** kolumny, która jest skojarzona z testu obciążenia w **Otwórz i Zarządzaj wynikami testu** okno dialogowe w edytorze testu obciążeniowego.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ponadto komentarze są wyświetlane, gdy tworzysz raport programu Excel dla obciążenia wyniki testu.<br /><br /> Aby uzyskać więcej informacji, zobacz [testy obciążenia raportowanie wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).||
|**Analizowanie wyników testu obciążeniowego:** po uzyskujesz dostęp do danych przebiegu testu obciążeniowego, można analizować dane wynikowe. Możesz wyświetlić podsumowanie testu obciążeniowego, aby szybko poznać wyniki. Podsumowanie testu obciążeniowego przedstawia wyniki klucza w formacie zwarty i łatwe do odczytu.<br /><br /> Podsumowanie testu obciążeniowego można wydrukować. Ułatwia to używane podczas komunikowania się wyniki do zainteresowanych stron.<br /><br /> Szczegóły wyników testu obciążenia można analizować za pomocą wykresów i tabel w wynikach. Obejmują one **błędy**, **stron**, **żądań**, **śledzenia SQL**, **testy**,  **Progi**, i **transakcji**.|-   [Przegląd podsumowania wyników testu obciążenia](../test/load-test-results-summary-overview.md)<br />-   [Porady: wyświetlanie odpowiedzi strony sieci web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analizowanie aktywności wirtualnego użytkownika w wynikach testu obciążenia można wyizolować problemy z wydajnością:** wykres aktywności wirtualnych użytkowników umożliwia wizualizowanie, co robią użytkownicy wirtualni podczas testu obciążeniowego. Może to pomóc wyizolować skoków Procesora lub przerwy w żądań na sekundę i określić, które testy lub stron, które są uruchomione podczas tych wzrostów i spadnie.|-   [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|