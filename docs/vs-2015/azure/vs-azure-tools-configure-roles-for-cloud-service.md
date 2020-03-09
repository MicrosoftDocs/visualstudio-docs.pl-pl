---
title: Konfigurowanie ról usługi w chmurze platformy Azure
description: Informacje o sposobie instalowania i konfigurowania ról dla usług Azure cloud services przy użyciu programu Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 810ebfcfb4cb4354c3df4c0d9892a37ca1624256
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410066"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurowanie ról usług w chmurze platformy Azure przy użyciu programu Visual Studio
Usługi w chmurze platformy Azure może mieć jedną lub więcej procesów roboczych lub role sieci web. Dla każdej roli musisz zdefiniować sposób konfigurowania tej roli, a także skonfigurować, jak działa tej roli. Aby dowiedzieć się więcej o rolach w usługach w chmurze, zobacz [wprowadzenie do usługi Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Informacje dotyczące usługi w chmurze są przechowywane w następujących plikach:

- **ServiceDefinition. csdef** — plik definicji usługi definiuje ustawienia środowiska uruchomieniowego dla usługi w chmurze, w tym informacje o wymaganych rolach, punktach końcowych i rozmiarze maszyny wirtualnej. Żadna z danych przechowywanych w `ServiceDefinition.csdef` nie może zostać zmieniona, gdy rola jest uruchomiona.
- **ServiceConfiguration. cscfg** — plik konfiguracji usługi służy do konfigurowania liczby wystąpień roli i wartości ustawień zdefiniowanych dla roli. Dane przechowywane w `ServiceConfiguration.cscfg` można zmienić, gdy rola jest uruchomiona.

Aby przechowywać różne wartości dla ustawienia które kontrolują sposób uruchamiania roli, można zdefiniować wiele konfiguracji usługi. Dla każdego środowiska wdrażania, można użyć konfiguracji innej usługi. Na przykład można ustawić parametry połączenia konta magazynu, tak aby korzystanie z emulatora lokalnego magazynu platformy Azure w ramach konfiguracji lokalnej usługi i utworzyć inną konfigurację usługi do użycia usługi Azure storage w chmurze.

Po utworzeniu usługi w chmurze platformy Azure w programie Visual Studio dwie konfiguracje usługi są automatycznie tworzone i dodawane do projektu platformy Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurowanie usługi w chmurze platformy Azure
W programie Visual Studio, można skonfigurować usługi w chmurze platformy Azure za pomocą Eksploratora rozwiązań, jak pokazano w poniższych krokach:

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowego projektu Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stronie właściwości projektu wybierz kartę **programowanie** .

    ![Strony właściwości projektu — karta rozwoju](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Na liście **Konfiguracja usługi** wybierz nazwę konfiguracji usługi, którą chcesz edytować. (Jeśli chcesz wprowadzić zmiany we wszystkich konfiguracjach usługi dla tej roli, wybierz opcję **wszystkie konfiguracje**).

    > [!IMPORTANT]
    > Jeśli wybierzesz konfigurację określonej usługi, niektóre właściwości są wyłączone, ponieważ ich można ustawić tylko w przypadku wszystkich konfiguracji. Aby edytować te właściwości, należy wybrać **wszystkie konfiguracje**.
    >
    >

    ![Lista konfiguracji usługi dla usługi w chmurze platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Zmień liczbę wystąpień roli
Aby poprawić wydajność usługi w chmurze, możesz zmienić liczbę wystąpień roli, które działają na podstawie liczby użytkowników lub obciążenia dla określonej roli. Oddzielnej maszynie wirtualnej jest tworzony dla każdego wystąpienia roli, gdy usługa w chmurze działa na platformie Azure. Ma to wpływ na rozliczenia, wdrożenia tej usługi w chmurze. Aby uzyskać więcej informacji na temat rozliczeń, zobacz [Opis rachunku na Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Konfiguracja** .

    ![Karta Konfiguracja](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. W polu tekstowym **Liczba wystąpień** wprowadź liczbę wystąpień, które mają zostać uruchomione dla tej roli. Każde wystąpienie jest uruchamiany na oddzielnej maszynie wirtualnej, gdy Opublikuj usługę w chmurze na platformie Azure.

    ![Trwa aktualizowanie liczby wystąpień](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Zarządzanie parametry połączenia dla konta magazynu
Możesz dodać, usunąć lub zmodyfikować parametrów połączenia w przypadku konfiguracji z usługi. Można na przykład użyć lokalnych parametrów połączenia dla konfiguracji usługi lokalnej, która ma wartość `UseDevelopmentStorage=true`. Można również skonfigurować konfigurację usługi w chmurze korzysta z konta magazynu na platformie Azure.

> [!WARNING]
> Po wprowadzeniu usługi Azure storage kluczowych informacji o koncie parametry połączenia konta magazynu, te informacje są przechowywane lokalnie w pliku konfiguracji usługi. Jednak te informacje obecnie nie są przechowywane jako tekst zaszyfrowany.
>
>

Za pomocą innej wartości dla każdej konfiguracji usługi, nie trzeba używać parametrów połączenia w innej usłudze w chmurze lub zmodyfikować kod, po opublikowaniu usługi w chmurze na platformie Azure. Można użyć dla tej samej nazwy parametrów połączenia w kodzie, a wartość jest inny, na podstawie konfiguracji usługi, który należy wybrać podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia** .

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Konfiguracja usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać parametry połączenia, wybierz pozycję **Dodaj ustawienie**.

    ![Dodaj parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowe ustawienie do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowe parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę, która ma być używana dla parametrów połączenia.
    - **Typ** — wybierz opcję **Parametry połączenia** z listy rozwijanej.
    - **Wartość** — można wprowadzić parametry połączenia bezpośrednio w komórce **Value** lub wybrać wielokropek (...), aby działał w oknie dialogowym **Tworzenie parametrów połączenia magazynu** .

1. W oknie dialogowym **Tworzenie parametrów połączenia magazynu** wybierz opcję **połączenia za pomocą programu**. Następnie postępuj zgodnie z instrukcjami dotyczącymi wybranej opcji:

    - **Microsoft Azure emulatora magazynu** — w przypadku wybrania tej opcji pozostałe ustawienia w oknie dialogowym zostaną wyłączone, ponieważ mają zastosowanie tylko do platformy Azure. Kliknij przycisk **OK**.
    - **Twoja subskrypcja** — w przypadku wybrania tej opcji Użyj listy rozwijanej, aby wybrać i zalogować się do konto Microsoft lub dodać konto Microsoft. Wybierz konta subskrypcji i magazynu platformy Azure. Kliknij przycisk **OK**.
    - **Ręcznie wprowadzone poświadczenia** — wprowadź nazwę konta magazynu i klucz podstawowy lub drugi. Wybierz opcję **połączenia** (protokół HTTPS jest zalecany w przypadku większości scenariuszy). Wybierz **przycisk OK**.

1. Aby usunąć parametry połączenia, wybierz parametry połączenia, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-connection-string"></a>Programowy dostęp do parametrów połączenia

Poniższe kroki pokazują jak programowo uzyskać dostęp parametrów połączenia przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C# których zamierzasz używać ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład dostęp do parametrów połączenia. Zastąp symbol zastępczy &lt;ConnectionStringname > odpowiednią wartością.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Dodaj ustawienia niestandardowe do użycia w usłudze w chmurze Azure
Ustawienia niestandardowe w pliku konfiguracji usługi umożliwiają Dodaj nazwę i wartość ciągu dla konfiguracji określonej usługi. Można użyć tego ustawienia, aby skonfigurować funkcję w usłudze w chmurze, odczytując wartość ustawienia i kontrolowania logiki w kodzie za pomocą tej wartości. Możesz zmienić te wartości konfiguracji usługi bez konieczności ponownego kompilowania pakietu usługi lub gdy jest uruchomiona usługa w chmurze. Powiadomienia o kodzie można sprawdzić podczas zmiany ustawienia. Zobacz [RoleEnvironment. zmiana zdarzenia](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Możesz dodać, usunąć lub zmodyfikować ustawienia niestandardowe dla Twojej konfiguracji usługi. Możesz zechcieć różne wartości dla tych ciągów, w przypadku konfiguracji z innej usługi.

Za pomocą innej wartości dla każdej konfiguracji usługi, nie trzeba używać różnych parametrów w usłudze w chmurze lub zmodyfikować kod, po opublikowaniu usługi w chmurze na platformie Azure. Można użyć dla tej samej nazwy ciągu w kodzie, a wartość jest inny, na podstawie konfiguracji usługi, który należy wybrać podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia** .

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać ustawienie niestandardowe, wybierz pozycję **Dodaj ustawienie**.

    ![Dodaj ustawienia niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowe ustawienie do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowe ustawienie niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę ustawienia.
    - **Typ** — wybierz z listy rozwijanej **ciąg** .
    - **Wartość** — wprowadź wartość ustawienia. Możesz wprowadzić wartość bezpośrednio w komórce **Value** lub wybrać wielokropek (...), aby wprowadzić wartość w oknie dialogowym **Edytowanie ciągu** .

1. Aby usunąć ustawienie niestandardowe, wybierz ustawienie, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programowy dostęp do wartości ustawienia niestandardowego

Poniższe kroki pokazują jak programowo uzyskać dostęp ustawienia niestandardowego przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C# których zamierzasz używać ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład niestandardowe ustawienie dostępu. Zastąp &lt;SettingName > symbolem zastępczym odpowiednią wartością.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Zarządzanie magazynem lokalnym dla każdego wystąpienia roli
Możesz dodać magazyn systemu plików lokalnych dla każdego wystąpienia roli. Danych przechowywanych w pamięci masowej nie jest dostępny przez innych wystąpień roli, dla którego dane są przechowywane lub innych ról.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**rozwiń węzeł projektu. W węźle **role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a następnie z menu kontekstowego wybierz pozycję **Właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Magazyn lokalny** .

    ![Karta magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Na liście **Konfiguracja usługi** upewnij się, że **wszystkie konfiguracje** są zaznaczone, ponieważ ustawienia magazynu lokalnego mają zastosowanie do wszystkich konfiguracji usługi. Dowolna inna wartość powoduje pól wejściowych na stronie są wyłączone.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Aby dodać wpis magazynu lokalnego, wybierz pozycję **Dodaj magazyn lokalny**.

    ![Dodaj magazyn lokalny](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po dodaniu nowego wpisu w magazynie lokalnym do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowy wpis magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nazwa** — wprowadź nazwę, która ma być używana dla nowego magazynu lokalnego.
    - **Rozmiar (MB)** — wprowadź rozmiar (w MB), który będzie potrzebny dla nowego magazynu lokalnego.
    - **Wyczyść w przypadku odtwarzania roli** — wybierz tę opcję, aby usunąć dane z nowego magazynu lokalnego podczas odtwarzania maszyny wirtualnej dla tej roli.

1. Aby usunąć wpis magazynu lokalnego, wybierz pozycję, a następnie wybierz pozycję **Usuń magazyn lokalny**.

1. Na pasku narzędzi programu Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-accessing-local-storage"></a>Programowe uzyskiwanie dostępu do magazynu lokalnego

W tej sekcji pokazano, jak programowo uzyskać dostęp do C# lokalnego magazynu przy użyciu programu, pisząc testowy plik tekstowy `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Wpisywanie tekstu do pliku w magazynie lokalnym

Poniższy kod przedstawia przykład sposobu wpisywanie tekstu do pliku w magazynie lokalnym. Zastąp symbol zastępczy &lt;LocalStorageName > odpowiednią wartością.

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

    ![Pokaż emulatora obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wybierz rolę sieci web.

    ![Emulator obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. W menu **emulatora obliczeń Microsoft Azure** wybierz pozycję **Narzędzia** > **Otwórz magazyn lokalny**.

    ![Element menu Otwórz magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otwarciu okna Eksploratora Windows wprowadź "MyLocalStorageTest. txt" "w polu tekstowym **wyszukiwania** , a następnie wybierz polecenie **Enter** , aby rozpocząć wyszukiwanie.

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o projektach platformy Azure w programie Visual Studio, odczytując [konfigurację projektu platformy Azure](vs-azure-tools-configuring-an-azure-project.md). Dowiedz się więcej o schemacie usługi w chmurze, odczytując [Informacje o schemacie](https://msdn.microsoft.com/library/azure/dd179398).
