---
title: Integrowanie SQL Server z językiem R
description: Program Visual Studio obsługuje tworzenie i uruchamianie zapytań SQL z języka R oraz możliwość pracy z procedurami przechowywanymi w języku R.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: c0aedbccdb82bd91fe201a23b6201a3cdd7db283
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908686"
---
# <a name="work-with-sql-server-and-r"></a>Współpraca z SQL Server i R

Doskonałe wsparcie dla SQL Server programu Visual Studio ułatwia analitykom danych współpracę z bazami danych R i SQL przy użyciu możliwości tworzenia i uruchamiania zapytań SQL oraz pracy z procedurami składowanymi.

> [!Note]
> Aby współdziałać z językami SQL i R, musisz mieć zainstalowane narzędzia SQL Server Data Tools:
> - Visual Studio 2017: Uruchom Instalatora programu Visual Studio i wybierz obciążenie magazynu i przetwarzania danych, które zawiera SQL Server narzędzia do obsługi danych.
> - Visual Studio 2015: Postępuj zgodnie z instrukcjami dotyczącymi [pobierania SQL Server narzędzi danych](/sql/ssdt/download-sql-server-data-tools-ssdt).

:::row:::
    :::column:::
        ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj film")
    :::column-end:::
    :::column:::
        [Obejrzyj wideo (YouTube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) , aby zapoznać się z omówieniem SQL Server i R (3m 03s).
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>Tworzenie i uruchamianie zapytań SQL

RTVS obsługuje dodawanie zapytań SQL do projektów języka R, co pozwala na iteracyjne opracowywanie zapytań SQL w osobnym kontekście do momentu uzyskania szukanych wyników.

Aby dodać plik zapytania SQL, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, wybierz polecenie **Dodaj**  >  **nowy element**, a następnie wybierz typ pliku **zapytania SQL** :

![Dodaj element zapytania SQL do projektu](media/sql-add-item.png)

To polecenie otwiera plik w edytorze Transact-SQL programu Visual Studio, który zapewnia pełną technologię IntelliSense dla SQL i możliwość uruchamiania zapytań. Aby te funkcje działały, należy nawiązać połączenie z bazą danych za pomocą przycisku Połącz na pasku narzędzi edytora lub spróbować uruchomić zapytanie (**Ctrl** + **SHIFT** + **E**, które również działa na zaznaczeniu). W obu przypadkach zostanie wyświetlone okno dialogowe połączenia:

![Okno dialogowe połączenia SQL](media/sql-connection-dialog.png)

Po nawiązaniu połączenia można uruchamiać zapytania i wyświetlać wyniki:

![Wyniki zapytania okna SQL](media/sql-query-results.png)

Edytor języka Transact-SQL obsługuje różne inne funkcje, takie jak wyświetlanie planu wykonywania zapytania i debugera zapytań.
Aby uzyskać więcej informacji, zobacz [Używanie edytora Transact-SQL do edytowania i wykonywania skryptów](/previous-versions/sql/sql-server-data-tools/hh272706(v=vs.103)).

## <a name="work-with-sql-server-stored-procedures"></a>Współpraca z SQL Server procedurami składowanymi

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 i nowsze) umożliwia osadzenie i uruchomienie kodu języka R z procedury składowanej T-SQL. Można uruchomić kod języka R na komputerze SQL Server, korzystać z danych zwróconych z zapytania SQL i wygenerować zestaw wyników SQL, który może być przetwarzany przez dalsze instrukcje SQL lub zwracane do klienta.

RTVS upraszcza w inny sposób nieporęczny i podatne na błędy proces łączenia kodu SQL i języka R w ramach jednej instrukcji SQL, zgodnie z opisem w poniższych sekcjach:

- [Dodawanie połączenia z bazą danych](#add-a-database-connection)
- [Zapisywanie i testowanie procedury składowanej SQL](#write-and-test-a-sql-stored-procedure)
- [Publikowanie procedury składowanej SQL](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj film")
    :::column-end:::
    :::column:::
        [Obejrzyj wideo (YouTube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) , aby zapoznać się z omówieniem procedur składowanych R i SQL (6 min 09s).
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>Dodawanie połączenia z bazą danych

1. Wybierz pozycję **R Tools**  >  **dane**  >  **Dodaj połączenie z bazą danych** , aby wyświetlić okno dialogowe **Właściwości połączenia** . Tutaj należy określić nazwę źródła danych (SQL Server w tym przypadku), nazwę serwera, tryb uwierzytelniania i nazwę bazy danych. Wybierz pozycję **Testuj połączenie** , aby zweryfikować dane wejściowe przed zamknięciem okna dialogowego.

    ![Okno dialogowe połączenia SQL](media/sql-connection-string-dialog.png)

1. Po wybraniu **przycisku OK** z prawidłowym połączeniem program Visual Studio generuje parametry połączenia o nazwie `dbConnection` w nowych *ustawieniach. Plik języka R* . RTVS automatycznie źródła (uruchamia) ten plik, dzięki czemu możesz natychmiast użyć połączenia ze skryptów języka R:

![Plik ustawień SQL. R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Zapisywanie i testowanie procedury składowanej SQL

Aby dodać nową procedurę składowaną SQL, kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj**  >  **nowy element**, wybierz **procedurę składowaną SQL z** listą szablonów, Nadaj plikowi nazwę i wybierz polecenie **OK**. Domyślna nazwa pliku to *SqlSProc. R*; Aby ułatwić odczytywanie, nazwa pliku *StoredProcedure. R* jest używana w pozostałej części tej sekcji. Jeśli masz wiele procedur składowanych, każdy plik musi mieć unikatową nazwę pliku.

RTVS tworzy trzy pliki dla procedury składowanej: a *. Plik języka r* dla kodu języka r, a *. Plik Query. SQL* dla kodu SQL i *. Plik Template. SQL* , który łączy dwa. Te ostatnie dwa pojawiają się w Eksplorator rozwiązań jako elementy podrzędne *. Plik języka R* :

![Eksplorator rozwiązań rozszerzony widok procedury składowanej SQL przy użyciu języka R](media/sql-solution-explorer-expanded.png)

*. Plik r* (*StoredProcedure. R* w tym przykładzie) to miejsce, w którym można napisać kod w języku r. Zawartość domyślna to:

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

Po prostu kod otrzymuje ramkę języka R o nazwie `InputDataSet` i zwraca jej wyniki w `OutputDataSet` , z kodem szablonu wyłącznie kopiując dane wejściowe do danych wyjściowych.

> [!Note]
> Nazwy tych ramek danych są kontrolowane przez `@input_data_1_name` `@output_data_1_name` Parametry i w wywołaniu `sp_execute_external_script` procedury składowanej system. Aby uzyskać więcej informacji na temat projektowania konwencji wywoływania i niektórych przykładów użycia, zobacz [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Inny wygenerowany kod (w komentarzach) zawiera mały skrypt testowy, który używa [pakietu RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) do przesyłania instrukcji SQL w celu SQL Server, uruchamiania go i pobierania zestawu wyników jako ramki danych języka R. Możesz usunąć komentarz tego kodu testowego, aby interaktywnie napisać kod R względem zestawu wyników, który otrzymujesz z SQL Server.

*. Plik Query. SQL* (*StoredProcedure. Query. SQL* w tym przykładzie) to miejsce, w którym można napisać i przetestować zapytanie SQL, które generuje dane dla `InputDataSet` . Za pomocą tego pliku *SQL* , Edytor udostępnia wszystkie normalne funkcje języka Transact-SQL.

Gdy będziesz zadowolony z kodu SQL, Zintegruj go z kodem języka R, przeciągając plik *SQL* na otwarty Edytor dla *. Plik języka R* . Na poniższym obrazie *StoredProcedure. Query. SQL* został przeciągnięty do punktu w *StoredProcedure. R* po przecinku w `sqlQuery(channel, )` :

![Odczytywanie pliku SQL w zmiennej typu R](media/sql-reference-sql-file-from-r.png)

Jak widać, ten prosty krok automatycznie generuje kod języka R, aby otworzyć plik *SQL* , odczytać jego zawartość w postaci ciągu i przekazać go do pakietu RODBC w celu wysłania go do SQL Server.

Teraz możesz interaktywnie napisać kod języka R, który manipuluje `InputDataSet` ramką Dataframe. Pamiętaj, że po prostu możesz wybrać kod R w edytorze i wysłać go do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) , naciskając klawisz **Ctrl** + **Enter**.

*. Plik Template. SQL* (*StoredProcedure. Template. SQL* w tym przykładzie), finally zawiera szablon służący do generowania procedury składowanej SQL:

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

- `_RCODE_`Symbol zastępczy jest zastępowany przez zawartość *. Plik języka R* (na przykład *StoredProcedure. R*).
- `_INPUT_QUERY_`Symbol zastępczy jest zastępowany przez zawartość *. Query. SQL* — plik (na przykład *StoredProcedure. Query. SQL*).
- Edytuj `WITH RESULT SETS` klauzulę, aby opisać schemat zestawu wyników zwróconego z procedury składowanej. W tym celu Zidentyfikuj kolumny z `OutputDataSet` ramki danych, które chcesz zwrócić do obiektu wywołującego procedury składowanej.

Na przykład dla następującej kwerendy:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Poniższa `WITH RESULT SETS` klauzula służy do określania typów danych zwracanych wartości:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikowanie procedury składowanej SQL

1. Wybierz polecenie **R Tools**  >  **dane**  >  **publikacji z menu Opcje** .
1. W wyświetlonym oknie dialogowym Zmień pozycję **Publikuj na:** na **bazę danych**, określ cel, wybierz pozycję **Opublikuj**, a następnie RTVS kompiluje i publikuje procedurę składowaną:

    ![Okno dialogowe publikowania procedury składowanej](media/sql-publish-with-options.png)

1. Aby opublikować wszystkie procedury składowane w projekcie, można użyć polecenia Publikuj **Narzędzia** do  >  **publikowania danych** języka R  >   , które jest również dostępne po kliknięciu prawym przyciskiem myszy projektu w Eksplorator rozwiązań.

> [!Tip]
> Jeśli masz otwarty Eksplorator obiektów SQL Server w programie Visual Studio, opublikowana procedura składowana zostanie wyświetlona w  >  folderze **procedury składowane** programowalności bazy danych. Możesz również uruchomić ją z Eksplorator obiektów przez kliknięcie prawym przyciskiem myszy i wybranie polecenia **wykonaj procedurę** lub przez wywołanie go interaktywnie z okna zapytania *SQL* .