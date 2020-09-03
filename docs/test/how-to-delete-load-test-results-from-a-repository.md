---
title: 'Porady: usuwanie wyników testu obciążenia z repozytorium'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd196076fb769f80c36ab8630eebf1e8a0f8b234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287782"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Instrukcje: usuwanie wyników testu obciążenia z repozytorium

Po uruchomieniu testu obciążenia informacje zebrane podczas przebiegu są przechowywane w repozytorium Załaduj Wyniki testów. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyniki testów ładowania](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Można zarządzać wynikami testów obciążenia z Edytor testu obciążeniowego przy użyciu okna dialogowego **Otwórz i zarządzaj wyniki testów ładowania** . Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Aby usunąć wyniki z repozytorium

1. Z projektu testu wydajności i obciążenia sieci Web Otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i Zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwórz i zarządzaj wyniki testów ładowania** .

3. W polu **Wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz **\<Local - No controller>** , aby uzyskać dostęp do wyników, które są przechowywane lokalnie.

4. W polu **Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz **\<Show results for all tests>** , aby wyświetlić wszystkie wyniki dla wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, pojawiają się na liście **wyników testu obciążenia** . Kolumny są typu **Time**, **Duration**, **User**, **wynik**, **test**i **Description**. **Test** zawiera nazwę testu, a **Opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu. W kolumnie **Opis** są wyświetlane krótkie opisy, które zostały wprowadzone w **komentarzach analizy** dla tego wyniku testu.

5. Na liście **wyników testu obciążenia** wybierz wynik. Możesz użyć klawisza **SHIFT** , klawisza **Ctrl** lub obu, aby zaznaczyć więcej niż jeden wynik.

6. Wybierz pozycję **Usuń**.

     Wyniki zostaną usunięte z repozytorium.

    > [!NOTE]
    > Okno dialogowe **otwieranie i zarządzanie ładowaniem wyniki testów** pozostaje otwarte po usunięciu wyników.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)
- [Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)
