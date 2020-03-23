---
title: Wyniki testu obciążenia eksportu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f72dbd687bc9177cd4cfd36416acb23445d30c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589048"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Jak: Eksportowanie wyników testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testów obciążenia można zarządzać z Edytora testów obciążenia za pomocą okna dialogowego **Otwieranie i zarządzanie wynikami testu obciążenia.** Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Aby wyeksportować wyniki z repozytorium

1. Z projektu testu wydajności sieci web i obciążenia otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwieranie wyników testu obciążenia i zarządzanie** nimi.

3. W **wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia,** wybierz kontroler. Wybierz ** \<opcję Lokalny — brak kontrolera>,** aby uzyskać dostęp do wyników przechowywanych lokalnie.

4. W **obszarze Pokaż wyniki dla następującego testu obciążenia**wybierz test obciążenia, którego wyniki chcesz wyświetlić. Wybierz ** \<pokaż wyniki dla wszystkich testów>,** aby wyświetlić wszystkie wyniki dla wszystkich testów.

     Jeśli wyniki testu obciążenia są dostępne, są one wyświetlane na liście **Wyniki testu obciążenia.** Kolumny to **Czas,** **Czas trwania,** **Użytkownik,** **Wynik,** **Test**i **Opis**. **Test** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu. Kolumna **Opis** wyświetla krótkie opisy, które zostały wprowadzone w **komentarzach do analizy** dla tego wyniku testu.

5. Na liście **Wyniki testu obciążenia** wybierz wynik. Za pomocą **klawisza Shift,** **klawisza Ctrl** lub obu można wybrać więcej niż jeden wynik i wyeksportować go do jednego pliku.

6. Wybierz **pozycję Eksportuj**.

     Zostanie wyświetlone okno dialogowe **Eksportuj wyniki testu obciążenia.**

7. W polu **Nazwa pliku** wpisz nazwę, a następnie wybierz pozycję **Zapisz**.

     Wyniki zostaną wyeksportowane do pliku archiwum.

    > [!NOTE]
    > Okno dialogowe **Otwieranie wyników testów obciążenia i zarządzanie nimi** pozostaje otwarte po wyświetlenie wyników.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Jak: Usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)
