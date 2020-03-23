---
title: Integracja programu SQL Server z r
description: Visual Studio obsługuje tworzenie i uruchamianie zapytań SQL z języka R i możliwość języka R do pracy z procedurami przechowywanymi.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 10b5dfee629b5b6e67ab544ca0bdd905ed2a120a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888455"
---
# <a name="work-with-sql-server-and-r"></a>Praca z programami SQL Server i R

Doskonała obsługa programu Visual Studio dla programu SQL Server ułatwia analitykom danych pracę z bazami danych języka R i SQL za pomocą możliwości tworzenia i uruchamiania zapytań SQL oraz pracy z procedurami przechowywanymi.

> [!Note]
> Aby pracować razem z programami SQL i R, muszą być zainstalowane narzędzia SQL Server Data Tools:
> - Visual Studio 2017: uruchom instalator programu Visual Studio i wybierz obciążenie magazynowania i przetwarzania danych, które zawiera narzędzia SQL Server Data.
> - Visual Studio 2015: postępuj zgodnie z instrukcjami dotyczącymi [narzędzia pobierania danych programu SQL Server](/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | [Obejrzyj klip wideo (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) omówienie programu SQL Server i R (3m 03s). |

## <a name="create-and-run-sql-queries"></a>Tworzenie i uruchamianie zapytań SQL

RTVS obsługuje dodawanie zapytań SQL do projektów języka R, co pozwala iteracyjne tworzenie zapytań SQL w osobnym kontekście, dopóki nie uzyskasz wyników, których szukasz.

Aby dodać plik zapytania SQL, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierz pozycję **Dodaj** > **nowy element**i wybierz typ pliku **kwerendy SQL:**

![Dodawanie elementu kwerendy SQL do projektu](media/sql-add-item.png)

To polecenie otwiera plik w edytorze Transact-SQL programu Visual Studio, który zapewnia pełną pozycję IntelliSense dla języka SQL i możliwość uruchamiania zapytań. Aby te funkcje działały, musisz połączyć się z bazą danych za pomocą przycisku połącz na pasku narzędzi edytora lub spróbować uruchomić kwerendę (**Ctrl**+**Shift**+**E**, która działa również na zaznaczeniu). Tak czy inaczej wywołuje okno dialogowe połączenia:

![Okno dialogowe połączenie SQL](media/sql-connection-dialog.png)

Po nawiązaniu połączenia można uruchamiać kwerendy i wyświetlać wyniki:

![Wyniki kwerendy okna SQL](media/sql-query-results.png)

Edytor Transact-SQL obsługuje wiele innych funkcji, takich jak wyświetlanie planu wykonania kwerendy i debugera kwerendy.
Aby uzyskać więcej informacji, zobacz [Edytowanie i wykonywanie skryptów za pomocą edytora Transact-SQL](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Praca z procedurami przechowywanymi w programie SQL Server

[Usługi SQL Server R](/sql/advanced-analytics/r/sql-server-r-services) Services (SQL Server 2016 i nowsze) umożliwiają osadzanie i uruchamianie kodu języka R z procedury składowanej T-SQL. Można uruchomić kod języka R na komputerze z programu SQL Server, działać na danych zwróconych z kwerendy SQL i wygenerować zestaw wyników SQL, który może być przetwarzany przez dalsze SQL lub zwracany do klienta.

RTVS upraszcza nieporęczny i podatny na błędy proces łączenia kodu SQL i R wewnątrz pojedynczej instrukcji SQL, zgodnie z opisem w następujących sekcjach:

- [Dodawanie połączenia z bazą danych](#add-a-database-connection)
- [Pisanie i testowanie procedury przechowywanej sql](#write-and-test-a-sql-stored-procedure)
- [Publikowanie procedury przechowywanej sql](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | [Obejrzyj film (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) przegląd procedur przechowywanych w języku R i SQL (6 m 09s). |

### <a name="add-a-database-connection"></a>Dodawanie połączenia z bazą danych

1. Wybierz polecenie R Tools Data Add Database Connection to bring up the **Connection Properties dialogowe** **.Select R Tools** > **Data** > **Add Database Connection** to bring up the Connection Properties dialog. W tym miejscu należy określić nazwę źródła danych (SQL Server w tym przypadku), nazwę serwera, tryb uwierzytelniania i nazwę bazy danych. Wybierz **opcję Testuj połączenie,** aby zweryfikować dane wejściowe przed zamknięciem okna dialogowego.

    ![Okno dialogowe połączenia SQL](media/sql-connection-string-dialog.png)

1. Po wybraniu **przycisku OK** z prawidłowym połączeniem `dbConnection` program Visual Studio generuje ciąg połączenia o nazwie w nowych *ustawieniach. R.* RTVS automatycznie źródła (uruchamia) ten plik, dzięki czemu można natychmiast użyć połączenia ze skryptów R:

![Plik Ustawienia SQL.R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Pisanie i testowanie procedury przechowywanej sql

Aby dodać nową procedurę składowaną SQL, kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj** > **nowy element,** wybierz pozycję Procedura **przechowywana SQL z r** z listy szablonów, nadaj plikowi nazwę i wybierz przycisk **OK**. Domyślną nazwa pliku to *SqlSProc.R*; dla ułatwienia odczytu, nazwa pliku *StoredProcedure.R* jest używany w pozostałej części tej sekcji. Jeśli masz wiele procedur przechowywanych, każdy plik musi mieć unikatową nazwę pliku.

RTVS tworzy trzy pliki dla procedury składowanej: an *. R* dla kodu R, a *. Query.sql* dla kodu SQL i *. Plik template.sql,* który łączy te dwa elementy. Oni dwa ostatnie pojawiają się w Eksploratorze rozwiązań jako dzieci *. R* plik:

![Rozszerzony widok rozszerzonego programu SQL w Eksploratorze rozwiązań z r](media/sql-solution-explorer-expanded.png)

W *. R* file *(StoredProcedure.R* this example) to miejsce, w którym piszesz kod R. Domyślna zawartość to:

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

Po prostu powiedział, że kod `InputDataSet` odbiera ramki `OutputDataSet`danych R wywoływane i zwraca jego wyniki w , z kodem szablonu tylko kopiowanie danych wejściowych do danych wyjściowych.

> [!Note]
> Nazwy tych ramek danych są `@input_data_1_name` kontrolowane `@output_data_1_name` przez i parametry `sp_execute_external_script` w wywołaniu procedury składowanej systemu. Aby uzyskać więcej informacji na temat projektu tej konwencji wywoływania i kilka przykładów jej użycia, zobacz [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Inny wygenerowany kod (w komentarzach) zawiera mały skrypt testowy, który używa [pakietu RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) do przesyłania instrukcji SQL do programu SQL Server, uruchamiania go i pobierania jego wyników ustawionych jako ramka danych R. Można odkomentować ten kod testu, aby interaktywnie napisać kod języka R względem zestawu wyników, który można uzyskać z programu SQL Server.

W *. Query.sql* file (*StoredProcedure.Query.sql* w tym przykładzie) jest miejscem, w `InputDataSet`którym piszesz i testujesz kwerendę SQL, która generuje dane dla . Dzięki temu plikowi *.sql* edytor udostępnia ci wszystkie zwykłe funkcje Transact-SQL.

Gdy jesteś zadowolony z kodu SQL, zintegruj go z kodem R, przeciągając plik *.sql* do otwartego edytora *dla . R.* Na poniższej ilustracji *storedprocedure.Query.sql* został przeciągnięty do punktu w *StoredProcedure.R* po przecinku w `sqlQuery(channel, )`:

![Odczytywanie pliku SQL do zmiennej ciągu R](media/sql-reference-sql-file-from-r.png)

Jak widać, ten prosty krok automatycznie generuje kod R, aby otworzyć plik *.sql,* odczytać jego zawartość w ciągu i przekazać go do pakietu RODBC, aby wysłać go do programu SQL Server.

Teraz można interaktywnie napisać kod Języka `InputDataSet` R, który manipuluje ramki danych zgodnie z potrzebami. Pamiętaj, że możesz po prostu wybrać kod R w edytorze i wysłać go do [interaktywnego okna,](interactive-repl-for-r-in-visual-studio.md) naciskając **klawisz Ctrl**+**Enter**.

W *. Plik template.sql* *(StoredProcedure.Template.sql* w tym przykładzie), na koniec zawiera szablon do generowania procedury przechowywanej SQL:

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

- Symbol `_RCODE_` zastępczy jest zastępowany zawartością pliku *. R* (na przykład *StoredProcedure.R*).
- Symbol `_INPUT_QUERY_` zastępczy jest zastępowany zawartością pliku *. Query.sql* (na przykład *StoredProcedure.Query.sql*).
- Edytuj `WITH RESULT SETS` klauzulę, aby opisać schemat zestawu wyników zwrócony z procedury składowanej. W szczególności zidentyfikować kolumny `OutputDataSet` z dataframe, które chcesz powrócić do wywołującego procedury składowanej.

Na przykład dla następującej kwerendy:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Aby określić typy danych wartości zwracanych, należy użyć następującej `WITH RESULT SETS` klauzuli:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikowanie procedury przechowywanej sql

1. Wybierz polecenie menu **R Narzędzia Publikowania** > **danych** > **za pomocą opcji.**
1. W wyświetlonym oknie dialogowym zmień **polecenie Publikuj na:** na **Baza danych**, określ obiekt docelowy, wybierz pozycję **Publikuj**i RTVS tworzy i publikuje procedurę składowaną:

    ![Okno dialogowe Publikowania procedury składowanej](media/sql-publish-with-options.png)

1. Aby opublikować wszystkie procedury przechowywane w projekcie, można użyć polecenia **R Tools** > **Data** > **Publish Stored Procedures,** które jest również dostępne po kliknięciu prawym przyciskiem myszy projektu w Eksploratorze rozwiązań.

> [!Tip]
> Jeśli w programie Visual Studio otwarto Eksplorator obiektów programu SQL Server, opublikowana procedura składowana jest wyświetlana w folderze**Procedury przechowywane** **programowalności** > bazy danych. Można go również uruchomić w Eksploratorze obiektów, klikając prawym przyciskiem myszy i wybierając **polecenie Wykonaj procedurę**lub wywołując ją interaktywnie z okna kwerendy *.sql.*
