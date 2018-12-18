---
title: Analizowanie wyników testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 4c5da35407b028d1c435c87a55f265bd22c46c3a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047632"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Porady: dostęp do wyników testów obciążenia do analizy

Po uruchomieniu testu obciążenia z edytora testu obciążenia, automatycznego otwierania wyników testów obciążenia, i uruchamianie testu obciążenia jest wyświetlana w **analizatora testu obciążenia**. Po uruchomieniu testu obciążenia z wiersza polecenia, możesz ręcznie dostęp wyniki testu obciążenia.

Wynik testu obciążenia dla ukończonego testu obciążenia zawiera próbki liczników wydajności i informacje o błędzie, który zbierano okresowo z komputerów objętych testami. Duża liczba próbek liczników wydajności może być zbierana w trakcie przebiegu testu obciążeniowego. Ilość zebranych danych wydajności zależy od długości przebiegu testu, interwał próbkowania, liczby komputerów w obszarze badania, liczby gromadzonych liczników, modułów zbierających dane, które są skonfigurowane i poziomów rejestrowania. Dużym teście obciążenia ilość zebranych danych wydajności może łatwo wynieść kilka gigabajtów. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Aby dostęp do wyniku testu obciążeniowego

1.  Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2.  Na pasku narzędzi edytora testu obciążenia wybierz **Otwórz i Zarządzaj wynikami** przycisku.

     **Otwórz i Zarządzaj wynikami** pojawi się okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążeniowego**, wybierz kontroler. Wybierz  **\<lokalny >-bez kontrolera** aby przejść do wyników przechowywanych lokalnie.

4.  W **Pokaż wyniki następującego testu obciążeniowego**, zaznacz test obciążeniowy, którego wyniki chcesz wyświetlić. Wybierz  **\<Pokaż wyniki wszystkich testów >** aby zobaczyć wszystkie wyniki wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, są wyświetlane w **wyniki testu obciążeniowego** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, i **opis** zawiera opcjonalny opis dodawany przed uruchomieniem testu.

    > [!NOTE]
    > Wyniki są wyświetlane najnowsze wyniki w górnej części listy.

5.  W **wyniki testu obciążeniowego** zaznacz wyniki testu obciążenia, aby analizować i wybierz pozycję **Otwórz**.

6.  **Analizatora testu obciążenia** pojawia się. Wynik testu obciążenia wybranego jest wyświetlany w widoku podsumowania. Aby uzyskać więcej informacji, zobacz [Przegląd podsumowania z wynikami testów obciążeniowych](../test/load-test-results-summary-overview.md).

     Może zarządzać innymi aspektami wyników testów obciążenia w **Otwórz i Zarządzaj wynikami** okno dialogowe, w tym importowanie, eksportowanie i usuwanie wyników testu obciążenia. Aby uzyskać więcej informacji, zobacz [wyniki testu obciążeniowego Zarządzanie obciążenia test repozytorium wyników](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)