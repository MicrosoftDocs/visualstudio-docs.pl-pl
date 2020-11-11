---
title: Dodawanie nowych połączeń
description: Dodawanie połączenia w programie Visual Studio do bazy danych lub usługi oraz Eksplorowanie zawartości i schematów bazy danych przy użyciu Eksplorator serwera, Cloud Explorer lub Eksplorator obiektów SQL Server.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 32fbd3462f6a496d681f76480c3eb4451f325b35
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518716"
---
# <a name="add-new-connections"></a>Dodawanie nowych połączeń

Możesz przetestować połączenie z bazą danych lub usługą oraz zbadać zawartość i schematy bazy danych za pomocą **Eksplorator serwera** , **Cloud Explorer** lub **Eksplorator obiektów SQL Server**. Funkcje tych okien nakładają się na pewien zakres. Podstawowe różnice są następujące:

- Eksplorator serwera

   Instalowany domyślnie w programie Visual Studio. Może służyć do testowania połączeń i wyświetlania SQL Server baz danych, innych baz danych, na których zainstalowano dostawcę ADO.NET oraz niektórych usług platformy Azure. Pokazuje również obiekty niskiego poziomu, takie jak liczniki wydajności systemu, dzienniki zdarzeń i kolejki komunikatów. Jeśli źródło danych nie ma dostawcy ADO.NET, nie będzie ono wyświetlane w tym miejscu, ale nadal będzie można z niego korzystać z programu Visual Studio, łącząc program programowo.

- Cloud Explorer

   Zainstaluj to okno ręcznie jako rozszerzenie programu Visual Studio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Oferuje wyspecjalizowaną funkcję eksplorowania i nawiązywania połączeń z usługami platformy Azure.

- Eksplorator obiektów SQL Server

   Instalowany z narzędziami danych SQL Server i widocznymi w menu **Widok** . Jeśli nie widzisz go tam, przejdź do **apletu programy i funkcje** w panelu sterowania, Znajdź program Visual Studio, a następnie wybierz pozycję **Zmień** , aby ponownie uruchomić Instalatora po zaznaczeniu pola wyboru dla SQL Server narzędzi danych. Użyj **Eksplorator obiektów SQL Server** , aby wyświetlać bazy danych SQL (jeśli mają dostawcę ADO.NET), tworzyć nowe bazy danych, modyfikować schematy, tworzyć procedury składowane, pobierać parametry połączenia, wyświetlać dane i nie tylko. Bazy danych SQL, w których nie zainstalowano żadnego dostawcy ADO.NET, nie będą wyświetlane w tym miejscu, ale nadal można z nich łączyć się programowo.

## <a name="add-a-connection-in-server-explorer"></a>Dodawanie połączenia w Eksplorator serwera

Aby utworzyć połączenie z bazą danych, kliknij ikonę **Dodaj połączenie** w **Eksplorator serwera** lub kliknij prawym przyciskiem myszy w obszarze **Eksplorator serwera** w węźle **połączenia danych** i wybierz polecenie **Dodaj połączenie**. W tym miejscu możesz również nawiązać połączenie z bazą danych na innym serwerze, w usłudze SharePoint lub w usłudze platformy Azure.

![Ikona Eksplorator serwera nowe połączenie](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Spowoduje to wyświetlenie okna dialogowego **Dodawanie połączenia** . W tym miejscu wprowadzono nazwę SQL Server wystąpienia LocalDB.

![Dodaj nowe połączenie](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Zmień dostawcę

Jeśli źródło danych nie jest wybrane, kliknij przycisk **Zmień** , aby wybrać nowe źródło danych i/lub nowego dostawcę danych ADO.NET. Nowy dostawca może poproszony o podanie poświadczeń w zależności od sposobu jego konfiguracji.

![Zmień Dostawca danych AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testowanie połączenia

Po wybraniu źródła danych kliknij pozycję **Testuj połączenie**. Jeśli to się nie powiedzie, należy rozwiązać problemy w oparciu o dokumentację dostawcy.

![Testuj połączenie](../data-tools/media/raddata-test-connection.png)

Jeśli test zakończy się pomyślnie, możesz utworzyć *Źródło danych* , które jest terminem programu Visual Studio, który naprawdę oznacza *model danych* oparty na podstawowej bazie danych lub usłudze.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
