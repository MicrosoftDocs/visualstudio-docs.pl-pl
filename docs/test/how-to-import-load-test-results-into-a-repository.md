---
title: 'Porady: importowanie wyników testu obciążenia do repozytorium'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bbc8c352c7bf3cda0524f07aa82b6ccbe70602b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589035"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Jak: Importowanie wyników testu obciążenia do repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testów obciążenia można zarządzać z Edytora testów obciążenia za pomocą okna dialogowego **Otwieranie i zarządzanie wynikami testu obciążenia.** Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Aby zaimportować wyniki do repozytorium

1. Z projektu testu wydajności sieci web i obciążenia otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwieranie wyników testu obciążenia i zarządzanie** nimi.

3. W **wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia,** wybierz kontroler. Wybierz ** \<>lokalne,** aby uzyskać dostęp do wyników przechowywanych lokalnie.

     Jeśli dostępne są wyniki testu obciążenia, są one wyświetlane na liście **Wyniki testu obciążenia.** Kolumny to **Czas,** **Czas trwania,** **Użytkownik,** **Wynik,** **Test**i **Opis**. **Test** zawiera nazwę testu, a **opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu.

4. Wybierz **pozycję Importuj**.

     Zostanie wyświetlone okno dialogowe **Importowanie wyników testu obciążenia.**

5. W polu **Nazwa pliku** wpisz nazwę zarchiwizowanego pliku wyników testu, a następnie wybierz polecenie **Otwórz**.

     \-lub -

     Przejdź do pliku, a następnie wybierz pozycję **Otwórz**.

    > [!NOTE]
    > Zarchiwizowany plik wyników testu określony w tym kroku musi zostać utworzony przez wykonanie operacji Eksportuj.

     Wyniki są importowane i wyświetlane na liście **Wyniki testu obciążenia.**

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)
