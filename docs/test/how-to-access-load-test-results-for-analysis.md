---
title: Analizowanie wyników testu obciążenia
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6a5da728e24d5d7fdbeccd1e28aa2742e04bf48
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596466"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Jak: Dostęp do wyników testów obciążenia do analizy

Po uruchomieniu testu obciążenia z Edytora testów obciążenia wyniki testu obciążenia otwierają się automatycznie, a test obciążenia bieżącego jest wyświetlany w **analizatorze testów obciążenia**. Po uruchomieniu testu obciążenia z wiersza polecenia, należy uzyskać dostęp do wyników testu obciążenia ręcznie.

Wynik testu obciążenia dla testu obciążenia zakończonego zawiera próbki licznika wydajności i informacje o błędach, które były okresowo zbierane z komputerów pod-test. Wiele próbek licznika wydajności można zbierać w trakcie przebiegu testu obciążenia. Ilość danych o wydajności, która jest zbierana zależy od długości przebiegu testu, interwał próbkowania, liczba komputerów w fazie testów, liczba liczników są zbierane, moduły zbierające dane, które są skonfigurowane i poziomów rejestrowania. W przypadku testu dużego obciążenia ilość danych wydajności, które są zbierane może łatwo być kilka gigabajtów. Aby uzyskać więcej informacji, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Aby uzyskać dostęp do wyniku testu obciążenia

1. Z projektu testu wydajności sieci web i obciążenia otwórz test obciążenia.

2. Na pasku narzędzi Edytora testów obciążenia wybierz przycisk **Otwórz i zarządzaj wynikami.**

     Zostanie wyświetlone okno dialogowe **Otwieranie i zarządzanie wynikami.**

3. W **wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia,** wybierz kontroler. Wybierz ** \<> lokalne — brak kontrolera,** aby uzyskać dostęp do wyników przechowywanych lokalnie.

4. W **obszarze Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz ** \<pokaż wyniki dla wszystkich testów>,** aby wyświetlić wszystkie wyniki dla wszystkich testów.

     Jeśli dostępne są wyniki testu obciążenia, są one wyświetlane na liście **Wyniki testu obciążenia.** Kolumny to **Czas,** **Czas trwania,** **Użytkownik,** **Wynik,** **Test**i **Opis**. **Test** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu.

    > [!NOTE]
    > Wyniki są wyświetlane z najnowszymi wynikami na górze listy.

5. Na liście **Wyniki testu obciążenia** wybierz wyniki testu obciążenia, które chcesz przeanalizować, i wybierz pozycję **Otwórz**.

6. Pojawi się **analizator testu obciążenia.** Wybrany wynik testu obciążenia jest wyświetlany w widoku Podsumowanie. Aby uzyskać więcej informacji, zobacz [Omówienie podsumowania wyników testów ładowania](../test/load-test-results-summary-overview.md).

     W oknie dialogowym **Otwieranie i zarządzanie wynikami** można zarządzać innymi aspektami wyników obciążenia, w tym importowaniem, eksportowaniem i usuwaniem wyników testów obciążenia. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
