---
title: 'Porady: usuwanie wyników testu obciążenia z repozytorium'
ms.date: 10/19/2016
ms.topic: conceptual
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
ms.openlocfilehash: 26dc9750a2bf2eaf5d0ee5dd3d08485c458bb74a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589061"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Porady: z wynikami testów obciążeniowych usunięcia z repozytorium

Po uruchomieniu testu obciążenia, informacje, które zostały zebrane podczas uruchomienia jest przechowywane w repozytorium wyników testów obciążenia. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [w repozytorium wyników testów obciążenia z wynikami testów obciążeniowych Zarządzaj](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testu obciążeniowego można zarządzać z edytora testu obciążenia, używając **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe. Można otworzyć, importować, eksportować i usuwać wyniki testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Aby usunąć wyniki z repozytorium

1. Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz **Otwórz i Zarządzaj wynikami**.

     **Otwórz i Zarządzaj wynikami testu obciążenia** zostanie wyświetlone okno dialogowe.

3. W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążeniowego**, wybierz kontroler. Wybierz  **\<lokalnie - bez kontrolera >** aby przejść do wyników przechowywanych lokalnie.

4. W **Pokaż wyniki następującego testu obciążeniowego**, zaznacz test obciążeniowy, którego wyniki chcesz wyświetlić. Wybierz  **\<Pokaż wyniki wszystkich testów >** aby zobaczyć wszystkie wyniki wszystkich testów.

     Jeśli wyniki testów obciążenia są dostępne, są wyświetlane w **wyniki testu obciążeniowego** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, i **opis** zawiera opcjonalny opis dodawany przed uruchomieniem testu. **Opis** krótkie opisy, które zostały wprowadzone w kolumnie jest wyświetlana **komentarze dotyczące analizy** dla tego wyniku testu.

5. W **wyniki testu obciążeniowego** Wybierz wynik. Możesz użyć **Shift** klucza **Ctrl** klucza i / lub wybrać więcej niż jeden wynik.

6. Wybierz **Usuń**.

     Wyniki są usuwane z repozytorium.

    > [!NOTE]
    > **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe pozostaje otwarty, po usunięciu wyniki.

## <a name="see-also"></a>Zobacz także

- [Porady: z wynikami testów obciążeniowych eksportu z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)
- [Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: Importuj wyniki testu obciążenia z repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)
