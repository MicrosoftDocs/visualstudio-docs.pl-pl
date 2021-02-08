---
title: Dodawanie usługi Azure Storage przy użyciu usług połączonych | Microsoft Docs
description: Dodawanie zależności usługi Azure Storage do aplikacji przy użyciu usług połączonych programu Visual Studio
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: a2aa5a0453b6a05c261d3cac853ab8265fb4e453
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844349"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Dodawanie usługi Azure Storage przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure Storage przy użyciu funkcji **usługi połączone** :

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Nawiązywanie połączenia z usługą Azure Storage przy użyciu usług połączonych

::: moniker range="vs-2017"

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

    ![Dodawanie usługi połączonej z platformą Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Na stronie **usługi połączone** wybierz pozycję **Magazyn w chmurze z usługą Azure Storage**.

    ![Dodawanie usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. W oknie dialogowym **Azure Storage** Wybierz istniejące konto magazynu i wybierz pozycję **Dodaj**.

    Jeśli musisz utworzyć konto magazynu, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto magazynu do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Aby utworzyć konto magazynu:

   1. Wybierz pozycję **Utwórz nowe konto magazynu** w dolnej części okna dialogowego.

   1. Wypełnij okno dialogowe **Tworzenie konta magazynu** , a następnie wybierz pozycję **Utwórz**.

       ![Nowe konto usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po wyświetleniu okna dialogowego **usługi Azure Storage** nowe konto magazynu zostanie wyświetlone na liście. Wybierz nowe konto magazynu z listy, a następnie wybierz pozycję **Dodaj**.

1. Usługa połączona do magazynu jest wyświetlana w węźle **odwołania do usługi** projektu.
:::moniker-end

:::moniker range=">=vs-2019"

1. Otwórz projekt w programie Visual Studio.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

    ![Dodawanie usługi połączonej z platformą Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Na karcie **połączone usługi** wybierz ikonę + dla **zależności usługi**.

    ![Dodaj zależność usługi](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stronie **Dodawanie zależności** wybierz pozycję **Azure Storage**.

    ![Dodawanie usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Zaloguj się do konta platformy Azure, jeśli jeszcze nie zalogowano się. Jeśli nie masz konta platformy Azure, możesz zarejestrować się, aby skorzystać z [bezpłatnej wersji próbnej](https://azure.microsoft.com/account/free).

1. Na ekranie **Konfigurowanie usługi Azure Storage** Wybierz istniejące konto magazynu i wybierz pozycję **dalej**.

    Jeśli musisz utworzyć konto magazynu, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto magazynu do projektu](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Aby utworzyć konto magazynu:

   1. Wybierz pozycję **Utwórz konto magazynu** w dolnej części okna dialogowego.

   1. Wypełnij pola **usługa Azure Storage: Utwórz nowe** okno dialogowe, a następnie wybierz pozycję **Utwórz**.

       ![Nowe konto usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Po wyświetleniu okna dialogowego **usługi Azure Storage** nowe konto magazynu zostanie wyświetlone na liście. Wybierz nowe konto magazynu z listy, a następnie wybierz pozycję **dalej**.

1. Wprowadź nazwę parametrów połączenia i zdecyduj, czy chcesz, aby parametry połączenia były przechowywane w lokalnym pliku tajemnicy, czy w [Azure Key Vault](/azure/key-vault).

   ![Określ parametry połączenia](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. Na ekranie **Podsumowanie zmian** są wyświetlane wszystkie modyfikacje, które zostaną wprowadzone w projekcie w przypadku ukończenia procesu. Jeśli zmiany wyglądają na OK, wybierz przycisk **Zakończ**.

   ![Podsumowanie zmian](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Usługa połączona do magazynu jest wyświetlana w węźle **odwołania do usługi** projektu.
:::moniker-end

## <a name="see-also"></a>Zobacz też

- [Forum usługi Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Dokumentacja usługi Azure Storage](/azure/storage/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)
