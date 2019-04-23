---
title: Uaktualnianie plików mdf | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 395e2a6233c1b6187d9089459cb8f267c4c3c904
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079911"
---
# <a name="upgrade-mdf-files"></a>Uaktualnianie plików mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano opcje uaktualniania pliku bazy danych (.mdf), po zainstalowaniu nowszą wersję programu Visual Studio. Zawiera on instrukcje w celu uwzględnienia poniższych zadań:  
  
- Uaktualnić plik bazy danych w celu użycia nowszej wersji programu SQL Server Express LocalDB  
  
- Uaktualnić plik bazy danych w celu użycia nowszej wersji programu SQL Server Express  
  
- Praca z plikiem bazy danych w programie Visual Studio przy zachowaniu zgodność ze starszej wersji programu SQL Server Express lub LocalDB  
  
- Wprowadź programu SQL Server Express domyślny aparat bazy danych  
  
  Aby otworzyć projekt, który zawiera plik bazy danych (.mdf), który został utworzony przy użyciu starszej wersji programu SQL Server Express lub LocalDB, można użyć programu Visual Studio. Aby kontynuować tworzenie projektu w programie Visual Studio, konieczne jest posiadanie tej wersji programu SQL Server Express lub LocalDB zainstalowane na tym samym komputerze co program Visual Studio lub musisz uaktualnić plik bazy danych. W przypadku uaktualniania pliku bazy danych nie można uzyskać do niego dostęp przy użyciu starszych wersji programu SQL Server Express lub LocalDB.  
  
  Użytkownik może również monit uaktualnić plik bazy danych, który został utworzony za pomocą starszej wersji programu SQL Server Express lub LocalDB, jeśli wersja pliku nie jest zgodna z wystąpieniem programu SQL Server Express lub LocalDB, który jest aktualnie zainstalowany. Aby rozwiązać ten problem, Visual Studio wyświetli monit o uaktualnienie pliku.  
  
> [!IMPORTANT]
>  Firma Microsoft zaleca tworzenie kopii zapasowej plików bazy danych przed przystąpieniem do uaktualniania.  
  
> [!WARNING]
>  Jeśli zaktualizujesz plik mdf, który został utworzony w programie LocalDB 2014 (V12) 32-bitowych do LocalDB 2016 (V13), nie można otworzyć go ponownie w 32-bitowej wersji programu LocalDB.  W wersji Update 2 LocalDB V13 jest tylko wersja 64-bitowa.  
  
 Przed rozpoczęciem uaktualnienia bazy danych należy wziąć pod uwagę następujące kryteria:  
  
- Nie uaktualniaj, jeśli użytkownik chce pracować nad projektem w starszej wersji i nowszej wersji programu Visual Studio.  
  
- Nie uaktualnienie aplikacji, które będą używane w środowiskach korzystających z programu SQL Server Express zamiast LocalDB.  
  
- Nie uaktualniaj Jeśli aplikacja korzysta z połączenia zdalnego, ponieważ LocalDB nie akceptuje tych postanowień.  
  
- Nie uaktualniaj, jeśli aplikacja opiera się na Internet Information Services (IIS).  
  
- Rozważ uaktualnienie, jeśli chcesz przetestować aplikacje baz danych w środowisku piaskownicy, ale nie chcesz administrować bazy danych.  
  
### <a name="to-upgrade-a-database-file"></a>Aby uaktualnić plik bazy danych  
  
1. W **Eksploratora serwera**, wybierz opcję **Połącz z bazą danych** przycisku.  
  
2. W **Dodaj połączenie** okna dialogowego wprowadź następujące informacje:  
  
   - **Źródło danych**: `Microsoft SQL Server (SqlClient)`  
  
   - **Nazwa serwera**:  
  
       - Aby użyć domyślnej wersji: `(localdb)\MSSQLLocalDB`.  Ta wartość umożliwi określenie ProjectV12 lub ProjectV13, w zależności od wersji programu Visual Studio jest zainstalowany i utworzenia pierwszego wystąpienia LocalDB. **MSSQLLocalDB** w węźle **Eksplorator obiektów SQL Server** pokazuje, w której wersji wskazuje.  
  
       - Aby użyć określonej wersji: `(localdb)\ProjectsV12` lub `(localdb)\ProjectsV13`, w których wersja V12 jest LocalDB 2014 i V13 jest LocalDB 2016.  
  
   - **Dołącz plik bazy danych**: Ścieżka fizyczna głównego pliku .mdf.  
  
   - **Nazwa logiczna**: Nazwa, którą chcesz korzystać z plikiem.  
  
3. Wybierz przycisk **OK**.  
  
4. Po wyświetleniu monitu wybierz **tak** przycisk, aby uaktualnić plik.  
  
   Baza danych została uaktualniona, jest dołączony do aparatu bazy danych LocalDB i nie będzie już zgodna ze starszą wersją programu LocalDB.  
  
   Można również zmodyfikować połączenie programu SQL Server Express do użycia LocalDB, otwierając menu skrótów dla połączenia, a następnie wybierając **modyfikowanie połączenia**. W **modyfikowanie połączenia** okna dialogowego pole, Zmień nazwę serwera aby `(LocalDB)\MSSQLLocalDB`. W **zaawansowane właściwości** okna dialogowego pole, upewnij się, że **wystąpienia użytkownika** ustawiono **False**.  
  
### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Aby uaktualnić do nowszej wersji programu SQL Server Express  
  
1. W menu skrótów dla połączenia z bazą danych, wybierz **modyfikowanie połączenia**.  
  
2. W **modyfikowanie połączenia** okno dialogowe, wybierz opcję **zaawansowane** przycisku.  
  
3. W **zaawansowane właściwości** okno dialogowe, wybierz opcję **OK** przycisk bez zmiany nazwy serwera.  
  
   Plik bazy danych została uaktualniona do odpowiada bieżącej wersji programu SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Aby pracować z bazą danych w programie Visual Studio, ale zachować zgodność z programu SQL Server Express  
  
- W programie Visual Studio Otwórz projekt bez jego uaktualnieniem.  
  
    - Aby uruchomić projekt, wybierz klawisz F5.  
  
    - Aby edytować bazy danych, otwórz plik mdf w **Eksploratora rozwiązań**i rozwiń węzeł w **Eksploratora serwera** do pracy z bazą danych.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Aby program SQL Server Express domyślny aparat bazy danych  
  
1. Na pasku menu wybierz **narzędzia** > **opcje**.  
  
2. W **opcje** okna dialogowego rozwiń **narzędzia danych** opcje, a następnie wybierz **połączeń danych** węzła.  
  
3. W **nazwa wystąpienia serwera SQL** tekst pola, określ nazwę wystąpienia programu SQL Server Express lub LocalDB, którego chcesz używać. Jeśli nie jest nazwane wystąpienie, określ `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4. Wybierz przycisk **OK**.  
  
   SQL Server Express będzie domyślny aparat bazy danych dla aplikacji.  