---
title: 'Porady: wybieranie repozytorium wyników testu obciążenia'
description: Informacje na temat identyfikowania lokalnego lub zdalnego programu SQL Server do przechowywania wyników testów. Serwer musi mieć Magazyn wyników testu obciążenia.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
manager: jmartens
ms.openlocfilehash: 832b4f9257c328989b2d4d0f7db3bb5f49ec4f08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971859"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Instrukcje: wybieranie repozytorium wyników testu obciążenia

Nie jest ograniczony do lokalnego magazynu wyników. Często testy obciążenia są uruchamiane na zdalnym zestawie komputerów agentów. Agenci, wraz z kontrolerem, mogą generować bardziej symulowane obciążenia niż każdy pojedynczy komputer. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Wyniki testów od agentów lub komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono Magazyn wyników testu obciążenia. W obu przypadkach należy określić miejsce przechowywania wyników testu obciążenia przy użyciu okna **administrowanie kontrolerami testów** .

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identyfikowanie magazynu wyników dla danych testu obciążenia

1. W **Eksplorator rozwiązań** Otwórz plik testu obciążenia.

2. Na pasku narzędzi **testu obciążenia** wybierz pozycję **Zarządzaj kontrolerami testów**. Zostanie wyświetlone okno dialogowe **zarządzaj Test Controller** . Jeśli używasz agenta zdalnie, musisz wybrać kontroler.

     ![Wyniki testów obciążenia przechowują właściwości połączenia ](../test/media/loadtestconnectionproperties.png) Załaduj wyniki testu, przechowuj właściwości połączenia

3. W **magazynie wyników testu obciążenia** kliknij **(...)** , aby wyświetlić okno dialogowe **Właściwości połączenia** .

4. W polu **Nazwa serwera** wpisz nazwę serwera, na którym uruchomiono `LoadTest` skrypty.

    > [!TIP]
    > Jeśli używasz programu SQL Express na komputerze lokalnym dla magazynu testów obciążenia, wprowadź \<computername> \sqlexpress (na przykład **MYCOMPUTER\SQLEXPRESS**).

5. W obszarze **Zaloguj się do serwera** możesz wybrać opcję **Użyj uwierzytelniania systemu Windows**. Możesz określić nazwę użytkownika i hasło, ale jeśli to zrobisz, musisz wybrać opcję **Zapisz moje hasło**.

6. W obszarze **Połącz z bazą danych** wybierz **opcję Wybierz lub wprowadź nazwę bazy danych**. W polu listy rozwijanej wybierz pozycję **LoadTest** .

7. Wybierz przycisk **OK**. Możesz przetestować połączenie, wybierając pozycję **Testuj połączenie**.

8. W oknie dialogowym **zarządzaj Test Controller** wybierz pozycję **Zamknij** .

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
