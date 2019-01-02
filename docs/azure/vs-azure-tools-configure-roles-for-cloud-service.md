---
title: Konfigurowanie ról usługi w chmurze platformy Azure
description: Informacje o sposobie instalowania i konfigurowania ról dla usług Azure cloud services przy użyciu programu Visual Studio.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9bbc913b98b4acddd04a2cc1e5b331848f85e2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893673"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurowanie ról usług w chmurze platformy Azure przy użyciu programu Visual Studio
Usługi w chmurze platformy Azure może mieć jedną lub więcej procesów roboczych lub role sieci web. Dla każdej roli musisz zdefiniować sposób konfigurowania tej roli, a także skonfigurować, jak działa tej roli. Aby dowiedzieć się więcej na temat ról w usługach cloud services, zobacz wideo [wprowadzenie do usług Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

Informacje dotyczące usługi w chmurze są przechowywane w następujących plikach:

- **Plik ServiceDefinition.csdef** -pliku definicji usługi definiuje ustawienia środowiska uruchomieniowego dla swojej usługi w chmurze w tym, jakie role są wymagane punkty końcowe i rozmiar maszyny wirtualnej. Brak danych przechowywanych w `ServiceDefinition.csdef` można zmienić, gdy jest uruchomiona rola użytkownika.
- **ServiceConfiguration.cscfg** — plik konfiguracji usługi umożliwia skonfigurowanie liczby wystąpień roli są uruchamiane, a wartości ustawienia zdefiniowane dla roli. Dane przechowywane w `ServiceConfiguration.cscfg` można zmienić po uruchomieniu roli użytkownika.

Aby przechowywać różne wartości dla ustawienia które kontrolują sposób uruchamiania roli, można zdefiniować wiele konfiguracji usługi. Dla każdego środowiska wdrażania, można użyć konfiguracji innej usługi. Na przykład można ustawić parametry połączenia konta magazynu, tak aby korzystanie z emulatora lokalnego magazynu platformy Azure w ramach konfiguracji lokalnej usługi i utworzyć inną konfigurację usługi do użycia usługi Azure storage w chmurze.

Po utworzeniu usługi w chmurze platformy Azure w programie Visual Studio dwie konfiguracje usługi są automatycznie tworzone i dodawane do projektu platformy Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurowanie usługi w chmurze platformy Azure
W programie Visual Studio, można skonfigurować usługi w chmurze platformy Azure za pomocą Eksploratora rozwiązań, jak pokazano w poniższych krokach:

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **właściwości**.
   
    ![Menu kontekstowego projektu Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stronie właściwości projektu, wybierz **rozwoju** kartę. 

    ![Strony właściwości projektu — karta rozwoju](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. W **konfiguracji usługi** listy, wybierz nazwę konfiguracji usługi, które chcesz edytować. (Wprowadzić zmiany w konfiguracji usługi dla tej roli, należy zaznaczyć **wszystkie konfiguracje**.)
   
    > [!IMPORTANT]
    > Jeśli wybierzesz konfigurację określonej usługi, niektóre właściwości są wyłączone, ponieważ ich można ustawić tylko w przypadku wszystkich konfiguracji. Aby edytować te właściwości, należy wybrać **wszystkie konfiguracje**.
    > 
    > 
   
    ![Lista konfiguracji usługi dla usługi w chmurze platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Zmień liczbę wystąpień roli
Aby poprawić wydajność usługi w chmurze, możesz zmienić liczbę wystąpień roli, które działają na podstawie liczby użytkowników lub obciążenia dla określonej roli. Oddzielnej maszynie wirtualnej jest tworzony dla każdego wystąpienia roli, gdy usługa w chmurze działa na platformie Azure. Ma to wpływ na rozliczenia, wdrożenia tej usługi w chmurze. Aby uzyskać więcej informacji na temat rozliczeń, zobacz [opis zawartości rachunku dla systemu Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu. W obszarze **role** węzła, kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz **właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz **konfiguracji** kartę.

    ![Karta Konfiguracja](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. W **konfiguracji usługi** wybierz konfigurację usługi, które chcesz zaktualizować.
   
    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. W **liczba wystąpień** tekstu wprowadź liczbę wystąpień, które chcesz uruchomić tę rolę. Każde wystąpienie jest uruchamiany na oddzielnej maszynie wirtualnej, gdy Opublikuj usługę w chmurze na platformie Azure.

    ![Trwa aktualizowanie liczby wystąpień](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. W programie Visual Studio pasek narzędzi, wybierz opcję **Zapisz**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Zarządzanie parametry połączenia dla konta magazynu
Możesz dodać, usunąć lub zmodyfikować parametrów połączenia w przypadku konfiguracji z usługi. Na przykład, możesz zechcieć ciąg połączenia lokalnej konfiguracji usługi lokalnej, która ma wartość `UseDevelopmentStorage=true`. Można również skonfigurować konfigurację usługi w chmurze korzysta z konta magazynu na platformie Azure.

> [!WARNING]
> Po wprowadzeniu usługi Azure storage kluczowych informacji o koncie parametry połączenia konta magazynu, te informacje są przechowywane lokalnie w pliku konfiguracji usługi. Jednak te informacje obecnie nie są przechowywane jako tekst zaszyfrowany.
> 
> 

Za pomocą innej wartości dla każdej konfiguracji usługi, nie trzeba używać parametrów połączenia w innej usłudze w chmurze lub zmodyfikować kod, po opublikowaniu usługi w chmurze na platformie Azure. Można użyć dla tej samej nazwy parametrów połączenia w kodzie, a wartość jest inny, na podstawie konfiguracji usługi, który należy wybrać podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu. W obszarze **role** węzła, kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz **właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz **ustawienia** kartę.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. W **konfiguracji usługi** wybierz konfigurację usługi, które chcesz zaktualizować.

    ![Konfiguracja usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać parametry połączenia, wybierz **Dodaj ustawienie**.

    ![Dodaj parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowe ustawienie do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowe parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę, którą chcesz używać dla parametrów połączenia.
    - **Typ** — wybierz tę opcję **parametry połączenia** z listy rozwijanej.
    - **Wartość** — można wprowadzić parametry połączenia bezpośrednio w **wartość** komórki lub wybierz wielokropek (...) do pracy w **utworzyć parametry połączenia magazynu** okna dialogowego.  

1. W **utworzyć parametry połączenia magazynu** okno dialogowe, wybierz opcję dla **nawiązywanie połączenia przy użyciu**. Następnie postępuj zgodnie z instrukcjami dotyczącymi wybranej opcji:

    - **Microsoft Azure storage emulator** — Jeśli wybierzesz tę opcję, pozostałe ustawienia w oknie dialogowym są wyłączone, ponieważ mają one zastosowanie tylko do platformy Azure. Wybierz **OK**.
    - **Twoja subskrypcja** — w przypadku wybrania tej opcji, użyj listy rozwijanej można wybrać i zaloguj się do konta Microsoft lub dodać konta Microsoft. Wybierz konta subskrypcji i magazynu platformy Azure. Wybierz **OK**.
    - **Ręcznie wprowadzić poświadczenia** — wprowadź nazwę konta magazynu i klucz podstawowy lub drugiej. Wybierz opcję **połączenia** (protokół HTTPS jest zalecane w przypadku większości scenariuszy). Wybierz **OK**.

1. Aby usunąć ciąg połączenia, wybierz parametry połączenia, a następnie wybierz **Usuń ustawienie**.

1. W programie Visual Studio pasek narzędzi, wybierz opcję **Zapisz**.

## <a name="programmatically-access-a-connection-string"></a>Programowy dostęp do parametrów połączenia

Poniższe kroki pokazują jak programowo uzyskać dostęp parametrów połączenia przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C# których zamierzasz używać ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład dostęp do parametrów połączenia. Zastąp &lt;ConnectionStringName > Symbol zastępczy odpowiednią wartość. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Dodaj ustawienia niestandardowe do użycia w usłudze w chmurze Azure
Ustawienia niestandardowe w pliku konfiguracji usługi umożliwiają Dodaj nazwę i wartość ciągu dla konfiguracji określonej usługi. Można użyć tego ustawienia, aby skonfigurować funkcję w usłudze w chmurze, odczytując wartość ustawienia i kontrolowania logiki w kodzie za pomocą tej wartości. Możesz zmienić te wartości konfiguracji usługi bez konieczności ponownego kompilowania pakietu usługi lub gdy jest uruchomiona usługa w chmurze. Powiadomienia o kodzie można sprawdzić podczas zmiany ustawienia. Zobacz [zdarzeń RoleEnvironment.Changing](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Możesz dodać, usunąć lub zmodyfikować ustawienia niestandardowe dla Twojej konfiguracji usługi. Możesz zechcieć różne wartości dla tych ciągów, w przypadku konfiguracji z innej usługi.

Za pomocą innej wartości dla każdej konfiguracji usługi, nie trzeba używać różnych parametrów w usłudze w chmurze lub zmodyfikować kod, po opublikowaniu usługi w chmurze na platformie Azure. Można użyć dla tej samej nazwy ciągu w kodzie, a wartość jest inny, na podstawie konfiguracji usługi, który należy wybrać podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu. W obszarze **role** węzła, kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz **właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz **ustawienia** kartę.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. W **konfiguracji usługi** wybierz konfigurację usługi, które chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać niestandardową wartość ustawienia, wybierz **Dodaj ustawienie**.

    ![Dodaj ustawienia niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowe ustawienie do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowe ustawienie niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — Podaj nazwę ustawienia.
    - **Typ** — wybierz tę opcję **ciąg** z listy rozwijanej.
    - **Wartość** -wprowadź wartość ustawienia. Można wprowadzać wartości bezpośrednio do **wartość** komórki lub wybierz wielokropek (...), aby wprowadzić wartość **Edytowanie ciągu** okna dialogowego.  

1. Aby usunąć niestandardową wartość ustawienia, wybierz ustawienie, a następnie wybierz **Usuń ustawienie**.

1. W programie Visual Studio pasek narzędzi, wybierz opcję **Zapisz**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programowy dostęp do wartości ustawienia niestandardowego
 
Poniższe kroki pokazują jak programowo uzyskać dostęp ustawienia niestandardowego przy użyciu języka C#.

1. Dodaj następujące dyrektywy using do pliku języka C# których zamierzasz używać ustawienia:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład niestandardowe ustawienie dostępu. Zastąp &lt;SettingName > Symbol zastępczy odpowiednią wartość. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Zarządzanie magazynem lokalnym dla każdego wystąpienia roli
Możesz dodać magazyn systemu plików lokalnych dla każdego wystąpienia roli. Danych przechowywanych w pamięci masowej nie jest dostępny przez innych wystąpień roli, dla którego dane są przechowywane lub innych ról.  

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, rozwiń węzeł projektu. W obszarze **role** węzła, kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz **właściwości**.

    ![Menu kontekstowe roli Azure Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz **Magazyn lokalny** kartę.

    ![Karta magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. W **konfiguracji usługi** listy, upewnij się, że **wszystkie konfiguracje** jest zaznaczone, ponieważ ustawienia lokalnego magazynu mają zastosowanie do wszystkich konfiguracji z usługi. Dowolna inna wartość powoduje pól wejściowych na stronie są wyłączone. 

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Aby dodać wpis magazynu lokalnego, wybierz **dodać magazyn lokalny**.

    ![Dodaj magazyn lokalny](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po dodaniu nowego wpisu w magazynie lokalnym do listy zaktualizuj wiersz na liście niezbędne informacje.

    ![Nowy wpis magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nazwa** — wprowadź nazwę, którą chcesz użyć dla nowego magazynu lokalnego.
    - **Rozmiar (MB)** -wprowadź rozmiar w Megabajtach, potrzebna do nowego magazynu lokalnego.
    - **Czyszczenie na odtwarzanie roli** — wybierz tę opcję, aby usunąć dane w nowym magazynie lokalnym, gdy maszyna wirtualna dla roli zostanie odtworzona.

1. Aby usunąć wpis magazynu lokalnego, wybierz wpis, a następnie wybierz **usunąć magazyn lokalny**.

1. W programie Visual Studio pasek narzędzi, wybierz opcję **Zapisz**.

## <a name="programmatically-accessing-local-storage"></a>Programowe uzyskiwanie dostępu do magazynu lokalnego

W tej sekcji przedstawiono sposób programowego dostępu do magazynu lokalnego przy użyciu języka C#, pisząc plik tekstowy testu `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Wpisywanie tekstu do pliku w magazynie lokalnym

Poniższy kod przedstawia przykład sposobu wpisywanie tekstu do pliku w magazynie lokalnym. Zastąp &lt;LocalStorageName > Symbol zastępczy odpowiednią wartość. 

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
    
1.  W obszarze powiadomień Windows kliknij prawym przyciskiem myszy ikonę platformy Azure oraz z menu kontekstowego wybierz **Pokaż interfejs użytkownika emulatora obliczeń**. 

    ![Pokaż emulatora obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wybierz rolę sieci web.

    ![Emulator obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Na **emulatora obliczeń Azure Microsoft** menu, wybierz opcję **narzędzia** > **Otwórz magazynu lokalnego**.

    ![Element menu Otwórz magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otwarciu okna Eksploratora Windows, wpisz "MyLocalStorageTest.txt'' do **wyszukiwania** pola tekstowego, a następnie wybierz pozycję **Enter** ma się rozpocząć wyszukiwanie. 

## <a name="next-steps"></a>Następne kroki
Więcej informacji na temat projektów systemu Azure w programie Visual Studio, czytając [Konfigurowanie projektu Azure](vs-azure-tools-configuring-an-azure-project.md). Więcej informacji na temat schematu usługi w chmurze, czytając [odwołanie do schematu](https://msdn.microsoft.com/library/azure/dd179398).
