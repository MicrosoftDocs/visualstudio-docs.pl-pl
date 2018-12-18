---
title: Zarządzaj wynikami testu obciążeniowego
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0b2d030f375f67608fc6cf34ae108fed2ba54f5d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067119"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Zarządzaj wynikami testu obciążenia w repozytorium wyników testów obciążenia

Kiedy uruchamiasz testy obciążenia, wszystkie informacje zebrane podczas uruchomienia testu obciążenia mogą być przechowywane w *repozytorium wyników testów obciążenia*, która jest bazą danych SQL. Repozytorium wyników testu obciążenia zawiera dane licznika wydajności i wszelkie informacje o błędach zarejestrowane. Baza danych repozytorium wyników jest tworzona przez konfigurację dla kontrolerów, lub tworzona automatycznie przy pierwszym lokalnym uruchomieniu testu obciążenia. Do uruchamiania lokalnego baza danych zostanie utworzony automatycznie Jeśli schemat testu obciążenia nie jest obecny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli zmodyfikujesz parametry połączenia repozytorium wyników kontrolera do korzystania z innego serwera, nowy serwer musi mieć *loadtestresultsrepository.sql* skrypt uruchamiany w celu utworzenia schematu.

Program Visual Studio Enterprise zapewnia nazwane zestawy liczników, które zbierają wspólne liczniki wydajności bazujące na technologii. Te zestawy są przydatne podczas analizowania serwera IIS, serwera ASP.NET lub programu SQL server. Wszystkie dane zebrane z zestawami licznika są przechowywane w repozytorium wyników testu obciążenia.

> [!IMPORTANT]
> Istnieje różnica między zestawem liczników a danych licznika wydajności. Zestaw liczników to metadane. Definiuje grupę liczników wydajności, które powinny być zbierane z komputera, na którym wykonuje określoną rolę, takich jak usługi IIS lub programu SQL Server. Zestaw liczników jest częścią definicji testu obciążenia. Dane licznika wydajności są zbierane na podstawie zbiory liczników, mapowania licznika Ustaw na określonym komputerze oraz częstotliwość próbkowania.

## <a name="sql-server-versions"></a>Wersje programu SQL Server

 Aby użyć testów obciążenia, można użyć programu SQL Server Express LocalDB, który jest instalowany z programem Visual Studio. Jest domyślny serwer bazy danych dla testów obciążenia (w tym integracji programu Microsoft Excel). SQL Server Express LocalDB to tryb wykonywania programu SQL Server Express, który jest przeznaczony dla twórców programu. Instalacja programu SQL Server Express LocalDB kopiuje minimalny zestaw plików niezbędnych do uruchomienia aparatu bazy danych programu SQL Server.

 Jeśli zespół oczekuje potrzeb duże bazy danych lub projekty wykraczają poza możliwości programu SQL Server Express LocalDB, należy rozważyć uaktualnienie do programu SQL Express lub pełnej wersji programu SQL Server w celu zapewnienia dalszego skalowania. W przypadku uaktualniania programu SQL Server pliki MDF i LDF dla programu SQL Server Express LocalDB są przechowywane w folderze profilu użytkownika. Te pliki mogą służyć do importowania bazy danych testów obciążeniowych do programu SQL Server Express lub SQL Server.

## <a name="load-test-results-store-considerations"></a>Uwagi dotyczące przechowywania wyników testów obciążenia

 Po zainstalowaniu programu Visual Studio Enterprise, Magazyn wyników testu obciążenia skonfigurowano do korzystania z wystąpienia programu SQL Express, który jest zainstalowany na komputerze. Program SQL Express jest ograniczony do wykorzystywania maksymalnie 4 GB miejsca na dysku. Po uruchomieniu wielu testów obciążenia w długim okresie czasu, należy rozważyć skonfigurowanie magazynu wyników testów obciążeń do użycia wystąpienia pełnego produktu SQL Server, jeśli jest dostępny.

## <a name="load-test-analyzer-tasks"></a>Zadania analizatora testu obciążenia

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Konfigurowanie testu obciążeniowego repozytorium wyników:** możesz skonfigurować repozytorium wyników testu obciążenia w bazie danych SQL. **Uwaga:** po zainstalowaniu kontrolera testów można również tworzyć repozytorium testu obciążenia. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).||
|**Zaznaczanie i wyświetlanie repozytorium wyników:** możesz wybrać repozytorium określonych wyników. Nie jesteś ograniczony do magazynu wyników lokalnych. Często testy obciążenia są uruchamiane na zbiorze zdalnym komputerów agentów. Wyniki testów z agentów lub z komputera lokalnego można zapisać na dowolnym serwerze SQL, na którym utworzono Magazyn wyników testu obciążenia. W obu przypadkach należy wskazać, gdzie przechowywać wyniki testu obciążenia przy użyciu **Administrowanie kontrolerami testów** okna.|-   [Porady: Wybieranie repozytorium wyników testu obciążenia](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Porady: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)|
|**Usuwanie wyników testu obciążenia z repozytorium:** można usunąć wyniku testu obciążeniowego z **edytora testu obciążenia** przy użyciu **Otwórz i Zarządzaj wynikami testu obciążenia** okno dialogowe.|-   [Porady: z wynikami testów obciążeniowych usunięcia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Import i eksport wyników do repozytorium:** można importować i eksportować wyniki testów obciążenia z **edytora testu obciążenia**.|-   [Porady: Importuj wyniki testu obciążenia z repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Porady: z wynikami testów obciążeniowych eksportu z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Zadania powiązane

 [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

 Można wyświetlić wyniki odbywającego się testu obciążenia i zakończonego testu obciążenia przy użyciu **analizatora testu obciążenia**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)