---
title: Zarządzanie Wyniki testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6b24fcc485462b8d67ae88104c1ee3ed156e747
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652935"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia

Kiedy uruchamiasz testy obciążenia, wszystkie informacje zebrane podczas uruchomienia testu obciążenia mogą być przechowywane w *repozytorium wyniki testów obciążenia*, które jest bazą danych SQL. Repozytorium Wyniki testów obciążenia zawiera dane licznika wydajności i wszelkie informacje o zarejestrowanych błędach. Baza danych repozytorium wyników jest tworzona przez Instalatora dla kontrolerów lub tworzona automatycznie podczas pierwszego lokalnego przebiegu testu obciążenia. W przypadku lokalnego uruchomienia baza danych zostanie utworzona automatycznie, jeśli schemat testu obciążenia nie jest obecny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli zmodyfikujesz parametry połączenia repozytorium wyników kontrolera w celu użycia innego serwera, nowy serwer musi mieć uruchomiony skrypt *loadtestresultsrepository. SQL* , aby utworzyć schemat.

Visual Studio Enterprise udostępnia nazwane zestawy liczników, które zbierają typowe liczniki wydajności na podstawie technologii. Te zestawy są przydatne podczas analizowania serwera IIS, serwera ASP.NET lub programu SQL Server. Wszystkie zebrane dane za pomocą zestawów liczników są przechowywane w repozytorium Wyniki testów obciążenia.

> [!IMPORTANT]
> Istnieje różnica między zestawem liczników a danymi licznika wydajności. Zestaw liczników to Metadata. Definiuje grupę liczników wydajności, które powinny być zbierane z komputera, który wykonuje określoną rolę, taką jak usługi IIS lub SQL Server. Zestaw liczników jest częścią definicji testu obciążenia. Dane licznika wydajności są zbierane w oparciu o zbiory liczników, mapowanie zestawu liczników do określonego komputera oraz częstotliwość próbkowania.

## <a name="sql-server-versions"></a>Wersje SQL Server

Aby skorzystać z testów obciążenia, można użyć SQL Server Express LocalDB, który jest instalowany z programem Visual Studio. Jest to domyślny serwer bazy danych dla testów obciążenia (łącznie z integracją programu Microsoft Excel). SQL Server Express LocalDB to tryb wykonywania SQL Server Express, który jest przeznaczony dla deweloperów programu. SQL Server Express instalacji LocalDB kopiuje minimalny zestaw plików niezbędnych do uruchomienia aparatu bazy danych SQL Server Database.

Jeśli Twój zespół oczekuje na duże zapotrzebowanie bazy danych lub że Twoje projekty skalowalność SQL Server Express LocalDB, rozważ uaktualnienie do wersji SQL Express lub Full SQL Server, aby zapewnić dalsze skalowanie możliwości. W przypadku uaktualnienia SQL Server pliki MDF i LDF dla SQL Server Express LocalDB są przechowywane w folderze profilu użytkownika. Te pliki mogą służyć do importowania bazy danych testu obciążenia do SQL Server Express lub SQL Server.

## <a name="load-test-results-store-considerations"></a>Zagadnienia dotyczące magazynu wyników testów obciążenia

Po zainstalowaniu Visual Studio Enterprise Magazyn wyników testu obciążenia jest skonfigurowany do korzystania z wystąpienia programu SQL Express zainstalowanego na komputerze. Program SQL Express jest ograniczony do korzystania z maksymalnie 4 GB miejsca na dysku. Jeśli uruchomisz wiele testów obciążenia w długim okresie czasu, należy rozważyć skonfigurowanie magazynu wyników testów obciążenia w celu użycia wystąpienia pełnego SQL Server produktu, jeśli jest dostępny.

## <a name="load-test-analyzer-tasks"></a>Zadania analizatora testu obciążenia

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Skonfiguruj repozytorium wyników testu obciążenia:** Repozytorium wyników testów obciążenia można skonfigurować w bazie danych SQL. **Uwaga:**  Repozytorium testów obciążenia można również utworzyć podczas instalacji kontrolera testów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).||
|**Wybieranie i wyświetlanie repozytorium wyników:** Możesz wybrać określone repozytorium wyników. Nie jest ograniczony do lokalnego magazynu wyników. Często testy obciążenia są uruchamiane na zdalnym zestawie komputerów agentów. Wyniki testów od agentów lub komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono Magazyn wyników testu obciążenia. W obu przypadkach należy określić miejsce przechowywania wyników testu obciążenia przy użyciu okna **administrowanie kontrolerami testów** .|-   [instrukcje: wybieranie repozytorium wyników testu obciążenia](../test/how-to-select-a-load-test-results-repository.md)<br />-   [instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Usuwanie wyniku testu obciążenia z repozytorium:** Można usunąć wynik testu obciążenia z **Edytor testu obciążeniowego** przy użyciu okna dialogowego **otwórz i Zarządzaj wyniki testów ładowania** .|-   [: usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importuj i Eksportuj wyniki do repozytorium:** Można importować i eksportować wyniki testów obciążenia z **Edytor testu obciążeniowego**.|-   [instrukcje: Importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [instrukcje: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Zadania powiązane

[Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Można wyświetlić wyniki zarówno uruchomionego testu obciążenia, jak i zakończonego testu obciążenia za pomocą **analizatora testu obciążenia**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)