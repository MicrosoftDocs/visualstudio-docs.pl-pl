---
title: 'Porady: wybieranie repozytorium wyników testu obciążenia'
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 513dd884f65e041e7ad90dda1483633fec57e100
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589009"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Jak: Wybierz repozytorium wyników testu obciążenia

Nie jesteś ograniczony do lokalnego magazynu wyników. Często testy obciążenia są uruchamiane na zdalnym zestawie komputerów agenta. Agenci, wraz z kontrolerem, mogą generować więcej symulowanego obciążenia niż jakikolwiek pojedynczy komputer. Aby uzyskać więcej informacji, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Wyniki testów z agentów lub komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono magazyn wyników testów obciążenia. W obu przypadkach należy określić, gdzie chcesz przechowywać wyniki testu obciążenia przy użyciu **administrującego kontrolerami testów** okna.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identyfikowanie magazynu wyników dla danych testu obciążenia

1. W **Eksploratorze rozwiązań**otwórz plik testu obciążenia.

2. Na **pasku narzędzi Testu obciążenia** wybierz pozycję **Zarządzaj kontrolerami testów**. Zostanie wyświetlone okno dialogowe **Zarządzanie kontrolerem testów.** Jeśli agent jest używany zdalnie, należy wybrać kontroler.

     ![Wyniki testu obciążenia przechowują właściwości](../test/media/loadtestconnectionproperties.png) połączenia Załaduj wyniki testu przechowują właściwości połączenia

3. W **magazynie wyników testu obciążenia**kliknij **przycisk (...)** , aby wyświetlić okno **dialogowe Właściwości połączenia.**

4. W **części Nazwa serwera**wpisz nazwę serwera, `LoadTest` na którym uruchomisz skrypty.

    > [!TIP]
    > Jeśli używasz programu SQL Express na komputerze lokalnym \<do przechowywania testów obciążenia, wprowadź nazwa komputera>\sqlexpress (na przykład **MyComputer\sqlexpress**).

5. W obszarze **Zaloguj się do serwera**można wybrać opcję Użyj **uwierzytelniania systemu Windows**. Możesz określić nazwę użytkownika i hasło, ale jeśli to zrobisz, musisz wybrać opcję **Zapisz moje hasło**.

6. W obszarze **Łączenie z bazą danych**wybierz pozycję Wybierz lub wprowadź nazwę bazy **danych**. Z listy rozwijanej wybierz **pozycję LoadTest.**

7. Wybierz pozycję **OK**. Połączenie można przetestować, wybierając opcję **Test połączenia**.

8. Wybierz **pozycję Zamknij** w oknie dialogowym Zarządzanie **kontrolerem testów.**

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
