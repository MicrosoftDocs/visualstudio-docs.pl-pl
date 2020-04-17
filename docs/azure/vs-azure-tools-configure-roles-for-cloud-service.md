---
title: Konfigurowanie ról usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować i skonfigurować role dla usług w chmurze platformy Azure przy użyciu programu Visual Studio.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: a01a1fb182fc9d45e4e08dcd9acb8e0ec734f098
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489730"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurowanie ról usług w chmurze platformy Azure przy użyciu programu Visual Studio
Usługa w chmurze platformy Azure może mieć co najmniej jedną rolę roboczą lub rolę sieci web. Dla każdej roli należy zdefiniować sposób konfigurowania tej roli, a także skonfigurować sposób działania tej roli. Aby dowiedzieć się więcej o rolach w usługach w chmurze, zobacz klip wideo [Wprowadzenie do usług w chmurze Azure.](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)

Informacje dotyczące usługi w chmurze są przechowywane w następujących plikach:

- **ServiceDefinition.csdef** — plik definicji usługi definiuje ustawienia czasu wykonywania usługi w chmurze, w tym jakie role są wymagane, punkty końcowe i rozmiar maszyny wirtualnej. Żadne dane przechowywane `ServiceDefinition.csdef` w można zmienić, gdy rola jest uruchomiona.
- **ServiceConfiguration.cscfg** — plik konfiguracji usługi konfiguruje liczbę wystąpień roli i wartości ustawień zdefiniowanych dla roli. Dane przechowywane `ServiceConfiguration.cscfg` w można zmienić, gdy rola jest uruchomiona.

Aby przechowywać różne wartości dla ustawień, które kontrolują sposób działania roli, można zdefiniować wiele konfiguracji usługi. Można użyć innej konfiguracji usługi dla każdego środowiska wdrażania. Na przykład można ustawić ciąg połączenia konta magazynu, aby używać emulatora lokalnego magazynu platformy Azure w konfiguracji usługi lokalnej i utworzyć inną konfigurację usługi do używania magazynu platformy Azure w chmurze.

Podczas tworzenia usługi w chmurze platformy Azure w programie Visual Studio dwie konfiguracje usługi są automatycznie tworzone i dodawane do projektu platformy Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurowanie usługi w chmurze platformy Azure
Usługę w chmurze platformy Azure można skonfigurować z Eksploratora rozwiązań w programie Visual Studio, jak pokazano w następujących krokach:

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe projektu Eksploratora rozwiązań](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Na stronie właściwości projektu wybierz kartę **Rozwój.**

    ![Strona właściwości projektu — karta programowanie](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Na liście **Konfiguracja usługi** wybierz nazwę konfiguracji usługi, którą chcesz edytować. (Jeśli chcesz wprowadzić zmiany we wszystkich konfiguracjach usługi dla tej roli, wybierz **opcję Wszystkie konfiguracje).**

    > [!IMPORTANT]
    > Jeśli wybierzesz określoną konfigurację usługi, niektóre właściwości są wyłączone, ponieważ można je ustawić tylko dla wszystkich konfiguracji. Aby edytować te właściwości, należy wybrać **opcję Wszystkie konfiguracje**.

    ![Lista konfiguracji usługi dla usługi w chmurze platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Zmienianie liczby wystąpień roli
Aby zwiększyć wydajność usługi w chmurze, można zmienić liczbę wystąpień roli, które są uruchomione, na podstawie liczby użytkowników lub obciążenia oczekiwanego dla określonej roli. Oddzielna maszyna wirtualna jest tworzona dla każdego wystąpienia roli, gdy usługa w chmurze jest uruchamiana na platformie Azure. Ma to wpływ na rozliczenia za wdrożenie tej usługi w chmurze. Aby uzyskać więcej informacji na temat rozliczeń, zobacz [Opis rachunku za platformę Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu. W węźle **Role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe roli Azure w eksploratorze rozwiązania](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Konfiguracja**.

    ![Karta Konfiguracja](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. W polu **tekstowym Liczba wystąpień** wprowadź liczbę wystąpień, które chcesz uruchomić dla tej roli. Każde wystąpienie jest uruchamiane na osobnej maszynie wirtualnej podczas publikowania usługi w chmurze na platformie Azure.

    ![Aktualizowanie liczby wystąpień](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Na pasku narzędzi Visual Studio wybierz pozycję **Zapisz**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Zarządzanie ciągami połączeń dla kont magazynu
Można dodawać, usuwać lub modyfikować parametry połączenia dla konfiguracji usługi. Na przykład można chcieć lokalnego ciągu połączenia dla lokalnej `UseDevelopmentStorage=true`konfiguracji usługi o wartości . Można również skonfigurować konfigurację usługi w chmurze, która używa konta magazynu na platformie Azure.

> [!WARNING]
> Po wprowadzeniu informacji o kluczu konta magazynu platformy Azure dla ciągu połączenia konta magazynu te informacje są przechowywane lokalnie w pliku konfiguracji usługi. Jednak te informacje nie są obecnie przechowywane jako zaszyfrowany tekst.
>
>

Przy użyciu innej wartości dla każdej konfiguracji usługi, nie trzeba używać różnych ciągów połączeń w usłudze w chmurze lub zmodyfikować kod podczas publikowania usługi w chmurze na platformie Azure. Można użyć tej samej nazwy dla ciągu połączenia w kodzie, a wartość jest inna, na podstawie konfiguracji usługi, która jest wybierana podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu. W węźle **Role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe roli Azure w eksploratorze rozwiązania](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia**.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Konfiguracja usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać ciąg połączenia, wybierz pozycję **Dodaj ustawienie**.

    ![Dodaj ciąg połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowego ustawienia do listy zaktualizuj wiersz na liście o niezbędne informacje.

    ![Nowe parametry połączenia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę, której chcesz użyć dla ciągu połączenia.
    - **Typ** — wybierz **ciąg połączenia** z listy rozwijanej.
    - **Wartość** — ciąg połączenia można wprowadzić bezpośrednio do komórki **Wartość** lub wybrać wielokropek (...) do pracy w oknie dialogowym **Utwórz ciąg połączenia magazynu.**

1. W oknie dialogowym **Tworzenie ciągu połączenia magazynu** wybierz opcję **Połącz za pomocą programu**. Następnie postępuj zgodnie z instrukcjami dotyczącymi wybranej opcji:

    - **Emulator magazynu platformy Microsoft Azure** — jeśli wybierzesz tę opcję, pozostałe ustawienia w oknie dialogowym zostaną wyłączone, ponieważ dotyczą tylko platformy Azure. Kliknij przycisk **OK**.
    - **Subskrypcja** — jeśli wybierzesz tę opcję, użyj listy rozwijanej, aby wybrać i zalogować się do konta Microsoft lub dodać konto Microsoft. Wybierz konto subskrypcji i magazynu platformy Azure. Kliknij przycisk **OK**.
    - **Ręcznie wprowadzone poświadczenia** — wprowadź nazwę konta magazynu i klucz podstawowy lub drugi. Wybierz opcję **dla połączenia** (protokół HTTPS jest zalecany w większości scenariuszy). Wybierz **przycisk OK**.

1. Aby usunąć ciąg połączenia, zaznacz ciąg połączenia, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-connection-string"></a>Programowy dostęp do ciągu połączenia

Poniższe kroki pokazują, jak programowo uzyskać dostęp do ciągu połączenia przy użyciu języka C#.

1. Dodaj następujące za pomocą dyrektyw do pliku Języka C#, w którym ma być używane to ustawienie:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład jak uzyskać dostęp do ciągu połączenia. Zastąp &lt;symbol zastępczy ConnectionStringName> odpowiednią wartością.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Dodawanie ustawień niestandardowych do użycia w usłudze w chmurze platformy Azure
Ustawienia niestandardowe w pliku konfiguracji usługi umożliwiają dodanie nazwy i wartości ciągu dla określonej konfiguracji usługi. Można użyć tego ustawienia, aby skonfigurować funkcję w usłudze w chmurze, odczytając wartość ustawienia i używając tej wartości do kontrolowania logiki w kodzie. Te wartości konfiguracji usługi można zmienić bez konieczności przebudowy pakietu usług lub gdy usługa w chmurze jest uruchomiona. Kod może sprawdzić powiadomienia o zmianie ustawienia. Zobacz [Zdarzenie RoleEnvironment.Changing](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Można dodawać, usuwać lub modyfikować ustawienia niestandardowe dla konfiguracji usługi. Można chcieć różnych wartości dla tych ciągów dla różnych konfiguracji usługi.

Przy użyciu innej wartości dla każdej konfiguracji usługi, nie trzeba używać różnych ciągów w usłudze w chmurze lub zmodyfikować kod podczas publikowania usługi w chmurze na platformie Azure. Można użyć tej samej nazwy dla ciągu w kodzie, a wartość jest inna, na podstawie konfiguracji usługi, która jest wybierana podczas tworzenia usługi w chmurze lub podczas publikowania go.

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu. W węźle **Role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe roli Azure w eksploratorze rozwiązania](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Ustawienia**.

    ![Karta Ustawienia](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Na liście **Konfiguracja usługi** wybierz konfigurację usługi, którą chcesz zaktualizować.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Aby dodać ustawienie niestandardowe, wybierz pozycję **Dodaj ustawienie**.

    ![Dodawanie ustawienia niestandardowego](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Po dodaniu nowego ustawienia do listy zaktualizuj wiersz na liście o niezbędne informacje.

    ![Nowe ustawienie niestandardowe](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nazwa** — wprowadź nazwę ustawienia.
    - **Typ** — wybierz **ciąg** z listy rozwijanej.
    - **Wartość** — umożliwia wprowadzenie wartości ustawienia. Wartość można wprowadzić bezpośrednio do komórki **Wartość** lub wybrać wielokropek (...) aby wprowadzić wartość w oknie dialogowym **Edytuj ciąg.**

1. Aby usunąć ustawienie niestandardowe, zaznacz to ustawienie, a następnie wybierz pozycję **Usuń ustawienie**.

1. Na pasku narzędzi Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programowy dostęp do wartości ustawienia niestandardowego

Poniższe kroki pokazują, jak programowo uzyskać dostęp do ustawienia niestandardowego przy użyciu języka C#.

1. Dodaj następujące za pomocą dyrektyw do pliku Języka C#, w którym ma być używane to ustawienie:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Poniższy kod ilustruje przykład, jak uzyskać dostęp do ustawienia niestandardowego. Zastąp symbol zastępczy &lt;> Ustawienia odpowiednią wartością.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Zarządzanie magazynem lokalnym dla każdego wystąpienia roli
Można dodać magazyn lokalnego systemu plików dla każdego wystąpienia roli. Dane przechowywane w tym magazynie nie są dostępne przez inne wystąpienia roli, dla której dane są przechowywane, lub przez inne role.

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**rozwiń węzeł projektu. W węźle **Role** kliknij prawym przyciskiem myszy rolę, którą chcesz zaktualizować, a z menu kontekstowego wybierz polecenie **Właściwości**.

    ![Menu kontekstowe roli Azure w eksploratorze rozwiązania](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wybierz kartę **Magazyn lokalny.**

    ![Karta Magazyn lokalny](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Na liście **Konfiguracja usługi** upewnij się, że **wszystkie konfiguracje** są wybrane jako ustawienia magazynu lokalnego mają zastosowanie do wszystkich konfiguracji usługi. Każda inna wartość powoduje wyłączenie wszystkich pól wejściowych na stronie.

    ![Lista konfiguracji usługi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Aby dodać wpis magazynu lokalnego, wybierz pozycję **Dodaj magazyn lokalny**.

    ![Dodawanie magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Po dodaniu nowego wpisu magazynu lokalnego do listy zaktualizuj wiersz na liście o niezbędne informacje.

    ![Nowy wpis magazynu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nazwa** — wprowadź nazwę, której chcesz użyć w nowym magazynie lokalnym.
    - **Rozmiar (MB)** — wprowadź rozmiar w MB, który jest potrzebny dla nowego magazynu lokalnego.
    - **Wyczyść odtwarzanie roli** — wybierz tę opcję, aby usunąć dane w nowym magazynie lokalnym, gdy maszyna wirtualna dla roli jest odtwolatywać.

1. Aby usunąć wpis magazynu lokalnego, zaznacz go, a następnie wybierz pozycję **Usuń magazyn lokalny**.

1. Na pasku narzędzi Visual Studio wybierz pozycję **Zapisz**.

## <a name="programmatically-accessing-local-storage"></a>Programowy dostęp do pamięci lokalnej

W tej sekcji pokazano, jak programowo uzyskać dostęp do magazynu `MyLocalStorageTest.txt`lokalnego przy użyciu języka C# przez napisanie testowego pliku tekstowego .

### <a name="write-a-text-file-to-local-storage"></a>Zapisywanie pliku tekstowego w magazynie lokalnym

Poniższy kod przedstawia przykład sposobu pisania pliku tekstowego do magazynu lokalnego. Zastąp symbol zastępczy &lt;LocalStorageName> odpowiednią wartością.

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

### <a name="find-a-file-written-to-local-storage"></a>Znajdowanie pliku zapisanego w magazynie lokalnym

Aby wyświetlić plik utworzony przez kod w poprzedniej sekcji, wykonaj następujące kroki:

1. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę platformy Azure, a następnie z menu kontekstowego wybierz polecenie **Pokaż interfejs użytkownika emulatora obliczeń**.

    ![Pokaż emulator obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wybierz rolę sieci Web.

    ![Emulator obliczeń platformy Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. W menu **Emulator obliczeń platformy Microsoft Azure** wybierz polecenie **Narzędzia** > **Otwórz sklep lokalny**.

    ![Otwórz element menu sklepu lokalnego](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Po otwarciu okna Eksploratora Windows wprowadź w polu tekstowym **Wyszukaj** pozycję "MyLocalStorageTest.txt" i wybierz pozycję **Wprowadź,** aby rozpocząć wyszukiwanie.

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o projektach platformy Azure w programie Visual Studio, [czytając pozycję Konfigurowanie projektu platformy Azure.](vs-azure-tools-configuring-an-azure-project.md) Dowiedz się więcej o schemacie usługi w chmurze, czytając [odwołanie do schematu](https://msdn.microsoft.com/library/azure/dd179398).
