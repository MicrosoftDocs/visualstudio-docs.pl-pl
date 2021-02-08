---
title: Dodaj usługę Azure sygnalizacji przy użyciu usług połączonych | Microsoft Docs
description: Dodaj usługę Azure Signal do aplikacji przy użyciu programu Visual Studio, aby dodać podłączoną usługi
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: a3b76115e7d5cfe484c9aea00246e4d42acf6268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841163"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Dodawanie usługi Azure Signaler przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure Signal Service przy użyciu funkcji **usługi połączone** :

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Nawiązywanie połączenia z usługą Azure Signaler przy użyciu usług połączonych

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **usługa Azure Signal**.

    ![Dodaj usługę Azure Signal Service](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **Konfigurowanie usługi Azure Signal** wybierz istniejący składnik usługi Azure sygnalizujący, a następnie wybierz przycisk **dalej**.

    Jeśli musisz utworzyć nowy składnik, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 7.

    ![Połącz z istniejącym składnikiem usługi Azure Signal](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Aby utworzyć wystąpienie usługi Azure sygnalizujące:

   1. Wybierz pozycję **Utwórz nowe wystąpienie usługi Azure sygnalizujące** w dolnej części ekranu.

   1. Wypełnij **usługę Azure Signal Service: Utwórz nowy** ekran, a następnie wybierz pozycję **Utwórz**.

       ![Nowe wystąpienie usługi Azure sygnalizujące](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Po wyświetleniu ekranu **Konfigurowanie usługi Azure sygnalizacyjnyej** na liście pojawi się nowe wystąpienie. Wybierz nowe wystąpienie z listy, a następnie wybierz przycisk **dalej**.

1. Wprowadź nazwę parametrów połączenia lub wybierz wartość domyślną, a następnie wybierz, czy parametry połączenia mają być przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/azure-signalr-add-connected-service/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Połączenie jest wyświetlane w sekcji **zależności usługi** na karcie **podłączone usługi** .

   ![Zależności usługi](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Zobacz też

- [Strona produktu usługi Azure Signal](https://azure.microsoft.com/services/signalr-service/)
- [Dokumentacja usługi Azure SignalR Service](/azure/azure-signalr)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)
