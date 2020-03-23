---
title: Zarządzanie wynikami testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0562a6cceeb50d43222a7850de11d52b0587cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584429"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia

Po uruchomieniu testów obciążenia wszelkie informacje zebrane podczas przebiegu testu obciążenia mogą być przechowywane w *repozytorium wyników testu obciążenia,* który jest bazą danych SQL. Repozytorium wyników testu obciążenia zawiera dane licznika wydajności i wszelkie informacje o zarejestrowanych błędach. Baza danych repozytorium wyników jest tworzona przez instalatora dla kontrolerów lub tworzona automatycznie przy pierwszym uruchomieniu lokalnym testu obciążenia. W przypadku uruchomienia lokalnego baza danych zostanie utworzona automatycznie, jeśli schemat testu obciążenia nie jest obecny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli zmodyfikujesz parametry połączenia repozytorium wyników kontrolera, aby użyć innego serwera, nowy serwer musi mieć uruchomiony skrypt *loadtestresultsrepository.sql,* aby utworzyć schemat.

Visual Studio Enterprise udostępnia nazwane zestawy liczników, które zbierają typowe liczniki wydajności na podstawie technologii. Zestawy te są przydatne podczas analizowania serwera usług IIS, serwera ASP.NET lub serwera SQL. Wszystkie dane zebrane za pomocą zestawów liczników są przechowywane w repozytorium wyników testu obciążenia.

> [!IMPORTANT]
> Istnieje różnica między zestawem liczników a danymi licznika wydajności. Zestaw liczników to metadane. Definiuje grupę liczników wydajności, które powinny być zbierane z komputera, który wykonuje określoną rolę, takich jak usługi IIS lub SQL Server. Zestaw liczników jest częścią definicji testu obciążenia. Dane licznika wydajności są zbierane na podstawie zestawów liczników, mapowania licznika ustawionego na określony komputer i częstotliwości próbkowania.

## <a name="sql-server-versions"></a>Wersje programu SQL Server

Aby użyć testów obciążenia, można użyć programu SQL Server Express LocalDB, który jest instalowany w programie Visual Studio. Jest to domyślny serwer bazy danych do testów obciążenia (w tym integracji programu Microsoft Excel). SQL Server Express LocalDB jest trybem wykonywania programu SQL Server Express, który jest przeznaczony dla deweloperów programów. Instalacja programu SQL Server Express LocalDB kopiuje minimalny zestaw plików niezbędnych do uruchomienia aparatu bazy danych programu SQL Server.

Jeśli zespół oczekuje dużych potrzeb bazy danych lub projekty przerastają SQL Server Express LocalDB, należy rozważyć uaktualnienie do programu SQL Express lub pełnego programu SQL Server, aby zapewnić dalszy potencjał skalowania. W przypadku uaktualnienia programu SQL Server pliki MDF i LDF dla programu SQL Server Express LocalDB są przechowywane w folderze profilu użytkownika. Pliki te mogą być używane do importowania bazy danych testów obciążenia do programu SQL Server Express lub SQL Server.

## <a name="load-test-results-store-considerations"></a>Wyniki testu obciążenia przechowują uwagi

Po zainstalowaniu programu Visual Studio Enterprise magazyn wyników testu obciążenia jest skonfigurowany do używania wystąpienia programu SQL Express zainstalowanego na komputerze. Sql Express jest ograniczona do korzystania z maksymalnie 4 GB miejsca na dysku. Jeśli uruchomisz wiele testów obciążenia przez długi okres czasu, należy rozważyć skonfigurowanie magazynu wyników testów obciążenia, aby użyć wystąpienia pełnego produktu programu SQL Server, jeśli jest dostępny.

## <a name="load-test-analyzer-tasks"></a>Załaduj zadania analizatora testów

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Konfigurowanie repozytorium wyników testu obciążenia:** Można skonfigurować repozytorium wyników testu obciążenia w bazie danych SQL. **Uwaga:**  Repozytorium testu obciążenia można również utworzyć podczas instalowania kontrolera testów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).||
|**Wybieranie i wyświetlanie repozytorium wyników:** Można wybrać określone repozytorium wyników. Nie jesteś ograniczony do lokalnego magazynu wyników. Często testy obciążenia są uruchamiane na zdalnym zestawie komputerów agenta. Wyniki testów z agentów lub komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono magazyn wyników testów obciążenia. W obu przypadkach należy określić, gdzie należy przechowywać wyniki testu obciążenia przy użyciu **administrującego kontrolerów testów** okna.|-   [Jak: Wybierz repozytorium wyników testu obciążenia](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Usuwanie wyniku testu obciążenia z repozytorium:** Wynik testu obciążenia można usunąć z **Edytora testów obciążenia** za pomocą okna dialogowego **Otwieranie i zarządzanie wynikami testu obciążenia.**|-   [Jak: Usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importowanie i eksportowanie wyników do repozytorium:** Wyniki testów obciążenia można importować i eksportować z **Edytora testów obciążenia**.|-   [Jak: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Jak: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Zadania powiązane

[Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Można wyświetlić wyniki zarówno uruchomionego testu obciążenia, jak i testu obciążenia zakończonego przy użyciu **analizatora testów obciążenia**.

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)
