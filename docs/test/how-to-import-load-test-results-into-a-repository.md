---
title: 'Instrukcje: Importuj wyniki testu obciążenia z repozytorium'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: efbd13bf7ada237dc21bc5b2b6a186b13a52fd06
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932418"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Instrukcje: Importuj wyniki testu obciążenia z repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [w repozytorium wyników testów obciążenia z wynikami testów obciążeniowych Zarządzaj](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Wyniki testu obciążeniowego można zarządzać z edytora testu obciążenia, używając **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe. Można otworzyć, importować, eksportować i usuwać wyniki testu obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Aby zaimportować wyników do repozytorium

1.  Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2.  Na osadzonym pasku narzędzi wybierz **Otwórz i Zarządzaj wynikami**.

     **Otwórz i Zarządzaj wynikami testu obciążenia** zostanie wyświetlone okno dialogowe.

3.  W **wprowadź nazwę kontrolera Aby odnaleźć wyniki testu obciążeniowego**, wybierz kontroler. Wybierz  **\<lokalny >** aby przejść do wyników przechowywanych lokalnie.

     Jeśli wyniki testów obciążenia są dostępne, są wyświetlane w **wyniki testu obciążeniowego** listy. Kolumny są **czasu**, **czas trwania**, **użytkownika**, **wynik**, **testu**, i  **Opis elementu**. **Testowanie** zawiera nazwę testu, i **opis** zawiera opcjonalny opis dodawany przed uruchomieniem testu.

4.  Wybierz **importu**.

     **Importuj wyniki testu obciążeniowego** pojawi się okno dialogowe.

5.  W **nazwy pliku** polu, wpisz nazwę pliku wyników testu zarchiwizowany, a następnie wybierz **Otwórz**.

     \- lub —

     Przejdź do pliku, a następnie wybierz **Otwórz**.

    > [!NOTE]
    > Pliku wyników testu zarchiwizowany, który określisz w tym kroku musi być utworzony przez wykonanie operacji eksportowania.

     Wyniki są importowane i są wyświetlane w **wyniki testu obciążeniowego** listy.

## <a name="see-also"></a>Zobacz także

- [Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Eksportuj wyniki testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)