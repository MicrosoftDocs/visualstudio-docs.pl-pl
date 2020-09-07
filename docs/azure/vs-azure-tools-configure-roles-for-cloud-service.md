---
title: Konfigurowanie ról dla usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować i skonfigurować role dla usług Azure Cloud Services przy użyciu programu Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 960bd86a1e0993e4d2c57514a29ceecca34cca3d
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508512"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurowanie ról usług w chmurze platformy Azure przy użyciu programu Visual Studio
Usługa w chmurze platformy Azure może mieć co najmniej jedną rolę procesu roboczego lub sieci Web. Dla każdej roli należy zdefiniować sposób konfigurowania tej roli, a także skonfigurować sposób jej uruchamiania. Aby dowiedzieć się więcej o rolach w usługach w chmurze, zobacz [wprowadzenie do usługi Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Informacje o usłudze w chmurze są przechowywane w następujących plikach:

- **ServiceDefinition. csdef** — plik definicji usługi definiuje ustawienia czasu wykonywania dla usługi w chmurze, w tym informacje o wymaganych rolach, punktach końcowych i rozmiarze maszyny wirtualnej. Żadna z danych przechowywanych w nie `ServiceDefinition.csdef` może zostać zmieniona, gdy rola jest uruchomiona.
- **ServiceConfiguration. cscfg** — plik konfiguracji usługi służy do konfigurowania liczby wystąpień roli i wartości ustawień zdefiniowanych dla roli. Dane przechowywane w programie `ServiceConfiguration.cscfg` można zmienić, gdy rola jest uruchomiona.

Aby przechowywać różne wartości ustawień, które kontrolują sposób uruchamiania roli, można zdefiniować wiele konfiguracji usługi. Dla każdego środowiska wdrażania można użyć innej konfiguracji usługi. Można na przykład ustawić parametry połączenia konta magazynu tak, aby używały lokalnego emulatora usługi Azure Storage w konfiguracji usług lokalnych i utworzyć inną konfigurację usługi do korzystania z usługi Azure Storage w chmurze.

Podczas tworzenia usługi w chmurze platformy Azure w programie Visual Studio, dwie konfiguracje usługi są automatycznie tworzone i dodawane do projektu platformy Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurowanie usługi w chmurze platformy Azure
Eksplorator rozwiązań usługę w chmurze platformy Azure można skonfigurować w programie Visual Studio, jak pokazano w następujących krokach:

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe projektu Eksplorator rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stronie właściwości projektu wybierz kartę **programowanie** .

    ![Strona właściwości projektu — karta programowanie](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Na liście **Konfiguracja usługi** wybierz nazwę konfiguracji usługi, którą chcesz edytować. (Jeśli chcesz wprowadzić zmiany we wszystkich konfiguracjach usługi dla tej roli, wybierz opcję **wszystkie konfiguracje**).

    > [!IMPORTANT]
    > W przypadku wybrania określonej konfiguracji usługi niektóre właściwości są wyłączone, ponieważ mogą być ustawiane tylko dla wszystkich konfiguracji. Aby edytować te właściwości, należy wybrać **wszystkie konfiguracje**.

    ![Lista konfiguracji usługi dla usługi w chmurze platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Zmień liczbę wystąpień roli
Aby zwiększyć wydajność usługi w chmurze, można zmienić liczbę wystąpień roli, która jest uruchomiona, na podstawie liczby użytkowników lub obciążenia oczekiwanego dla określonej roli. Oddzielna maszyna wirtualna jest tworzona dla każdego wystąpienia roli, gdy usługa w chmurze jest uruchomiona na platformie Azure. Ma to wpływ na rozliczenia dla wdrożenia tej usługi w chmurze. Aby uzyskać więcej informacji na temat rozliczeń, zobacz [Opis rachunku na Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe Eksplorator rozwiązań roli platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Konfiguracja**.

    ![Karta Konfiguracja](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. W polu tekstowym **Liczba wystąpień** wprowadź liczbę wystąpień, które mają zostać uruchomione dla tej roli. Każde wystąpienie jest uruchamiane na oddzielnej maszynie wirtualnej po opublikowaniu usługi w chmurze na platformie Azure.

    ![Aktualizowanie liczby wystąpień](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Zarządzanie parametrami połączenia dla kont magazynu
Można dodawać, usuwać lub modyfikować parametry połączenia dla konfiguracji usługi. Można na przykład użyć lokalnych parametrów połączenia dla konfiguracji usługi lokalnej, która ma wartość `UseDevelopmentStorage=true` . Możesz również skonfigurować konfigurację usługi w chmurze, która korzysta z konta magazynu na platformie Azure.

> [!WARNING]
> Po wprowadzeniu informacji o kluczu konta usługi Azure Storage dla parametrów połączenia konta magazynu te informacje są przechowywane lokalnie w pliku konfiguracji usługi. Jednak te informacje nie są obecnie przechowywane jako zaszyfrowane.
>
>

Przy użyciu innej wartości dla każdej konfiguracji usługi nie trzeba używać różnych parametrów połączenia w usłudze w chmurze ani modyfikować kodu podczas publikowania usługi w chmurze na platformie Azure. Możesz użyć tej samej nazwy parametrów połączenia w kodzie, a wartość różni się w zależności od konfiguracji usługi wybranej podczas kompilowania usługi w chmurze lub po jej opublikowaniu.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe Eksplorator rozwiązań roli platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia**.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Konfiguracja usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać parametry połączenia, wybierz pozycję **Dodaj ustawienie**.

    ![Dodaj parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowego ustawienia do listy należy zaktualizować wiersz na liście przy użyciu niezbędnych informacji.

    ![Nowe parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę, która ma być używana dla parametrów połączenia.
    - **Typ** — wybierz opcję **Parametry połączenia** z listy rozwijanej.
    - **Wartość** — można wprowadzić parametry połączenia bezpośrednio w komórce **Value** lub wybrać wielokropek (...), aby działał w oknie dialogowym **Tworzenie parametrów połączenia magazynu** .

1. W oknie dialogowym **Tworzenie parametrów połączenia magazynu** wybierz opcję **połączenia za pomocą programu**. Następnie postępuj zgodnie z instrukcjami dotyczącymi wybranej opcji:

    - **Emulator magazynu Microsoft Azure** — w przypadku wybrania tej opcji pozostałe ustawienia w oknie dialogowym zostaną wyłączone, ponieważ mają zastosowanie tylko do platformy Azure. Wybierz pozycję **OK**.
    - **Twoja subskrypcja** — w przypadku wybrania tej opcji Użyj listy rozwijanej, aby wybrać i zalogować się do konto Microsoft lub dodać konto Microsoft. Wybierz subskrypcję platformy Azure i konto magazynu. Wybierz pozycję **OK**.
    - **Ręcznie wprowadzone poświadczenia** — wprowadź nazwę konta magazynu i klucz podstawowy lub drugi. Wybierz opcję **połączenia** (protokół HTTPS jest zalecany w przypadku większości scenariuszy). Wybierz **przycisk OK**.

1. Aby usunąć parametry połączenia, wybierz parametry połączenia, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-connection-string"></a>Programowe uzyskiwanie dostępu do parametrów połączenia

W poniższych krokach pokazano, jak programowo uzyskać dostęp do parametrów połączenia przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C#, w którym zamierzasz użyć tego ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład uzyskiwania dostępu do parametrów połączenia. Zamień &lt; symbol connectionstringname> na odpowiednią wartość.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Dodawanie niestandardowych ustawień do użycia w usłudze w chmurze platformy Azure
Ustawienia niestandardowe w pliku konfiguracji usługi pozwalają dodać nazwę i wartość ciągu dla określonej konfiguracji usługi. Możesz użyć tego ustawienia, aby skonfigurować funkcję w usłudze w chmurze, odczytując wartość ustawienia i korzystając z tej wartości w celu kontrolowania logiki w kodzie. Te wartości konfiguracji usługi można zmienić bez konieczności ponownego kompilowania pakietu usługi lub korzystania z usługi w chmurze. Kod może sprawdzać powiadomienia o zmianie ustawień. Zobacz [RoleEnvironment. zmiana zdarzenia](/previous-versions/azure/reference/ee758134(v=azure.100)).

Możesz dodawać, usuwać lub modyfikować niestandardowe ustawienia konfiguracji usługi. Mogą być potrzebne różne wartości dla tych ciągów dla różnych konfiguracji usługi.

Przy użyciu innej wartości dla każdej konfiguracji usługi nie trzeba używać różnych ciągów w usłudze w chmurze ani modyfikować kodu podczas publikowania usługi w chmurze na platformie Azure. Możesz użyć tej samej nazwy dla ciągu w kodzie, a wartość różni się w zależności od konfiguracji usługi wybranej podczas kompilowania usługi w chmurze lub po jej opublikowaniu.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe Eksplorator rozwiązań roli platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia**.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać ustawienie niestandardowe, wybierz pozycję **Dodaj ustawienie**.

    ![Dodaj ustawienie niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowego ustawienia do listy należy zaktualizować wiersz na liście przy użyciu niezbędnych informacji.

    ![Nowe ustawienie niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę ustawienia.
    - **Typ** — wybierz z listy rozwijanej **ciąg** .
    - **Wartość** — wprowadź wartość ustawienia. Możesz wprowadzić wartość bezpośrednio w komórce **Value** lub wybrać wielokropek (...), aby wprowadzić wartość w oknie dialogowym **Edytowanie ciągu** .

1. Aby usunąć ustawienie niestandardowe, wybierz ustawienie, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programowe uzyskiwanie dostępu do wartości ustawienia niestandardowego

W poniższych krokach pokazano, jak programowo uzyskać dostęp do niestandardowego ustawienia przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C#, w którym zamierzasz użyć tego ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład uzyskiwania dostępu do niestandardowego ustawienia. Zastąp ciąg &lt; setting> symbolem zastępczym odpowiednią wartością.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Zarządzanie magazynem lokalnym dla każdego wystąpienia roli
Można dodać lokalny magazyn systemu plików dla każdego wystąpienia roli. Dane przechowywane w tym magazynie nie są dostępne w innych wystąpieniach roli, dla których są przechowywane dane, lub przez inne role.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe Eksplorator rozwiązań roli platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Magazyn lokalny** .

    ![Karta magazyn lokalny](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Na liście **Konfiguracja usługi** upewnij się, że **wszystkie konfiguracje** są zaznaczone, ponieważ ustawienia magazynu lokalnego mają zastosowanie do wszystkich konfiguracji usługi. Każda inna wartość powoduje wyłączenie wszystkich pól wejściowych na stronie.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Aby dodać wpis magazynu lokalnego, wybierz pozycję **Dodaj magazyn lokalny**.

    ![Dodawanie magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po dodaniu nowego lokalnego wpisu magazynu do listy, zaktualizuj wiersz na liście o niezbędne informacje.

    ![Nowy wpis magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nazwa** — wprowadź nazwę, która ma być używana dla nowego magazynu lokalnego.
    - **Rozmiar (MB)** — wprowadź rozmiar (w MB), który będzie potrzebny dla nowego magazynu lokalnego.
    - **Wyczyść w przypadku odtwarzania roli** — wybierz tę opcję, aby usunąć dane z nowego magazynu lokalnego podczas odtwarzania maszyny wirtualnej dla tej roli.

1. Aby usunąć wpis magazynu lokalnego, wybierz pozycję, a następnie wybierz pozycję **Usuń magazyn lokalny**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-accessing-local-storage"></a>Programowe uzyskiwanie dostępu do magazynu lokalnego

W tej sekcji pokazano, jak programowo uzyskać dostęp do magazynu lokalnego przy użyciu języka C#, pisząc testowy plik tekstowy `MyLocalStorageTest.txt` .

### <a name="write-a-text-file-to-local-storage"></a>Napisz plik tekstowy do magazynu lokalnego

Poniższy kod przedstawia przykład sposobu pisania pliku tekstowego do magazynu lokalnego. Zastąp &lt; symbol zastępczy> LocalStorageName odpowiednią wartością.

```csharp
// Retrieve an object that points to the local storage resource
LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");

//Define the file name and path
string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
String filePath = Path.Combine(paths);

using (FileStream writeStream = File.Create(filePath))
{
    Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
    writeStream.Write(textToWrite, 0, textToWrite.Length);
}
```

### <a name="find-a-file-written-to-local-storage"></a>Znajdź plik zapisany w magazynie lokalnym

Aby wyświetlić plik utworzony przez kod w poprzedniej sekcji, wykonaj następujące kroki:

1. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę platformy Azure, a następnie z menu kontekstowego wybierz pozycję **Pokaż interfejs użytkownika emulatora obliczeń**.

    ![Pokaż emulator obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wybierz rolę sieci Web.

    ![Emulator obliczeń Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. W menu **emulatora obliczeń Microsoft Azure** wybierz pozycję **Narzędzia**  >  **Otwórz magazyn lokalny**.

    ![Otwórz element menu magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otwarciu okna Eksploratora Windows wprowadź "MyLocalStorageTest.txt" "w polu tekstowym **Wyszukaj** , a następnie wybierz **klawisz ENTER** , aby rozpocząć wyszukiwanie.

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o projektach platformy Azure w programie Visual Studio, odczytując [konfigurację projektu platformy Azure](vs-azure-tools-configuring-an-azure-project.md). Dowiedz się więcej o schemacie usługi w chmurze, odczytując [Informacje o schemacie](/previous-versions/azure/dd179398(v=azure.100)).