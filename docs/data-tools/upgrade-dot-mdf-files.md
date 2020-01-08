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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 195cab863554bc60478df4e80319eab80124140a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586097"
---
# <a name="upgrade-mdf-files"></a>Uaktualnianie plików mdf

W tym temacie opisano opcje uaktualniania pliku bazy danych ( *. mdf*) po zainstalowaniu nowszej wersji programu Visual Studio. Zawiera instrukcje dotyczące następujących zadań:

- Uaktualnij plik bazy danych, aby korzystać z nowszej wersji programu SQL Server Express LocalDB

- Uaktualnij plik bazy danych, aby korzystać z nowszej wersji SQL Server Express

- Pracuj z plikiem bazy danych w programie Visual Studio, ale zachowaj zgodność ze starszą wersją SQL Server Express lub LocalDB

- Uczyń SQL Server Express domyślnym aparatem bazy danych

Możesz użyć programu Visual Studio, aby otworzyć projekt zawierający plik bazy danych ( *. mdf*), który został utworzony przy użyciu starszej wersji programu SQL Server Express lub LocalDB. Aby jednak kontynuować opracowywanie projektu w programie Visual Studio, należy zainstalować tę wersję programu SQL Server Express lub LocalDB na tym samym komputerze co program Visual Studio lub uaktualnić plik bazy danych. Jeśli uaktualniasz plik bazy danych, nie będzie można uzyskać do niego dostępu przy użyciu starszych wersji programu SQL Server Express lub LocalDB.

Może również pojawić się monit o uaktualnienie pliku bazy danych, który został utworzony za pomocą wcześniejszej wersji programu SQL Server Express lub LocalDB, jeśli wersja pliku nie jest zgodna z aktualnie zainstalowanym wystąpieniem SQL Server Express lub LocalDB. Aby rozwiązać ten problem, program Visual Studio wyświetli monit o uaktualnienie pliku.

> [!IMPORTANT]
> Zalecamy utworzenie kopii zapasowej pliku bazy danych przed jego uaktualnieniem.

> [!WARNING]
> W przypadku uaktualnienia pliku *MDF* , który został utworzony w LocalDB 2014 (V12) 32 bit do LocalDB 2016 (V13) lub nowszego, nie będzie można ponownie otworzyć pliku w 32-bitowej wersji programu LocalDB.

Przed uaktualnieniem bazy danych należy wziąć pod uwagę następujące kryteria:

- Nie uaktualniaj, jeśli chcesz korzystać z projektu w starszej wersji i nowszej wersji programu Visual Studio.

- Nie uaktualniaj, jeśli aplikacja będzie używana w środowiskach, które używają SQL Server Express, a nie LocalDB.

- Nie uaktualniaj, jeśli aplikacja używa połączeń zdalnych, ponieważ LocalDB nie akceptuje ich.

- Nie uaktualniaj, jeśli aplikacja korzysta z Internet Information Services (IIS).

- Rozważ uaktualnienie, jeśli chcesz przetestować aplikacje bazy danych w środowisku piaskownicy, ale nie chcesz administrować bazą danych.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Aby uaktualnić plik bazy danych w celu użycia wersji LocalDB

1. W **Eksplorator serwera**wybierz przycisk **Połącz z bazą danych** .

2. W oknie dialogowym **Dodawanie połączenia** podaj następujące informacje:

    - **Źródło danych**: `Microsoft SQL Server (SqlClient)`

    - **Server Name** (Nazwa serwera):

        - Aby użyć domyślnej wersji: `(localdb)\MSSQLLocalDB`.  Spowoduje to określenie opcji ProjectV12 lub ProjectV13, w zależności od zainstalowanej wersji programu Visual Studio i utworzenia pierwszego wystąpienia LocalDB. Węzeł **MSSQLLocalDB** w **Eksplorator obiektów SQL Server** wskazuje, która wersja wskazuje.

        - Aby użyć określonej wersji: `(localdb)\ProjectsV12` lub `(localdb)\ProjectsV13`, gdzie V12 jest LocalDB 2014, a V13 to LocalDB 2016.

    - **Dołączanie pliku bazy danych**: Ścieżka fizyczna podstawowego pliku *. mdf* .

    - **Nazwa logiczna**: nazwa, która ma być używana z plikiem.

3. Wybierz przycisk **OK**.

4. Po wyświetleniu monitu wybierz przycisk **tak** , aby uaktualnić plik.

    Baza danych zostanie uaktualniona, jest dołączona do aparatu bazy danych LocalDB i nie jest już zgodna ze starszą wersją programu LocalDB.

Możesz również zmodyfikować połączenie SQL Server Express, aby użyć LocalDB, otwierając menu skrótów dla połączenia, a następnie wybierając pozycję **Modyfikuj połączenie**. W oknie dialogowym **modyfikowanie połączenia** Zmień wartość w polu Nazwa serwera na `(LocalDB)\MSSQLLocalDB`. W oknie dialogowym **Właściwości zaawansowane** upewnij się, że **wystąpienie użytkownika** ma wartość **Fałsz**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Aby uaktualnić plik bazy danych w celu użycia wersji SQL Server Express

1. W menu skrótów dla połączenia z bazą danych wybierz pozycję **Modyfikuj połączenie**.

2. W oknie dialogowym **modyfikowanie połączenia** wybierz przycisk **Zaawansowane** .

3. W oknie dialogowym **Właściwości zaawansowane** wybierz przycisk **OK** bez zmiany nazwy serwera.

    Plik bazy danych jest uaktualniany w celu dopasowania do bieżącej wersji SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Aby korzystać z bazy danych w programie Visual Studio, ale zachować zgodność z SQL Server Express

- W programie Visual Studio Otwórz projekt bez uaktualniania.

  - Aby uruchomić projekt, wybierz klawisz **F5** .

  - Aby edytować bazę danych, Otwórz plik *. mdf* w **Eksplorator rozwiązań**i rozwiń węzeł w **Eksplorator serwera** , aby współpracował z bazą danych.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Aby SQL Server Express domyślnego aparatu bazy danych

1. Na pasku menu wybierz pozycję **narzędzia** > **Opcje**.

2. W oknie dialogowym **Opcje** Rozwiń opcje **narzędzi bazy danych** , a następnie wybierz pozycję **połączenia danych**.

3. W polu tekstowym **Nazwa wystąpienia SQL Server** Określ nazwę wystąpienia SQL Server Express lub LocalDB, którego chcesz użyć. Jeśli wystąpienie nie ma nazwy, określ `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4. Wybierz przycisk **OK**.

    SQL Server Express będzie domyślnym aparatem bazy danych aplikacji.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](accessing-data-in-visual-studio.md)
