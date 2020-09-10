---
title: Przeglądanie zasobów magazynu i zarządzanie nimi
description: Przeglądanie zasobów magazynu i zarządzanie nimi za pomocą Eksplorator serwera
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 6e75a3822df6a5867e48693024637b901d40282b
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89740000"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Przeglądanie zasobów magazynu i zarządzanie nimi za pomocą Eksploratora serwera

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Omówienie

Jeśli zainstalowano narzędzia platformy Azure dla Microsoft Visual Studio, można wyświetlać dane obiektów blob, kolejek i tabel z kont magazynu dla platformy Azure. Węzeł usługi Azure **Storage** w Eksplorator serwera zawiera dane znajdujące się na koncie emulatora magazynu lokalnego oraz inne konta usługi Azure Storage.

Aby wyświetlić Eksplorator serwera w programie Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **Eksplorator serwera**. W węźle **Magazyn** są wyświetlane wszystkie konta magazynu, które istnieją w ramach każdej subskrypcji lub certyfikatu platformy Azure, z którym nawiązano połączenie. Jeśli konto magazynu nie jest wyświetlane, możesz je dodać, postępując zgodnie z instrukcjami [w dalszej części tego artykułu](#add-storage-accounts-by-using-server-explorer).

Począwszy od zestawu Azure SDK 2,7, można również wyświetlać zasoby platformy Azure i zarządzać nimi za pomocą programu Cloud Explorer. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Wyświetlanie zasobów magazynu i zarządzanie nimi w programie Visual Studio

Eksplorator serwera automatycznie pokazuje listę obiektów blob, kolejek i tabel na koncie emulatora magazynu. Konto emulatora magazynu jest wymienione w Eksplorator serwera w węźle **Magazyn** jako węzeł **deweloperski** .

Aby wyświetlić zasoby konta emulatora magazynu, rozwiń węzeł **programowanie** . Jeśli emulator magazynu nie został uruchomiony po rozwinięciu węzła **deweloperskiego** , zostanie automatycznie uruchomiony. Ten proces może potrwać kilka sekund. Podczas uruchamiania emulatora magazynu można nadal korzystać z innych obszarów programu Visual Studio.

Aby wyświetlić zasoby na koncie magazynu, rozwiń węzeł konta magazynu w Eksplorator serwera, w którym znajdują się węzły **obiektów BLOB**, **kolejek**i **tabel** .

## <a name="work-with-blob-resources"></a>Korzystanie z zasobów obiektów BLOB

Węzeł **obiekty blob** wyświetla listę kontenerów dla wybranego konta magazynu. Kontenery obiektów BLOB zawierają pliki obiektów blob, a obiekty te można organizować w folderach i podfolderach. Aby uzyskać więcej informacji, zobacz [jak używać usługi BLOB Storage z platformy .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Aby utworzyć kontener obiektów BLOB

1. Otwórz menu skrótów dla węzła **obiekty blob** , a następnie wybierz pozycję **Utwórz kontener obiektów BLOB**.
1. W oknie dialogowym **Tworzenie kontenera obiektów BLOB** wprowadź nazwę nowego kontenera.
1. Wybierz klawisz Enter na klawiaturze lub kliknij lub naciśnij poza polem nazwy, aby zapisać kontener obiektów BLOB.

   > [!NOTE]
   > Nazwa kontenera obiektów BLOB musi rozpoczynać się od cyfry (0-9) lub małej litery (a – z).

### <a name="to-delete-a-blob-container"></a>Aby usunąć kontener obiektów BLOB

Otwórz menu skrótów dla kontenera obiektów blob, który chcesz usunąć, a następnie wybierz polecenie **Usuń**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Aby wyświetlić listę elementów w kontenerze obiektów BLOB

Otwórz menu skrótów dla nazwy kontenera obiektów BLOB na liście, a następnie wybierz polecenie **Otwórz**.

Po wyświetleniu zawartości kontenera obiektów BLOB pojawia się on na karcie znanej jako widok kontenera obiektów BLOB.

![Widok kontenera obiektów BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Można wykonać następujące operacje na obiektach Blob przy użyciu przycisków w prawym górnym rogu widoku kontenera obiektów blob:

* Wprowadź wartość filtru i Zastosuj ją.
* Odśwież listę obiektów BLOB w kontenerze.
* Przekaż plik.
* Usuń obiekt BLOB. (Usunięcie pliku z kontenera obiektów BLOB nie powoduje usunięcia pliku bazowego. Usuwa go tylko z kontenera obiektów BLOB.)
* Otwórz obiekt BLOB.
* Zapisz obiekt BLOB na komputerze lokalnym.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Aby utworzyć folder lub podfolder w kontenerze obiektów BLOB

1. Wybierz kontener obiektów BLOB w **Eksploratorze chmury**. W oknie kontenera wybierz przycisk **Przekaż obiekt BLOB** .

1. W oknie dialogowym **Przekaż nowy plik** wybierz przycisk **Przeglądaj** , aby określić plik do przekazania, a następnie wprowadź nazwę folderu w polu **folder (opcjonalnie)** .

   ![Przekazywanie pliku do folderu obiektów BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Można dodać podfoldery w folderach kontenerów, wykonując ten sam krok. Jeśli nie określisz nazwy folderu, plik zostanie przekazany do najwyższego poziomu kontenera obiektów BLOB. Plik pojawi się w określonym folderze w kontenerze.

   ![Folder dodany do kontenera obiektów BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Kliknij dwukrotnie folder lub wybierz klawisz ENTER, aby wyświetlić zawartość folderu. Gdy jesteś w folderze kontenera, możesz wrócić do katalogu głównego kontenera, wybierając przycisk **Otwórz katalog nadrzędny** (strzałka).

### <a name="to-delete-a-container-folder"></a>Aby usunąć folder kontenera

Usuń wszystkie pliki w folderze.

Ponieważ foldery w kontenerach obiektów BLOB są folderami wirtualnymi, nie można utworzyć pustego folderu. Nie można również usunąć folderu, aby usunąć jego zawartość, ale należy usunąć całą zawartość folderu, aby usunąć sam folder.

### <a name="to-filter-blobs-in-a-container"></a>Aby odfiltrować obiekty blob w kontenerze

Można filtrować obiekty blob, które są wyświetlane przez określenie wspólnego prefiksu.

Jeśli na przykład wprowadzisz polecenie **Hello** w polu tekstowym filtr, a następnie wybierzesz przycisk **Execute** (**!**), zostaną wyświetlone tylko obiekty blob zaczynające się od "Hello".

![Pole tekstowe filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

W polu tekstowym filtr jest rozróżniana wielkość liter i nie jest obsługiwane filtrowanie z użyciem symboli wieloznacznych. Obiekty blob można filtrować tylko według prefiksu. Prefiks może zawierać ogranicznik, jeśli używasz ogranicznika do organizowania obiektów BLOB w hierarchii wirtualnej. Na przykład filtrowanie na prefiksie "HelloFabric/" zwraca wszystkie obiekty blob, które zaczynają się od tego ciągu.

### <a name="to-download-blob-data"></a>Aby pobrać dane obiektów BLOB

W programie **Cloud Explorer**Użyj dowolnej z następujących metod:

* Otwórz menu skrótów dla co najmniej jednego obiektu BLOB, a następnie wybierz polecenie **Otwórz**.
* Wybierz nazwę obiektu BLOB, a następnie wybierz przycisk **Otwórz** .
* Kliknij dwukrotnie nazwę obiektu BLOB.

Postęp pobierania obiektu BLOB jest wyświetlany w oknie **Dziennik aktywności platformy Azure** .

Obiekt BLOB zostanie otwarty w domyślnym edytorze dla tego typu pliku. Jeśli system operacyjny rozpoznaje typ pliku, plik zostanie otwarty w aplikacji zainstalowanej lokalnie. W przeciwnym razie zostanie wyświetlony monit o wybranie aplikacji, która jest odpowiednia dla typu pliku obiektu BLOB. Plik lokalny, który jest tworzony podczas pobierania obiektu BLOB, jest oznaczony jako tylko do odczytu.

Dane obiektów BLOB są buforowane lokalnie i sprawdzane względem czasu ostatniej modyfikacji obiektu BLOB w usłudze Azure Blob Storage. Jeśli obiekt BLOB został zaktualizowany od czasu ostatniego pobrania, zostanie pobrany ponownie. W przeciwnym razie obiekt BLOB jest ładowany z dysku lokalnego.

Domyślnie obiekt BLOB jest pobierany do katalogu tymczasowego. Aby pobrać obiekty blob do określonego katalogu, otwórz menu skrótów dla wybranych nazw obiektów blob i wybierz polecenie **Zapisz jako**. Gdy zapisujesz obiekt BLOB w ten sposób, plik obiektu BLOB nie zostanie otwarty, a plik lokalny jest tworzony przy użyciu atrybutów odczytu i zapisu.

### <a name="to-upload-blobs"></a>Aby przekazać obiekty blob

Aby przekazać obiekty blob, wybierz przycisk **Przekaż obiekt BLOB** , gdy kontener jest otwarty do wyświetlania w widoku kontenera obiektów BLOB.

Można wybrać co najmniej jeden plik do przekazania i można przekazać pliki dowolnego typu. W oknie **Dziennik aktywności platformy Azure** zostanie wyświetlony postęp przekazywania. Aby uzyskać więcej informacji na temat sposobu pracy z danymi obiektów blob, zobacz [jak korzystać z usługi Azure Blob Storage w środowisku .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Aby wyświetlić dzienniki przesłane do obiektów BLOB

Jeśli używasz Diagnostyka Azure do rejestrowania danych z aplikacji platformy Azure i przeniesionosz dzienniki do konta magazynu, zobaczysz kontenery utworzone przez platformę Azure dla tych dzienników. Wyświetlanie tych dzienników w Eksplorator serwera to prosty sposób na zidentyfikowanie problemów z aplikacją, szczególnie w przypadku, gdy została ona wdrożona na platformie Azure.

Aby uzyskać więcej informacji na temat Diagnostyka Azure, zobacz [zbieranie danych rejestrowania przy użyciu Diagnostyka Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>Aby uzyskać adres URL dla obiektu BLOB

Otwórz menu skrótów obiektu BLOB, a następnie wybierz polecenie **Kopiuj adres URL**.

### <a name="to-edit-a-blob"></a>Aby edytować obiekt BLOB

Wybierz obiekt BLOB, a następnie wybierz przycisk **Otwórz obiekt BLOB** .

Plik zostanie pobrany do lokalizacji tymczasowej i otwarty na komputerze lokalnym. Przekaż obiekt BLOB ponownie po wprowadzeniu zmian.

## <a name="work-with-queue-resources"></a>Współpraca z zasobami kolejki

Kolejki usług magazynu są hostowane na koncie usługi Azure Storage. Można ich użyć, aby umożliwić role usługi w chmurze komunikować się ze sobą i z innymi usługami przez mechanizm przekazywania komunikatów. Dostęp do kolejki można wykonać programowo za pośrednictwem usługi w chmurze i za pośrednictwem usługi sieci Web dla klientów zewnętrznych. Dostęp do kolejki można także uzyskać bezpośrednio przy użyciu Eksplorator serwera w programie Visual Studio.

Podczas tworzenia usługi w chmurze, która korzysta z kolejek, możesz chcieć użyć programu Visual Studio do tworzenia kolejek i pracy z nimi interaktywnie podczas tworzenia i testowania kodu.

W Eksplorator serwera można wyświetlić kolejki na koncie magazynu, utworzyć i usunąć kolejki, otworzyć kolejkę w celu wyświetlenia jej komunikatów oraz dodać komunikaty do kolejki. Po otwarciu kolejki do wyświetlania można wyświetlić poszczególne komunikaty, a następnie wykonać następujące akcje w kolejce przy użyciu przycisków w lewym górnym rogu:

* Odśwież widok kolejki.
* Dodawanie komunikatu do kolejki.
* Usuwa komunikat z kolejki najwyższego poziomu.
* Wyczyść całą kolejkę.

Na poniższej ilustracji przedstawiono kolejkę zawierającą dwie komunikaty:

![Wyświetlanie kolejki](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Aby uzyskać więcej informacji o kolejkach usługi Storage, zobacz [Rozpoczynanie pracy z usługą Azure queue storage przy użyciu platformy .NET](/azure/storage/queues/storage-dotnet-how-to-use-queues). Aby uzyskać informacje na temat usługi sieci Web dla kolejek usług magazynu, zobacz temat [Omówienie usługi Queue](/rest/api/storageservices/Queue-Service-Concepts). Aby uzyskać informacje o sposobach wysyłania komunikatów do kolejki usług magazynu przy użyciu programu Visual Studio, zobacz [wysyłanie komunikatów do kolejki usług magazynu](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Kolejki usług magazynu różnią się od kolejek Azure Service Bus. Więcej informacji o Service Bus kolejkach znajduje się w temacie [Service Bus Queues, tematy i subskrypcje](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Współpraca z zasobami tabeli

Usługa Azure Table Storage służy do przechowywania dużych ilości danych strukturalnych. Usługa to magazyn danych NoSQL, który akceptuje uwierzytelnione wywołania z chmury platformy Azure i poza nią. Tabele Azure idealnie nadają się do przechowywania strukturalnych danych nierelacyjnych.

### <a name="to-create-a-table"></a>Aby utworzyć tabelę

1. W programie **Cloud Explorer**wybierz węzeł **tabele** konta magazynu, a następnie wybierz pozycję **Utwórz tabelę**.
1. W oknie dialogowym **Tworzenie tabeli** wprowadź nazwę tabeli.

### <a name="to-view-table-data"></a>Aby wyświetlić dane tabeli

1. W programie **Cloud Explorer**Otwórz węzeł **Azure** , a następnie otwórz węzeł **Magazyn** .
1. Otwórz węzeł konta magazynu, który Cię interesuje, a następnie otwórz węzeł **tabele** , aby wyświetlić listę tabel dla konta magazynu.
1. Otwórz menu skrótów dla tabeli, a następnie wybierz polecenie **Wyświetl tabelę**.

    ![Tabela platformy Azure w Eksplorator rozwiązań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tabela jest zorganizowana według jednostek (pokazanych w wierszach) i właściwości (pokazanych w kolumnach). Na przykład Następna ilustracja przedstawia jednostki wymienione w Projektancie tabel.

### <a name="to-edit-table-data"></a>Aby edytować dane tabeli

W **Projektancie tabel**, otwórz menu skrótów dla jednostki (pojedynczy wiersz) lub właściwość (pojedyncza komórka), a następnie wybierz pozycję **Edytuj**.

![Dodawanie lub edytowanie jednostki tabeli](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Jednostki w pojedynczej tabeli nie muszą mieć tego samego zestawu właściwości (kolumn). Należy pamiętać o następujących ograniczeniach dotyczących wyświetlania i edytowania danych tabeli:

* Nie można wyświetlać ani edytować danych binarnych ( `type byte[]` ), ale można je przechowywać w tabeli.
* Nie można edytować wartości **PartitionKey** lub **RowKey** , ponieważ usługa Azure Table Storage nie obsługuje tej operacji.
* Nie można utworzyć właściwości o nazwie **timestamp**. Usługi Azure Storage używają właściwości o tej nazwie.
* Jeśli wprowadzisz wartość **daty i godziny** , musisz użyć formatu odpowiedniego dla ustawienia Region i język komputera (na przykład mm/dd/rrrr hh: mm: SS [am | PM] dla angielskiej wersji językowej USA).

### <a name="to-add-entities"></a>Aby dodać jednostki

1. W **Projektancie tabel**wybierz przycisk **Dodaj jednostkę** .

    ![Przycisk Dodaj jednostkę](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. W oknie dialogowym **Dodawanie jednostki** wprowadź wartości właściwości **PartitionKey** i **RowKey** .

    ![Okno dialogowe Dodawanie jednostki](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Należy uważnie wprowadzić wartości. Nie można ich zmienić po zamknięciu okna dialogowego, chyba że usuniesz jednostkę i dodasz ją ponownie.

### <a name="to-filter-entities"></a>Aby filtrować jednostki

W przypadku korzystania z konstruktora kwerend można dostosować zestaw jednostek, które są wyświetlane w tabeli.

1. Aby otworzyć konstruktora zapytań, Otwórz tabelę do wyświetlenia.
1. Wybierz przycisk **Konstruktor zapytań** na pasku narzędzi widoku tabeli.

    Zostanie wyświetlone okno dialogowe **Konstruktor zapytań** . Na poniższej ilustracji przedstawiono zapytanie, które jest kompilowane w konstruktorze zapytań.

    ![Konstruktor zapytań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Po zakończeniu tworzenia zapytania Zamknij okno dialogowe. Tekst w postaci tekstu zapytania pojawia się w polu tekstowym jako filtr Usługi danych programu WCF.
1. Aby uruchomić zapytanie, wybierz ikonę zielonego trójkąta.

Możesz również filtrować dane jednostki, które pojawiają się w Projektancie tabel, jeśli wprowadzisz ciąg filtru Usługi danych programu WCF bezpośrednio w polu tekstowym filtru. Ten rodzaj ciągu jest podobny do klauzuli SQL WHERE, ale jest wysyłany do serwera jako żądanie HTTP. Aby uzyskać informacje o sposobie konstruowania ciągów filtru, zobacz [konstruowanie ciągów filtru dla projektanta tabel](vs-azure-tools-table-designer-construct-filter-strings.md).

Na poniższej ilustracji przedstawiono przykład prawidłowego ciągu filtru:

![Ciąg filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Odśwież dane magazynu

Gdy Eksplorator serwera nawiązuje połączenie lub pobiera dane z konta magazynu, operacja może potrwać do minuty. Jeśli nie można nawiązać połączenia Eksplorator serwera, operacja może przekroczyć limit czasu. Podczas pobierania danych można nadal korzystać z innych części programu Visual Studio. Aby anulować operację, jeśli trwa zbyt długo, wybierz przycisk **Zatrzymaj Odśwież** na pasku narzędzi Eksplorator serwera.

### <a name="to-refresh-blob-container-data"></a>Aby odświeżyć dane kontenera obiektów BLOB

* Wybierz węzeł **obiekty blob** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.
* Aby odświeżyć listę obiektów blob, które są wyświetlane, wybierz przycisk **Execute (wykonaj** ).

### <a name="to-refresh-table-data"></a>Aby odświeżyć dane tabeli

* Wybierz węzeł **tabele** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.
* Aby odświeżyć listę jednostek, które są wyświetlane w **Projektancie tabel**, wybierz przycisk **Execute (wykonaj** ) w Projektancie tabel.

### <a name="to-refresh-queue-data"></a>Aby odświeżyć dane kolejki

Wybierz węzeł **kolejki** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Aby odświeżyć wszystkie elementy na koncie magazynu

Wybierz nazwę konta, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Dodawanie kont magazynu przy użyciu Eksplorator serwera

Istnieją dwa sposoby dodawania kont magazynu za pomocą Eksplorator serwera. Możesz utworzyć konto magazynu w ramach subskrypcji platformy Azure lub dołączyć istniejące konto magazynu.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Aby utworzyć konto magazynu przy użyciu Eksplorator serwera

1. W Eksplorator serwera Otwórz menu skrótów dla węzła **Magazyn** , a następnie wybierz pozycję **Utwórz konto magazynu**.

1. W oknie dialogowym **Tworzenie konta magazynu** wybierz lub wprowadź następujące informacje:

   * Subskrypcja platformy Azure, do której chcesz dodać konto magazynu.
   * Nazwa, która ma być używana dla nowego konta magazynu.
   * Region lub grupa koligacji (na przykład zachodnie stany USA lub Azja Wschodnia).
   * Typ replikacji, który ma być używany dla konta magazynu, na przykład lokalnie nadmiarowy.

   ![Tworzenie konta usługi Azure Storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Wybierz pozycję **Utwórz**.

Nowe konto magazynu zostanie wyświetlone na liście **Magazyn** w Eksplorator rozwiązań.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Aby dołączyć istniejące konto magazynu przy użyciu Eksplorator serwera

1. W Eksplorator serwera Otwórz menu skrótów dla węzła usługi Azure **Storage** , a następnie wybierz pozycję **Dołącz magazyn zewnętrzny**.

    ![Dodawanie istniejącego konta magazynu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. W oknie dialogowym **Tworzenie konta magazynu** wybierz lub wprowadź następujące informacje:

   * Nazwa istniejącego konta magazynu, które chcesz dołączyć.
   * Klucz dla wybranego konta magazynu. Ta wartość jest zazwyczaj podawana po wybraniu konta magazynu. Jeśli chcesz, aby program Visual Studio zapamiętał klucz konta magazynu, zaznacz pole wyboru **Pamiętaj klucz konta** .
   * Protokół, który ma być używany do nawiązywania połączenia z kontem magazynu, na przykład HTTP, HTTPS lub niestandardowy punkt końcowy. Aby uzyskać więcej informacji na temat niestandardowych punktów końcowych, zobacz [jak skonfigurować parametry połączenia](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>Aby wyświetlić pomocnicze punkty końcowe

Jeśli utworzono konto magazynu za pomocą opcji replikacji **geograficznej dostępu do odczytu** , można wyświetlić jej pomocnicze punkty końcowe, otwierając menu skrótów dla nazwy konta, a następnie wybierając pozycję **Właściwości**.

![Pomocnicze punkty końcowe magazynu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Aby usunąć konto magazynu z Eksplorator serwera

W Eksplorator serwera Otwórz menu skrótów dla nazwy konta, a następnie wybierz polecenie **Usuń**.

Usunięcie konta magazynu spowoduje również usunięcie wszystkich zapisanych informacji o kluczu dla tego konta.

Po usunięciu konta magazynu z Eksplorator serwera nie wpłynie to na konto magazynu ani żadne dane, które zawiera. Po prostu usuwa odwołanie z Eksplorator serwera. Aby trwale usunąć konto magazynu, użyj [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat korzystania z usług Azure Storage, zobacz [dostęp do usług Azure Storage](/azure/storage/common/storage-introduction).
