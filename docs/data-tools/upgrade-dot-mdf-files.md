---
title: Uaktualnianie plików mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 334898fe9bb6ec5a7dcd84e081f99994e18ccb89
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091684"
---
# <a name="upgrade-mdf-files"></a>Uaktualnianie plików mdf

W tym temacie opisano opcje uaktualniania pliku bazy danych (*.mdf*) po Zainstaluj nowszą wersję programu Visual Studio. Zawiera on instrukcje w celu uwzględnienia poniższych zadań:

- Uaktualnić plik bazy danych w celu użycia nowszej wersji programu SQL Server Express LocalDB

- Uaktualnić plik bazy danych w celu użycia nowszej wersji programu SQL Server Express

- Praca z plikiem bazy danych w programie Visual Studio przy zachowaniu zgodność ze starszej wersji programu SQL Server Express lub LocalDB

- Wprowadź programu SQL Server Express domyślny aparat bazy danych

Można użyć programu Visual Studio, aby otworzyć projekt, który zawiera plik bazy danych (*.mdf*) który został utworzony przy użyciu starszej wersji programu SQL Server Express lub LocalDB. Aby kontynuować tworzenie projektu w programie Visual Studio, konieczne jest posiadanie tej wersji programu SQL Server Express lub LocalDB zainstalowane na tym samym komputerze co program Visual Studio lub musisz uaktualnić plik bazy danych. W przypadku uaktualniania pliku bazy danych nie można uzyskać do niego dostęp przy użyciu starszych wersji programu SQL Server Express lub LocalDB.

Użytkownik może również monit uaktualnić plik bazy danych, który został utworzony za pomocą starszej wersji programu SQL Server Express lub LocalDB, jeśli wersja pliku nie jest zgodna z wystąpieniem programu SQL Server Express lub LocalDB, który jest aktualnie zainstalowany. Aby rozwiązać ten problem, Visual Studio wyświetli monit o uaktualnienie pliku.

> [!IMPORTANT]
> Firma Microsoft zaleca tworzenie kopii zapasowej plików bazy danych przed przystąpieniem do uaktualniania.

> [!WARNING]
> Jeśli uaktualniasz *.mdf* plik, który został utworzony w programie LocalDB 2014 (V12) 32-bitowej do LocalDB 2016 (V13) lub nowszego, nie można ponownie otworzyć plik w 32-bitowej wersji programu LocalDB.

Przed rozpoczęciem uaktualnienia bazy danych należy wziąć pod uwagę następujące kryteria:

- Nie uaktualniaj, jeśli użytkownik chce pracować nad projektem w starszej wersji i nowszej wersji programu Visual Studio.

- Nie uaktualnienie aplikacji, które będą używane w środowiskach korzystających z programu SQL Server Express zamiast LocalDB.

- Nie uaktualniaj Jeśli aplikacja korzysta z połączenia zdalnego, ponieważ LocalDB nie akceptuje tych postanowień.

- Nie uaktualniaj, jeśli aplikacja opiera się na Internet Information Services (IIS).

- Rozważ uaktualnienie, jeśli chcesz przetestować aplikacje baz danych w środowisku piaskownicy, ale nie chcesz administrować bazy danych.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Aby uaktualnić plik bazy danych, aby użyć wersji LocalDB

1. W **Eksploratora serwera**, wybierz opcję **Połącz z bazą danych** przycisku.

2. W **Dodaj połączenie** okna dialogowego wprowadź następujące informacje:

    - **Źródło danych**: `Microsoft SQL Server (SqlClient)`

    - **Nazwa serwera**:

        - Aby użyć domyślnej wersji: `(localdb)\MSSQLLocalDB`.  Ta wartość umożliwi określenie ProjectV12 lub ProjectV13, w zależności od wersji programu Visual Studio jest zainstalowany i utworzenia pierwszego wystąpienia LocalDB. **MSSQLLocalDB** w węźle **Eksplorator obiektów SQL Server** pokazuje, w której wersji wskazuje.

        - Aby użyć określonej wersji: `(localdb)\ProjectsV12` lub `(localdb)\ProjectsV13`, w których wersja V12 jest LocalDB 2014 i V13 jest LocalDB 2016.

    - **Dołącz plik bazy danych**: Ścieżka fizyczna podstawową *.mdf* pliku.

    - **Nazwa logiczna**: Nazwa, którą chcesz korzystać z plikiem.

3. Wybierz przycisk **OK**.

4. Po wyświetleniu monitu wybierz **tak** przycisk, aby uaktualnić plik.

    Baza danych została uaktualniona, jest dołączony do aparatu bazy danych LocalDB i nie będzie już zgodna ze starszą wersją programu LocalDB.

Można również zmodyfikować połączenie programu SQL Server Express do użycia LocalDB, otwierając menu skrótów dla połączenia, a następnie wybierając **modyfikowanie połączenia**. W **modyfikowanie połączenia** okna dialogowego pole, Zmień nazwę serwera aby `(LocalDB)\MSSQLLocalDB`. W **zaawansowane właściwości** okna dialogowego pole, upewnij się, że **wystąpienia użytkownika** ustawiono **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Aby uaktualnić plik bazy danych, aby użyć wersji programu SQL Server Express

1. W menu skrótów dla połączenia z bazą danych, wybierz **modyfikowanie połączenia**.

2. W **modyfikowanie połączenia** okno dialogowe, wybierz opcję **zaawansowane** przycisku.

3. W **zaawansowane właściwości** okno dialogowe, wybierz opcję **OK** przycisk bez zmiany nazwy serwera.

    Plik bazy danych została uaktualniona do odpowiada bieżącej wersji programu SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Aby pracować z bazą danych w programie Visual Studio, ale zachować zgodność z programu SQL Server Express

- W programie Visual Studio Otwórz projekt bez jego uaktualnieniem.

    - Aby uruchomić projekt, wybierz **F5** klucza.

    - Aby edytować bazy danych, otwórz *.mdf* w pliku **Eksploratora rozwiązań**i rozwiń węzeł w **Eksploratora serwera** do pracy z bazą danych.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Aby program SQL Server Express domyślny aparat bazy danych

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. W **opcje** okna dialogowego rozwiń **narzędzia graficzne bazy danych** opcje, a następnie wybierz **połączeń danych**.

3. W **nazwa wystąpienia serwera SQL** tekst pola, określ nazwę wystąpienia programu SQL Server Express lub LocalDB, którego chcesz używać. Jeśli nie jest nazwane wystąpienie, określ `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4. Wybierz przycisk **OK**.

    SQL Server Express będzie domyślny aparat bazy danych dla aplikacji.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](accessing-data-in-visual-studio.md)