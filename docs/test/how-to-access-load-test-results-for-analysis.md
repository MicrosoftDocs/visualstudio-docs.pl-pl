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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6be8649ab611a44cb9d2791ae1f4a0e61e930d5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664881"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy

Po uruchomieniu testu obciążenia z Edytor testu obciążeniowego, wyniki testu obciążenia są otwierane automatycznie, a uruchomiony test obciążenia jest wyświetlany w **analizatorze testu obciążenia**. Po uruchomieniu testu obciążenia z wiersza polecenia, należy ręcznie uzyskać dostęp do wyników testu obciążenia.

Wynik testu obciążenia dla zakończonego testu obciążenia zawiera próbki licznika wydajności i informacje o błędach, które zostały zebrane okresowo z komputerów poddawanych testom. Duża liczba próbek licznika wydajności może być zbierana w trakcie przebiegu testu obciążenia. Ilość zbieranych danych wydajności zależy od długości przebiegu testu, interwału próbkowania, liczby komputerów objętych testem, liczby zbieranych liczników, skonfigurowanych modułów zbierających dane oraz poziomów rejestrowania. W przypadku dużego testu obciążenia ilość zbieranych danych wydajności może być łatwo większa niż kilka gigabajtów. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Aby uzyskać dostęp do wyniku testu obciążenia

1. Z projektu testu wydajności i obciążenia sieci Web Otwórz test obciążenia.

2. Na pasku narzędzi Edytor testu obciążeniowego wybierz przycisk **Otwórz i Zarządzaj wynikami** .

     Zostanie wyświetlone okno dialogowe **Otwórz i Zarządzaj wynikami** .

3. W polu **Wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz pozycję **\<local > — Brak kontrolera** , aby uzyskać dostęp do wyników przechowywanych lokalnie.

4. W polu **Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz **\<Show wyniki dla wszystkich testów >** , aby zobaczyć wszystkie wyniki dla wszystkich testów.

     Jeśli są dostępne wyniki testów obciążenia, są one wyświetlane na liście **wyników testu obciążenia** . Kolumny są typu **Time**, **Duration**, **User**, **wynik**, **test**i **Description**. **Test** zawiera nazwę testu, a **Opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu.

    > [!NOTE]
    > Wyniki są wyświetlane z najnowszymi wynikami w górnej części listy.

5. Na liście **wyników testu obciążenia** wybierz wyniki testu obciążenia, które chcesz analizować, a następnie wybierz pozycję **Otwórz**.

6. Zostanie wyświetlony **Analizator testu obciążenia** . Wybrany wynik testu obciążenia jest wyświetlany w widoku podsumowania. Aby uzyskać więcej informacji, zobacz [Omówienie podsumowania wyników testu obciążenia](../test/load-test-results-summary-overview.md).

     Można zarządzać innymi aspektami wyników testu obciążenia w oknie dialogowym **Otwórz i Zarządzaj wynikami** , w tym importowaniem, eksportowaniem i usuwaniem wyników testu obciążenia. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)