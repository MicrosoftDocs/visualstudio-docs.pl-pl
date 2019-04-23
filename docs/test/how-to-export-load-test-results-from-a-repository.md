---
title: Eksportuj wyniki testu obciążeniowego
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 477ab8ce86188af9a3db03b92e1ea0f574d8a6a3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096767"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Instrukcje: Eksportuj wyniki testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [w repozytorium wyników testów obciążenia z wynikami testów obciążeniowych Zarządzaj](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testu obciążeniowego można zarządzać z edytora testu obciążenia, używając **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe. Można otworzyć, importować, eksportować i usuwać wyniki testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Aby wyeksportować wyniki z repozytorium

1. Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz **Otwórz i Zarządzaj wynikami**.

     **Otwórz i Zarządzaj wynikami testu obciążenia** zostanie wyświetlone okno dialogowe.

3. W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążeniowego**, wybierz kontroler. Wybierz  **\<lokalnie - bez kontrolera >** aby przejść do wyników przechowywanych lokalnie.

4. W **Pokaż wyniki następującego testu obciążeniowego**, zaznacz test obciążeniowy, którego wyniki chcesz wyświetlić. Wybierz  **\<Pokaż wyniki wszystkich testów >** aby zobaczyć wszystkie wyniki wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, są wyświetlane w **wyniki testu obciążeniowego** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, i **opis** zawiera opcjonalny opis dodawany przed uruchomieniem testu. **Opis** krótkie opisy, które zostały wprowadzone w kolumnie jest wyświetlana **komentarze dotyczące analizy** dla tego wyniku testu.

5. W **wyniki testu obciążeniowego** Wybierz wynik. Możesz użyć **Shift** klucza **Ctrl** klucza i / lub aby wybrać więcej niż jeden wynik, a następnie wyeksportować je do pojedynczego pliku.

6. Wybierz **wyeksportować**.

     **Eksportuj wyniki testu obciążenia** pojawi się okno dialogowe.

7. W **nazwy pliku** polu, wpisz nazwę, a następnie wybierz **Zapisz**.

     Wyniki zostaną wyeksportowane do pliku archiwum.

    > [!NOTE]
    > **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe pozostaje otwarty, po wyświetleniu wyników.

## <a name="see-also"></a>Zobacz także

- [Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Instrukcje: Usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Importuj wyniki testu obciążenia z repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)