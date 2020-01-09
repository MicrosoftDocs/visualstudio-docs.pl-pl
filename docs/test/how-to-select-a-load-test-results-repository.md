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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589009"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Porady: Wybieranie repozytorium wyników testu obciążenia

Nie jesteś ograniczony do magazynu wyników lokalnych. Często testy obciążenia są uruchamiane na zbiorze zdalnym komputerów agentów. Agenci, wraz z kontrolerem, można wygenerować bardziej symulowane obciążenie niż dowolnego pojedynczego komputera. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Wyniki testów z agentów lub z komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono Magazyn wyników testu obciążenia. W obu przypadkach należy określić, której chcesz przechowywać wyniki testu obciążenia przy użyciu **Administrowanie kontrolerami testów** okna.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identyfikowanie magazynu wyników dla danych testu obciążenia

1. W **Eksploratora rozwiązań**, otwórz plik testu obciążeniowego.

2. Z **testu obciążeniowego** narzędzi, wybierz **Zarządzaj kontrolerami testów**. **Zarządzaj kontrolerem testów** zostanie wyświetlone okno dialogowe. Jeśli używasz agenta zdalnego, należy wybrać kontroler.

     ![Właściwości połączenia przechowywania wyników testów obciążenia](../test/media/loadtestconnectionproperties.png) właściwości połączenia przechowywania wyników testów obciążenia

3. W **magazynu z wynikami testów obciążeniowych**, kliknij przycisk **(...)**  do wyświetlenia **właściwości połączenia** okno dialogowe.

4. W **nazwy serwera**, wpisz nazwę serwera, na którym uruchomiono `LoadTest` skryptów.

    > [!TIP]
    > Jeśli używasz programu SQL Express na komputerze lokalnym do magazynu testów obciążeniowych, wprowadź \<nazwa_komputera > \sqlexpress (na przykład **MyComputer\sqlexpress**).

5. W obszarze **Zaloguj się na serwerze**, możesz wybrać **uwierzytelnianie Windows**. Można określić nazwę użytkownika i hasło, ale jeśli to zrobisz, musisz wybrać opcję **Zapisz moje hasło**.

6. W obszarze **nawiązywanie połączenia z bazą danych**, wybierz **wybierz lub wprowadź nazwę bazy danych**. Wybierz **LoadTest** w polu listy rozwijanej.

7. Wybierz **OK**. Możesz przetestować połączenie, wybierając **Testuj połączenie**.

8. Wybierz **Zamknij** w **Zarządzaj kontrolerem testów** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
