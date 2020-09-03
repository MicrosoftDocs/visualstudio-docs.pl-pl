---
title: Dodaj nowe połączenia | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673073"
---
# <a name="add-new-connections"></a>Dodawanie nowych połączeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz przetestować połączenie z bazą danych lub usługą oraz zbadać zawartość i schematy bazy danych za pomocą **Eksplorator serwera**, **Cloud Explorer**lub **Eksplorator obiektów SQL Server**. Funkcje tych okien nakładają się na pewien zakres. Podstawowe różnice są następujące:

 Eksplorator serwera instalowany domyślnie w programie Visual Studio. Może służyć do testowania połączeń i wyświetlania SQL Server baz danych, innych baz danych, na których zainstalowano dostawcę ADO.NET oraz niektórych usług platformy Azure. Pokazuje również obiekty niskiego poziomu, takie jak liczniki wydajności systemu, dzienniki zdarzeń i kolejki komunikatów. Jeśli źródło danych nie ma dostawcy ADO.NET, nie będzie ono wyświetlane w tym miejscu, ale nadal będzie można z niego korzystać z programu Visual Studio, łącząc program programowo.

 W programie Cloud Explorer ręcznie zainstaluj to okno jako rozszerzenie programu Visual Studio, wybierając pozycję **Narzędzia**  >  **rozszerzenia i aktualizacje**  >  **online**  >  **Galeria Visual Studio**. Oferuje wyspecjalizowaną funkcję eksplorowania i nawiązywania połączeń z usługami platformy Azure.

 Eksplorator obiektów SQL Server zainstalowana z narzędziami danych SQL Server i widoczna w menu **Widok** . Jeśli nie widzisz go tam, przejdź do **apletu programy i funkcje** w panelu sterowania, Znajdź program Visual Studio, a następnie wybierz pozycję **Zmień** , aby ponownie uruchomić Instalatora po zaznaczeniu pola wyboru dla SQL Server narzędzi danych. Użyj **Eksplorator obiektów SQL Server** , aby wyświetlać bazy danych SQL (jeśli mają dostawcę ADO.NET), tworzyć nowe bazy danych, modyfikować schematy, tworzyć procedury składowane, pobierać parametry połączenia, wyświetlać dane i nie tylko. Bazy danych SQL, w których nie zainstalowano żadnego dostawcy ADO.NET, nie będą wyświetlane w tym miejscu, ale nadal można z nich łączyć się programowo.

## <a name="add-a-connection-in-server-explorer"></a>Dodawanie połączenia w Eksplorator serwera
 Aby utworzyć połączenie z bazą danych, kliknij ikonę **Dodaj połączenie** w **Eksplorator serwera**lub kliknij prawym przyciskiem myszy w obszarze **Eksplorator serwera** w węźle **połączenia danych** i wybierz polecenie **Dodaj połączenie**. W tym miejscu możesz również nawiązać połączenie z bazą danych na innym serwerze, w usłudze SharePoint lub w usłudze platformy Azure.

 ![Ikona Eksplorator serwera nowe połączenie](../data-tools/media/raddata-server-explorer-new-connection-icon.png "ikona raddata Eksplorator serwera nowe połączenie")

 Spowoduje to wyświetlenie okna dialogowego **Dodawanie połączenia** . W tym miejscu wprowadzono nazwę SQL Server wystąpienia LocalDB.

 ![Dodaj nowe połączenie](../data-tools/media/raddata-add-new-connection-dialog.png "Okno dialogowe Dodawanie nowego połączenia raddata")

## <a name="change-the-provider"></a>Zmień dostawcę
 Jeśli źródło danych nie jest wybrane, kliknij przycisk **Zmień** , aby wybrać nowe źródło danych i/lub nowego dostawcę danych ADO.NET. Nowy dostawca może poproszony o podanie poświadczeń w zależności od sposobu jego konfiguracji.

 ![Zmień Dostawca danych AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata Zmień AD0.NET Dostawca danych")

## <a name="test-the-connection"></a>Testowanie połączenia
 Po wybraniu źródła danych kliknij pozycję **Testuj połączenie**. Jeśli to się nie powiedzie, należy rozwiązać problemy w oparciu o dokumentację dostawcy.

 ![Testuj połączenie](../data-tools/media/raddata-test-connection.png "Połączenie testowe raddata")

 Jeśli test zakończy się pomyślnie, możesz utworzyć *Źródło danych*, które jest terminem programu Visual Studio, który naprawdę oznacza *model danych* oparty na podstawowej bazie danych lub usłudze.

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
