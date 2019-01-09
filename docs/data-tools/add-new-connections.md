---
title: Dodaj nowe połączenia
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 73b09384bd57fd4ea0890d107ce641e4b615559f
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154221"
---
# <a name="add-new-connections"></a>Dodaj nowe połączenia

Przetestuj połączenie z bazą danych lub usługi i eksplorować zawartość bazy danych i schematów, za pomocą **Eksploratora serwera**, **programu Cloud Explorer**, lub **Eksplorator obiektów SQL Server**. Funkcje te okna nakłada się w pewnym stopniu. Podstawowe różnice są następujące:

- Server Explorer

   Instalowany domyślnie w programie Visual Studio. Może służyć do testowania połączeń i wyświetlania baz danych programu SQL Server, innych baz danych, które mają zainstalowanego dostawcę ADO.NET i niektórych usług platformy Azure. Pokazuje również obiektów niskiego poziomu, takie jak liczniki wydajności systemu, dzienniki zdarzeń i kolejki komunikatów. Jeśli źródło danych nie ma żadnego dostawcy ADO.NET, nie będzie widoczna w tym miejscu, ale możesz nadal używać go w programie Visual Studio, łącząc programowo.

- Cloud Explorer

   Ręcznie zainstaluj to okno jako rozszerzenia programu Visual Studio, wybierając **narzędzia** > **rozszerzenia i aktualizacje** > **Online**  >  **Witryny Marketplace programu visual Studio**. Udostępnia funkcje specjalne podczas samodzielnego eksplorowania i łączenie się z usługami platformy Azure.

- Eksplorator obiektów SQL Server

   Zainstalowany program SQL Server Data Tools i widoczne w obszarze **widoku** menu. Jeśli nie widzisz istnieje, przejdź do strony **programy i funkcje** w Panelu sterowania, Znajdź program Visual Studio, a następnie wybierz **zmiany** Aby ponownie uruchomić Instalatora po zaznaczeniu pola wyboru dla programu SQL Server Data Tools. Użyj **Eksplorator obiektów SQL Server** do baz danych SQL view (jeśli mają one dostawcy ADO.NET), tworzyć nowe bazy danych, zmodyfikuj schematów, tworzenie procedur składowanych, pobrać parametry połączenia, przeglądać dane i więcej. Bazy danych SQL, które nie jest zainstalowany dostawca ADO.NET nie będą wyświetlane w tym miejscu, ale można nadal połączyć się je programowo.

## <a name="add-a-connection-in-server-explorer"></a>Dodawanie połączenia w Eksploratorze serwera

Aby utworzyć połączenie z bazą danych, kliknij przycisk **Dodaj połączenie** ikonę **Eksploratora serwera**, lub kliknij prawym przyciskiem myszy **Eksploratora serwera** na **danych Połączenia** a następnie wybierz węzeł **Dodaj połączenie**. W tym miejscu możesz również nawiązać bazy danych na innym serwerze, usługi programu SharePoint lub usługi platformy Azure.

![Ikona nowego połączenia Eksploratora serwera](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Spowoduje to przejście **Dodaj połączenie** okno dialogowe. W tym miejscu możemy wprowadzono nazwę wystąpienia programu SQL Server LocalDB.

![Dodaj nowe połączenie](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Zmienianie dostawcy

Jeśli nie ma źródła danych, kliknij przycisk **zmiany** przycisk, aby wybrać nowe źródło danych i/lub nowego dostawcy danych ADO.NET. Nowy dostawca może poprosić o podanie poświadczeń, w zależności od sposobu skonfigurowania.

![Dostawca danych AD0.NET zmiany](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testuj połączenie

Po wybraniu źródła danych, kliknij przycisk **Testuj połączenie**. Jeśli się nie powiedzie, konieczne będzie rozwiązywanie zależności w dokumentacji udostępnianej przez dostawcę.

![Testuj połączenie](../data-tools/media/raddata-test-connection.png)

Jeśli test zakończy się powodzeniem, możesz przystąpić do tworzenia *źródła danych*, czyli termin programu Visual Studio, oznacza to naprawdę *modelu danych* opartego na podstawowej bazy danych lub usługi.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
