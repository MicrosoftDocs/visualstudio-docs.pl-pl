---
title: Dodawanie pamięci podręcznej platformy Azure dla Redis za pomocą usług połączonych | Microsoft Docs
description: Dodaj usługę Azure cache for Redis do aplikacji przy użyciu programu Visual Studio w celu dodania podłączonej usługi
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 48554484781cca46ba96f8a075d18ea55ec3ef43
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398621"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Dodawanie pamięci podręcznej platformy Azure dla Redis przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure cache for Redis przy użyciu funkcji **usługi połączone** :

- Aplikacja konsolowa .NET Framework
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (w tym Aplikacja konsolowa, WPF, Windows Forms, Biblioteka klas)
- Rola procesu roboczego platformy .NET Core
- Azure Functions
- Aplikacja platforma uniwersalna systemu Windows
- Xamarin
- Cordova

Funkcja połączonej usługi dodaje wszystkie konieczne odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracyjne.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [usługi połączone w programie Visual Studio dla komputerów Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z zainstalowanym obciążeniem platformy Azure.
- Projekt jednego z obsługiwanych typów

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Łączenie z usługą Azure cache for Redis za pomocą usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **pamięć podręczna platformy Azure dla Redis**.

    ![Dodawanie usługi Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **Konfigurowanie usługi Azure cache for Redis** wybierz istniejącą pamięć podręczną platformy Azure dla Redis, a **następnie** wybierz przycisk Dalej.

    Jeśli musisz utworzyć nowy składnik, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Nawiązywanie połączenia z istniejącą pamięcią podręczną platformy Azure dla usługi Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Aby utworzyć Azure Redis Cache:

   1. Wybierz pozycję **Utwórz nową Azure Redis Cache** w dolnej części ekranu.

   1. Wypełnij **pamięć podręczną platformy Azure dla Redis: Utwórz nowy** ekran, a następnie wybierz pozycję **Utwórz**.

       ![Nowa pamięć podręczna platformy Azure dla usługi Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Po wyświetleniu ekranu **Konfigurowanie usługi Azure cache for Redis** na liście zostanie wyświetlona nowa pamięć podręczna. Wybierz nową bazę danych z listy, a następnie wybierz pozycję **dalej**.

1. Wprowadź nazwę parametrów połączenia lub wybierz wartość domyślną, a następnie wybierz, czy parametry połączenia mają być przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Połączenie jest wyświetlane w sekcji **zależności usługi** na karcie **podłączone usługi** .

   ![Zależności usługi](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Strona produktu Azure cache for Redis](https://azure.microsoft.com/services/cache)
- [Pamięć podręczna systemu Azure dla dokumentacji Redis](/azure/azure-cache-for-redis/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)