---
title: Przeglądanie i zarządzanie zasobami magazynu za pomocą Eksploratora serwera | Dokumentacja firmy Microsoft
description: Przeglądanie i zarządzanie zasobami magazynowania za pomocą Eksploratora serwera
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 36b2691525eb66bf946317c1bb5254796d5cd639
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291224"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Przeglądanie zasobów magazynu i zarządzanie nimi za pomocą Eksploratora serwera

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Przegląd

Jeśli po zainstalowaniu narzędzi platformy Azure dla programu Microsoft Visual Studio, można wyświetlić obiektów blob, kolejki i tabelę danych z kont magazynu dla platformy Azure. Węzeł usługi Azure **Storage** w Eksplorator serwera zawiera dane znajdujące się na koncie emulatora magazynu lokalnego oraz inne konta usługi Azure Storage.

Aby wyświetlić Eksplorator serwera w programie Visual Studio, na pasku menu wybierz pozycję **wyświetl** > **Eksplorator serwera**. W węźle **Magazyn** są wyświetlane wszystkie konta magazynu, które istnieją w ramach każdej subskrypcji lub certyfikatu platformy Azure, z którym nawiązano połączenie. Jeśli konto magazynu nie jest wyświetlane, możesz je dodać, postępując zgodnie z instrukcjami [w dalszej części tego artykułu](#add-storage-accounts-by-using-server-explorer).

Począwszy od platformy Azure SDK 2.7 umożliwia także programu Cloud Explorer do przeglądania i zarządzania zasobami platformy Azure. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Wyświetlanie i zarządzanie zasobami magazynu w programie Visual Studio

Eksplorator serwera automatycznie pokazuje listę obiektów blob, kolejek i tabel na koncie emulatora magazynu. Konto emulatora magazynu jest wymienione w Eksplorator serwera w węźle **Magazyn** jako węzeł **deweloperski** .

Aby wyświetlić zasoby konta emulatora magazynu, rozwiń węzeł **programowanie** . Jeśli emulator magazynu nie został uruchomiony po rozwinięciu węzła **deweloperskiego** , zostanie automatycznie uruchomiony. Ten proces może potrwać kilka sekund. Możesz kontynuować pracę w innych obszarach programu Visual Studio, podczas uruchamiania emulatora magazynu.

Aby wyświetlić zasoby na koncie magazynu, rozwiń węzeł konta magazynu w Eksplorator serwera, w którym znajdują się węzły **obiektów BLOB**, **kolejek**i **tabel** .

## <a name="work-with-blob-resources"></a>Praca z zasobami obiektów blob

Węzeł **obiekty blob** wyświetla listę kontenerów dla wybranego konta magazynu. Kontenery obiektów blob zawierają pliki obiektów blob, a tych obiektów blob można organizować w foldery i podfoldery. Aby uzyskać więcej informacji, zobacz [jak używać usługi BLOB Storage z platformy .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Aby utworzyć kontener obiektów blob

1. Otwórz menu skrótów dla węzła **obiekty blob** , a następnie wybierz pozycję **Utwórz kontener obiektów BLOB**.
1. W oknie dialogowym **Tworzenie kontenera obiektów BLOB** wprowadź nazwę nowego kontenera.  
1. Naciśnij klawisz Enter na klawiaturze lub możesz kliknąć lub nacisnąć poza pole nazwy, aby zapisać kontenera obiektów blob.

   > [!NOTE]
   > Nazwa kontenera obiektu blob musi zaczynać się od liczby (0 – 9) lub małą literą (a – z).

### <a name="to-delete-a-blob-container"></a>Aby usunąć kontener obiektów blob

Otwórz menu skrótów dla kontenera obiektów blob, który chcesz usunąć, a następnie wybierz polecenie **Usuń**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Aby wyświetlić listę elementów w kontenerze obiektów blob

Otwórz menu skrótów dla nazwy kontenera obiektów BLOB na liście, a następnie wybierz polecenie **Otwórz**.

Po wyświetleniu zawartości kontenera obiektów blob zostanie wyświetlony na karcie, znane jako widok kontenera obiektów blob.

![Widok kontenera obiektów blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Korzystając z przycisków w prawym górnym rogu widoku kontenera obiektów blob, należy wykonać następujące operacje obiektów blob:

* Wprowadź wartość filtru i zastosować je.
* Odśwież listę obiektów blob w kontenerze.
* Przekaż plik.
* Usuwanie obiektu blob. (Usunięcie pliku z kontenera obiektów blob nie powoduje usunięcia pliku podstawowego. Powoduje tylko usunięcie go z kontenera obiektów blob.)
* Otwórz obiekt blob.
* Zapisywanie obiektu blob na komputerze lokalnym.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Aby utworzyć folder lub podfolder w kontenerze obiektów blob

1. Wybierz kontener obiektów blob w Eksploratorze chmury. W oknie kontenera wybierz przycisk **Przekaż obiekt BLOB** .

1. W oknie dialogowym **Przekaż nowy plik** wybierz przycisk **Przeglądaj** , aby określić plik do przekazania, a następnie wprowadź nazwę folderu w polu **folder (opcjonalnie)** .

   ![Próba przekazania pliku do folderu obiektów blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Możesz dodać podfoldery w folderach kontenera, postępując zgodnie z tego samego kroku. Jeśli nie określisz nazwy folderu, plik jest przekazywany do najwyższego poziomu określonego kontenera obiektów blob. Plik pojawi się w określonym folderze w kontenerze.

   ![Folder dodany do kontenera obiektów blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Kliknij dwukrotnie folder lub wybierz klawisz Enter, aby wyświetlić zawartość tego folderu. Gdy jesteś w folderze kontenera, możesz wrócić do katalogu głównego kontenera, wybierając przycisk **Otwórz katalog nadrzędny** (strzałka).

### <a name="to-delete-a-container-folder"></a>Aby usunąć folder kontenera

Usuń wszystkie pliki w folderze.

Ponieważ folderów w kontenerach obiektów blob są foldery wirtualne, nie można utworzyć pustego folderu. Również nie można usunąć folderu, aby usunąć jej zawartość pliku, ale zamiast tego należy usunąć całą zawartość folderu można usunąć folderu, sam.

### <a name="to-filter-blobs-in-a-container"></a>Aby odfiltrować obiekty BLOB w kontenerze

Można filtrować obiektów blob, które są wyświetlane, określając Wspólny prefiks.

Jeśli na przykład wprowadzisz polecenie **Hello** w polu tekstowym filtr, a następnie wybierzesz przycisk **Execute** ( **!** ), zostaną wyświetlone tylko obiekty blob zaczynające się od "Hello".

![Pole tekstowe filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

W polu tekstowym filtru jest rozróżniana wielkość liter i nie obsługuje filtrowanie przy użyciu symboli wieloznacznych. Obiekty BLOB można filtrować tylko według prefiksu. Prefiks mogą zawierać ogranicznik, korzystając z ogranicznika do organizowania obiektów blob w wirtualnej hierarchii. Na przykład filtrowania według prefiksu "HelloFabric /" zwraca wszystkie obiekty BLOB, które zaczynają się od tego ciągu.

### <a name="to-download-blob-data"></a>Aby pobrać dane obiektów blob

W programie Cloud Explorer należy użyć jednej z następujących metod:

* Otwórz menu skrótów dla co najmniej jednego obiektu BLOB, a następnie wybierz polecenie **Otwórz**.
* Wybierz nazwę obiektu BLOB, a następnie wybierz przycisk **Otwórz** .
* Kliknij dwukrotnie nazwę obiektu blob.

Postęp pobierania obiektu BLOB jest wyświetlany w oknie **Dziennik aktywności platformy Azure** .

Obiekt blob zostanie otwarty w domyślny edytor dla tego typu pliku. System operacyjny rozpoznaje typ pliku, plik jest otwierany w aplikacji zainstalowanej lokalnie. W przeciwnym razie zostanie wyświetlony monit wybierz aplikację, która jest odpowiednia dla typu pliku obiektu blob. Plik lokalny, który jest tworzony podczas pobierania obiektu blob jest oznaczony jako tylko do odczytu.

Dane obiektu blob jest lokalnie w pamięci podręcznej i sprawdza, czy czas ostatniej modyfikacji obiektu blob w usłudze Azure Blob storage. Jeśli obiekt blob został zaktualizowany od czasu ostatniego pobrania, zostanie pobrana ponownie. W przeciwnym razie obiekt blob jest ładowany z dysku lokalnego.

Domyślnie obiekt blob jest pobierany do katalogu tymczasowego. Aby pobrać obiekty blob do określonego katalogu, otwórz menu skrótów dla wybranych nazw obiektów blob i wybierz polecenie **Zapisz jako**. Po zapisaniu obiektu blob w ten sposób pliku obiektu blob nie jest otwarty, a plik lokalny jest tworzony za pomocą atrybutów odczytu/zapisu.

### <a name="to-upload-blobs"></a>Do przekazania obiektów blob

Aby przekazać obiekty blob, wybierz przycisk **Przekaż obiekt BLOB** , gdy kontener jest otwarty do wyświetlania w widoku kontenera obiektów BLOB.

Można wybrać jeden lub więcej plików do przekazania, a następnie możesz przekazać pliki dowolnego typu. W oknie **Dziennik aktywności platformy Azure** zostanie wyświetlony postęp przekazywania. Aby uzyskać więcej informacji na temat sposobu pracy z danymi obiektów blob, zobacz [jak korzystać z usługi Azure Blob Storage w środowisku .NET](https://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Aby wyświetlić dzienniki przekazywane do obiektów blob

Jeśli używasz usługi Azure Diagnostics dane dziennika z aplikacji systemu Azure i dzienników zostały przeniesione do swojego konta magazynu, zostanie wyświetlone kontenerów, które platformy Azure utworzone dla tych dzienników. Wyświetlanie dzienników w Eksploratorze serwera jest prosty sposób zidentyfikować problemy z aplikacją, zwłaszcza, jeśli jest został wdrożony na platformie Azure.

Aby uzyskać więcej informacji na temat Diagnostyka Azure, zobacz [zbieranie danych rejestrowania przy użyciu Diagnostyka Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Aby uzyskać adres URL obiektu blob

Otwórz menu skrótów obiektu BLOB, a następnie wybierz polecenie **Kopiuj adres URL**.

### <a name="to-edit-a-blob"></a>Aby edytować obiekt blob

Wybierz obiekt BLOB, a następnie wybierz przycisk **Otwórz obiekt BLOB** .

Plik jest pobierany do tymczasowej lokalizacji i otworzyć na komputerze lokalnym. Po wprowadzeniu zmian ponownie przekazać obiekt blob.

## <a name="work-with-queue-resources"></a>Praca z zasobami queue

Kolejki usługi Storage są hostowane na koncie usługi Azure storage. Aby zezwolić na chmurze usługi ról, aby komunikować się ze sobą oraz z innymi usługami przez mechanizm przekazywania komunikatów, można użyć ich. Kolejki są dostępne programowo za pośrednictwem usługi w chmurze, jak i za pośrednictwem usługi sieci web dla klientów zewnętrznych. Kolejkę można także przejść bezpośrednio przy użyciu Eksploratora serwera w programie Visual Studio.

Podczas tworzenia usługi w chmurze, która używa kolejek można użyć programu Visual Studio do tworzenia kolejek i interaktywnej pracy z nimi podczas tworzenia i testowania kodu.

W Eksploratorze serwera można wyświetlić kolejek na koncie magazynu, tworzenie i usuwanie kolejek, otworzyć kolejkę, aby wyświetlić jego wiadomości i dodawanie komunikatów do kolejki. Podczas otwierania kolejki do wyświetlania, można wyświetlić pojedyncze wiadomości i wykonywać następujące akcje w kolejce, korzystając z przycisków w lewym górnym rogu:

* Odśwież widok kolejki.
* Dodawanie komunikatu do kolejki.
* Usuń z kolejki komunikatów najwyższego poziomu.
* Wyczyść całej kolejki.

Na poniższej ilustracji przedstawiono kolejkę, która zawiera dwa komunikaty:

![Wyświetlanie kolejki](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Aby uzyskać więcej informacji o kolejkach usługi Storage, zobacz [Rozpoczynanie pracy z usługą Azure queue storage przy użyciu platformy .NET](https://go.microsoft.com/fwlink/?LinkID=264702). Aby uzyskać informacje na temat usługi sieci Web dla kolejek usług magazynu, zobacz temat [Omówienie usługi Queue](https://go.microsoft.com/fwlink/?LinkId=264788). Aby uzyskać informacje o sposobach wysyłania komunikatów do kolejki usług magazynu przy użyciu programu Visual Studio, zobacz [wysyłanie komunikatów do kolejki usług magazynu](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Kolejki usługi magazynu różnią się od kolejek usługi Azure Service Bus. Więcej informacji o Service Bus kolejkach znajduje się w temacie [Service Bus Queues, tematy i subskrypcje](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Praca z tabeli zasobów

Usługa Azure Table storage przechowuje duże ilości danych strukturalnych. Usługa jest magazynem danych NoSQL, który przyjmuje uwierzytelnione wywołania z wewnątrz i na zewnątrz chmury platformy Azure. Tabele platformy Azure są idealnym rozwiązaniem do przechowywania strukturalnych danych nierelacyjnych.

### <a name="to-create-a-table"></a>Aby utworzyć tabelę

1. W programie Cloud Explorer wybierz węzeł **tabele** konta magazynu, a następnie wybierz pozycję **Utwórz tabelę**.
1. W oknie dialogowym **Tworzenie tabeli** wprowadź nazwę tabeli.

### <a name="to-view-table-data"></a>Aby wyświetlić dane w tabeli

1. W programie Cloud Explorer otwórz węzeł **Azure** , a następnie otwórz węzeł **Magazyn** .
1. Otwórz węzeł konta magazynu, który Cię interesuje, a następnie otwórz węzeł **tabele** , aby wyświetlić listę tabel dla konta magazynu.
1. Otwórz menu skrótów dla tabeli, a następnie wybierz polecenie **Wyświetl tabelę**.

    ![Tabelę platformy Azure w Eksploratorze rozwiązań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tabela są zorganizowane według jednostek (pokazane w wierszach) i właściwości (pokazane w kolumnach). Na przykład Następna ilustracja przedstawia podmioty wymienione w Projektancie tabel.

### <a name="to-edit-table-data"></a>Aby edytować dane w tabeli

W Projektancie tabel, otwórz menu skrótów dla jednostki (pojedynczy wiersz) lub właściwość (pojedyncza komórka), a następnie wybierz pozycję **Edytuj**.

![Dodawanie lub edytowanie jednostki tabeli](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Jednostki w jednej tabeli nie są wymagane do tego samego zestawu właściwości (kolumny). Mieć na uwadze następujące ograniczenia na wyświetlanie i edytowanie danych w tabeli:

* Nie można wyświetlać ani edytować danych binarnych (`type byte[]`), ale można je przechowywać w tabeli.
* Nie można edytować wartości **PartitionKey** lub **RowKey** , ponieważ magazyn tabel na platformie Azure nie obsługuje tej operacji.
* Nie można utworzyć właściwości o nazwie **timestamp**. Usługi magazynu platformy Azure Użyj właściwości o tej nazwie.
* Jeśli wprowadzisz wartość **daty i godziny** , musisz użyć formatu odpowiedniego dla ustawienia Region i język komputera (na przykład mm/dd/rrrr hh: mm: SS [am | PM] dla angielskiej wersji językowej USA).

### <a name="to-add-entities"></a>Aby dodać jednostki

1. W Projektancie tabel wybierz przycisk **Dodaj jednostkę** .

    ![Dodawanie jednostki przycisku](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. W oknie dialogowym **Dodawanie jednostki** wprowadź wartości właściwości **PartitionKey** i **RowKey** .

    ![Dodaj jednostki, okno dialogowe](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Należy dokładnie wprowadzić wartości. Nie można ich zmienić po zamknięciu okna dialogowego, o ile nie można usunąć jednostki i dodaj go ponownie.

### <a name="to-filter-entities"></a>Aby filtrować jednostek

Można dostosować zestaw jednostek, które pojawiają się w tabeli, jeśli Użyj konstruktora zapytań.

1. Aby otworzyć Konstruktora zapytań, otwórz tabelę do wyświetlenia.
1. Wybierz przycisk **Konstruktor zapytań** na pasku narzędzi widoku tabeli.

    Zostanie wyświetlone okno dialogowe **Konstruktor zapytań** . Poniższa ilustracja przedstawia kwerendę, która jest tworzona w Konstruktorze zapytań.

    ![Konstruktor zapytań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Po zakończeniu tworzenia zapytania, zamknij okno dialogowe. Tekst w formularzu, zapytania pojawia się w polu tekstowym jako filtr usługi danych WCF.
1. Aby uruchomić zapytanie, wybierz ikonę zielony trójkąt.

Można także filtrować dane jednostki, która pojawia się w Projektancie tabel po wprowadzeniu ciąg filtru WCF Data Services bezpośrednio w polu tekstowym filtru. Tego rodzaju ciągu przypomina klauzulę WHERE języka SQL, ale jest wysyłane do serwera jako żądanie HTTP. Aby uzyskać informacje o sposobie konstruowania ciągów filtru, zobacz [konstruowanie ciągów filtru dla projektanta tabel](/azure/vs-azure-tools-table-designer-construct-filter-strings).

Poniższa ilustracja przedstawia przykład ciągu prawidłowego filtru:

![Ciąg filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Odświeżanie magazynu danych

Gdy Eksplorator serwera łączy się lub pobiera dane z konta magazynu, operacja może potrwać do minuty na zakończenie. Jeśli nie można nawiązać połączenia Eksplorator serwera, operacja może przekroczyć limit czasu. Podczas pobierania danych można nadal korzystać z innych części programu Visual Studio. Aby anulować operację, jeśli trwa zbyt długo, wybierz przycisk **Zatrzymaj Odśwież** na pasku narzędzi Eksplorator serwera.

### <a name="to-refresh-blob-container-data"></a>Aby odświeżyć dane w kontenerze obiektów blob

* Wybierz węzeł **obiekty blob** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.
* Aby odświeżyć listę obiektów blob, które są wyświetlane, wybierz przycisk **Execute (wykonaj** ).

### <a name="to-refresh-table-data"></a>Aby odświeżyć dane w tabeli

* Wybierz węzeł **tabele** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.
* Aby odświeżyć listę jednostek, które są wyświetlane w Projektancie tabel, wybierz przycisk **Execute (wykonaj** ) w Projektancie tabel.

### <a name="to-refresh-queue-data"></a>Aby odświeżyć dane w kolejce

Wybierz węzeł **kolejki** pod **magazynem**, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Aby odświeżyć wszystkie elementy w ramach konta magazynu

Wybierz nazwę konta, a następnie wybierz przycisk **Odśwież** na pasku narzędzi Eksplorator serwera.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Dodawanie kont magazynu za pomocą Eksploratora serwera

Istnieją dwa sposoby dodawania konta magazynu za pomocą Eksploratora serwera. Można utworzyć konta magazynu w ramach subskrypcji platformy Azure, lub można dołączyć istniejącego konta magazynu.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Aby utworzyć konto magazynu za pomocą Eksploratora serwera

1. W Eksplorator serwera Otwórz menu skrótów dla węzła **Magazyn** , a następnie wybierz pozycję **Utwórz konto magazynu**.

1. W oknie dialogowym **Tworzenie konta magazynu** wybierz lub wprowadź następujące informacje:

   * Subskrypcja platformy Azure, do której chcesz dodać konto magazynu.
   * Nazwa, którą chcesz użyć dla nowego konta magazynu.
   * Region lub grupa koligacji, (na przykład zachodnie stany USA lub Azja Wschodnia).
   * Typ replikacji, którego chcesz użyć dla konta magazynu, takich jak lokalnie nadmiarowy.

   ![Tworzenie konta usługi Azure storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Wybierz pozycję **Utwórz**.

Nowe konto magazynu zostanie wyświetlone na liście **Magazyn** w Eksplorator rozwiązań.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Można dołączyć istniejącego konta magazynu za pomocą Eksploratora serwera

1. W Eksplorator serwera Otwórz menu skrótów dla węzła usługi Azure **Storage** , a następnie wybierz pozycję **Dołącz magazyn zewnętrzny**.

    ![Dodawanie istniejącego konta magazynu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. W oknie dialogowym **Tworzenie konta magazynu** wybierz lub wprowadź następujące informacje:

   * Nazwa istniejącego konta magazynu, który chcesz dołączyć.
   * Klucz dla wybranego konta magazynu. Ta wartość jest zwykle zapewniany dla Ciebie, po wybraniu konta magazynu. Jeśli chcesz, aby program Visual Studio zapamiętał klucz konta magazynu, zaznacz pole wyboru **Pamiętaj klucz konta** .
   * Protokół nawiązywania połączenia z kontem usługi storage, takie jak HTTP, HTTPS lub niestandardowego punktu końcowego. Aby uzyskać więcej informacji na temat niestandardowych punktów końcowych, zobacz [jak skonfigurować parametry połączenia](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Aby wyświetlić dodatkowych punktów końcowych

Jeśli utworzono konto magazynu za pomocą opcji replikacji **geograficznej dostępu do odczytu** , można wyświetlić jej pomocnicze punkty końcowe, otwierając menu skrótów dla nazwy konta, a następnie wybierając pozycję **Właściwości**.

![Dodatkowej punkty końcowe usługi Storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Aby usunąć konto storage z poziomu Eksploratora serwera

W Eksplorator serwera Otwórz menu skrótów dla nazwy konta, a następnie wybierz polecenie **Usuń**. 

Jeśli usuniesz konto magazynu, wszelkie zapisane informacje o kluczu dla tego konta zostaną również usunięte.

Jeśli usuniesz konto magazynu z poziomu Eksploratora serwera nie ma wpływu na, konta magazynu ani żadnych danych, którą zawiera. Po prostu usuwa odwołanie z poziomu Eksploratora serwera. Aby trwale usunąć konto magazynu, użyj [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Kolejne kroki

Aby dowiedzieć się więcej na temat korzystania z usług Azure Storage, zobacz [wprowadzenie do usługi Azure Storage](/azure/storage/common/storage-introduction).
