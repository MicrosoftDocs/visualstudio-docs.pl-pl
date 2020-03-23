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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589061"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Jak: Usuwanie wyników testu obciążenia z repozytorium

Po uruchomieniu testu obciążenia informacje, które zostały zebrane podczas uruchamiania są przechowywane w repozytorium wyników testu obciążenia. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testów obciążenia można zarządzać z Edytora testów obciążenia za pomocą okna dialogowego **Otwieranie i zarządzanie wynikami testu obciążenia.** Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Aby usunąć wyniki z repozytorium

1. Z projektu testu wydajności sieci web i obciążenia otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwieranie wyników testu obciążenia i zarządzanie** nimi.

3. W **wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia,** wybierz kontroler. Wybierz ** \<opcję Lokalny — nie>kontrolera,** aby uzyskać dostęp do wyników przechowywanych lokalnie.

4. W **obszarze Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz ** \<pokaż wyniki dla wszystkich testów>,** aby wyświetlić wszystkie wyniki dla wszystkich testów.

     Jeśli wyniki testu obciążenia są dostępne, są one wyświetlane na liście **Wyniki testu obciążenia.** Kolumny to **Czas,** **Czas trwania,** **Użytkownik,** **Wynik,** **Test**i **Opis**. **Test** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu. Kolumna **Opis** wyświetla krótkie opisy, które zostały wprowadzone w **komentarzach do analizy** dla tego wyniku testu.

5. Na liście **Wyniki testu obciążenia** wybierz wynik. Za pomocą klawisza **Shift,** **klawisza Ctrl** lub obu można wybrać więcej niż jeden wynik.

6. Wybierz pozycję **Usuń**.

     Wyniki są usuwane z repozytorium.

    > [!NOTE]
    > Okno dialogowe **Otwieranie wyników testów obciążenia i zarządzanie nimi** pozostaje otwarte po usunięciu wyników.

## <a name="see-also"></a>Zobacz też

- [Jak: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)
- [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)
