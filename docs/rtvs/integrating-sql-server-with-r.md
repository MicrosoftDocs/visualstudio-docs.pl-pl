---
title: Integracja programu SQL Server przy użyciu języka R
description: Program Visual Studio obsługuje tworzenie i uruchamianie zapytań SQL z języka R i możliwości dla języka R do pracy za pomocą procedur składowanych.
ms.date: 06/25/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: fbe0144985355b30d92430d8b0a923987b7bf111
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936154"
---
# <a name="work-with-sql-server-and-r"></a>Praca z programu SQL Server i R

Niezrównane możliwości obsługi programu Visual Studio dla programu SQL Server pomaga analitykom pracy z języków R i SQL bazami danych za pośrednictwem możliwość tworzenia i uruchamiania zapytań SQL i Praca z procedurami składowanymi danych.

> [!Note]
> Współdziałanie z języków SQL i języka R, konieczne jest posiadanie programu SQL Server Data Tools zainstalowane:
> - Visual Studio 2017: Uruchom Instalatora programu Visual Studio i wybierz magazyn danych i przetwarzania obciążeń, w tym SQL Server Data tools.
> - Visual Studio 2015: postępuj zgodnie z instrukcjami [pobieranie programu SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (w witrynie youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) Omówienie programu SQL Server i R (3 m 03s). |

## <a name="create-and-run-sql-queries"></a>Tworzenie i uruchamianie zapytań SQL

RTVS obsługuje dodawanie zapytania SQL do projektów języka R, co umożliwia iteracyjne tworzenie zapytań SQL w kontekście oddzielne aż otrzymasz wyników, których szukasz.

Aby dodać plik zapytania SQL, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierz pozycję **Dodaj** > **nowy element**i wybierz **zapytania SQL** typ pliku:

![Dodawanie elementu zapytania SQL do projektu](media/sql-add-item.png)

To polecenie otwiera plik w edytorze języka Transact-SQL programu Visual Studio, co zapewnia pełną obsługą technologii IntelliSense dla języków SQL i możliwość uruchamiania zapytań. Te funkcje działają, musisz nawiązać połączenie z bazą danych, używając przycisku Połącz na pasku narzędzi edytora lub spróbuj uruchomić zapytanie (**Ctrl**+**Shift**+**E** , który działa również na wybranych). W obu przypadkach Wyświetla okno dialogowe połączenia:

![Okno dialogowe połączenia SQL](media/sql-connection-dialog.png)

Po nawiązaniu połączenia można uruchamiać zapytania i wyświetlać wyniki:

![Wyniki zapytania w oknie SQL](media/sql-query-results.png)

Edytor języka Transact-SQL obsługuje wiele innych funkcji, takich jak wyświetlanie plan wykonania zapytania i debuger zapytania.
Aby uzyskać więcej informacji, zobacz [Użyj edytora języka Transact-SQL do edycji i wykonywania skryptów](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Praca z procedur składowanych serwera SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) procedury składowanej (SQL Server 2016 lub nowszy) umożliwia osadzanie i uruchamianie kodu języka R z języka T-SQL. Można uruchomić kod R na komputerze programu SQL Server, operować na danych zwrócone przez zapytanie SQL i wygenerować zestaw wyników SQL, które mogą być przetwarzane przez dalsze SQL lub zwracana do klienta.

RTVS upraszcza ten proces, w przeciwnym razie niewygodna i obarczone ryzykiem błędów, łączenia kodu SQL i języka R w pojedynczej instrukcji SQL, zgodnie z opisem w poniższych sekcjach:

- [Dodawanie połączenia z bazą danych](#add-a-database-connection)
- [Pisanie i testowanie procedury przechowywanej SQL](#write-and-test-a-sql-stored-procedure)
- [Publikuj procedury składowane SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (w witrynie youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) omówienie języka R i SQL przechowywanych procedur (6 mln 09s). |

### <a name="add-a-database-connection"></a>Dodawanie połączenia z bazą danych

1. Wybierz **R Tools** > **danych** > **Dodaj połączenie z bazą danych** Aby przywołać **właściwości połączenia** okno dialogowe. W tym miejscu należy określić nazwę źródła danych (SQL Server, w tym przypadku), nazwę serwera, tryb uwierzytelniania i nazwę bazy danych. Wybierz **Testuj połączenie** się przed zamknięciem okna dialogowego Sprawdź dane wejściowe.

    ![Okno dialogowe połączenia SQL](media/sql-connection-string-dialog.png)

1. Po wybraniu **OK** przy użyciu prawidłowego połączenia programu Visual Studio generuje ciąg połączenia o nazwie `dbConnection` w nowym *ustawienia. R* pliku. RTVS automatycznie źródeł (działa) tego pliku, dzięki czemu można natychmiast użyć połączenia ze skryptów języka R:

![Plik SQL Settings.R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Pisanie i testowanie procedury przechowywanej SQL

Aby dodać nowe procedury składowanej SQL, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj** > **nowy element**, wybierz opcję **procedury składowanej SQL przy użyciu języka R** z listy szablonów, Nadaj plikowi nazwę, a następnie wybierz pozycję **OK**. Domyślna nazwa pliku jest *SqlSProc.R*; w celu ułatwienia odczytu, nazwa_pliku *StoredProcedure.R* jest używana w pozostałej części tej sekcji. Jeśli masz wiele procedur składowanych, każdy plik musi mieć unikatową nazwę pliku.

RTVS tworzy trzy pliki dla procedury składowanej: *. R* pliku w kodzie R *. Query.SQL* w pliku kodu SQL i *. Template.SQL* pliku, który łączy dwie. Ostatnie dwa są wyświetlane w Eksploratorze rozwiązań jako elementy podrzędne są *. R* pliku:

![Eksplorator rozwiązań rozwinięty widok procedury składowanej SQL przy użyciu języka R](media/sql-solution-explorer-expanded.png)

*. R* pliku (*StoredProcedure.R* w tym przykładzie) pisze się kod R. Wartość domyślna to:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Był wyświetlany kod odbiera R temu ramka danych jest nazywane `InputDataSet` i zwraca wyniki w `OutputDataSet`, przy użyciu kodu szablonu jedynie kopiowania danych wejściowych w danych wyjściowych.

> [!Note]
> Nazwy te elementy dataframe są kontrolowane przez `@input_data_1_name` i `@output_data_1_name` parametrów w wywołaniu `sp_execute_external_script` systemowej procedury składowanej. Aby uzyskać szczegółowe informacje na temat projektowania niniejszej konwencji wywoływania oraz przykłady jego użycia, zobacz [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Wygenerowany kod (w komentarzach) zawiera skrypt mały test, który używa [pakietu RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) przesyłać instrukcję SQL do programu SQL Server, należy ją uruchomić, a pobieranie jej zestawu wyników jako ramkę danych języka R. Można komentarz ten kod testu, do interaktywnego pisania kodu języka R względem wynik zestawu uzyskiwanie programu SQL Server.

*. Query.SQL* pliku (*StoredProcedure.Query.sql* w tym przykładzie) jest gdzie pisanie i testowanie zapytanie SQL, które generuje dane w celu `InputDataSet`. Dzięki temu *.sql* pliku edytora zapewnia wszystkie funkcje języka Transact-SQL zwykle do Ciebie.

Po zakończeniu kod SQL zintegrować ją z kodem języka R, przeciągając *.sql* pliku na Otwórz edytor dla *. R* pliku. Na ilustracji poniżej *StoredProcedure.Query.sql* zostało przeciągnięte do punktu w *StoredProcedure.R* po przecinku w `sqlQuery(channel, )`:

![Podczas odczytywania pliku SQL do zmiennej ciągu języka R](media/sql-reference-sql-file-from-r.png)

Jak widać, w tym kroku proste automatycznie generuje kod R, aby otworzyć *.sql* pliku, odczytać jego zawartości w ciąg i przekazać go do pakietu RODBC, aby wysłać go do programu SQL Server.

Teraz możesz interaktywnie kod R zapisu, która manipuluje `InputDataSet` ramkę danych zgodnie z potrzebami. Należy pamiętać, że można po prostu wybierz kod języka R w edytorze i wyślij go do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) , naciskając klawisz **Ctrl**+**Enter**.

*. Template.SQL* pliku (*StoredProcedure.Template.sql* w tym przykładzie), na koniec zawiera szablon do wygenerowania procedury składowanej SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` Symbol zastępczy jest zastępowany przez zawartość *. R* pliku (na przykład *StoredProcedure.R*).
- `_INPUT_QUERY_` Symbol zastępczy jest zastępowany przez zawartość *. Query.SQL* pliku (na przykład *StoredProcedure.Query.sql*).
- Edytuj `WITH RESULT SETS` klauzuli do opisania schematu zestawu zwrócone z procedury składowanej wyników. Precyzyjnego identyfikowania kolumny z `OutputDataSet` ramkę danych, które mają być zwracane do obiektu wywołującego procedurę składowaną.

Na przykład poniższe zapytanie:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Należy użyć następujących `WITH RESULT SETS` klauzulę, aby określić typy danych wartości zwracane:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikuj procedury składowane SQL

1. Wybierz **R Tools** > **danych** > **opcji publikowania z** polecenia menu.
1. W wyświetlonym oknie dialogowym Zmienianie **publikowania:** do **bazy danych**, określ cel, wybierz **Publikuj**, i RTVS kompilacje i publikuje procedura składowana:

    ![Procedura składowana okno dialogowe publikowanie](media/sql-publish-with-options.png)

1. Aby opublikować wszystkie procedury składowane w projekcie, można użyć **R Tools** > **danych** > **publikowania procedur składowanych** polecenia, które jest również dostępne po kliknięciu prawym przyciskiem myszy projekt w Eksploratorze rozwiązań.

> [!Tip]
> Jeśli masz Eksplorator obiektów SQL Server, Otwórz w programie Visual Studio, Twoja procedura składowana opublikowanych pojawia się w **programowania** > **procedur składowanych** folderu bazy danych. Można również uruchomić go w Eksploratorze obiektów kliknij prawym przyciskiem myszy i wybierając **wykonanie procedury**, lub przez wywołanie interaktywnie z *.sql* okno zapytania.
