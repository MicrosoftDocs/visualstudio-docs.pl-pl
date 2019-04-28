---
title: Przeglądanie i zarządzanie zasobami magazynu za pomocą Eksploratora serwera | Dokumentacja firmy Microsoft
description: Przeglądanie i zarządzanie zasobami magazynowania za pomocą Eksploratora serwera
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: f4cfa0abb9a6b61bdb5c27d3dd4243250162aa37
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62427782"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Przeglądanie zasobów magazynu i zarządzanie nimi za pomocą Eksploratora serwera

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Omówienie

Jeśli po zainstalowaniu narzędzi platformy Azure dla programu Microsoft Visual Studio, można wyświetlić obiektów blob, kolejki i tabelę danych z kont magazynu dla platformy Azure. Azure **magazynu** węzła w Eksploratorze serwera wyświetlane dane, które jest kontem emulatora magazynu lokalnego i konta magazynu platformy Azure.

Aby wyświetlić Eksploratora serwera w programie Visual Studio, na pasku menu, wybierz **widoku** > **Eksploratora serwera**. **Magazynu** węzeł zawiera wszystkich kont magazynu, które istnieją w ramach każdej subskrypcji platformy Azure lub certyfikat, który jest połączony z. Jeśli nie ma konta magazynu, można dodać go zgodnie z instrukcjami [w dalszej części tego artykułu](#add-storage-accounts-by-using-server-explorer).

Począwszy od platformy Azure SDK 2.7 umożliwia także programu Cloud Explorer do przeglądania i zarządzania zasobami platformy Azure. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobów platformy Azure za pomocą Eksploratora chmury](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Wyświetlanie i zarządzanie zasobami magazynu w programie Visual Studio

Eksplorator serwera automatycznie pokazuje listę obiektów blob, kolejek i tabel na koncie emulatora magazynu. W ramach emulatora magazynu znajduje się w Eksploratorze serwera w obszarze **magazynu** węzła jako **rozwoju** węzła.

Aby wyświetlić zasoby konta emulatora magazynu, rozwiń węzeł **rozwoju** węzła. Jeśli emulator magazynu nie została uruchomiona, po rozwinięciu **rozwoju** węzła, automatycznie uruchamia. Ten proces może potrwać kilka sekund. Możesz kontynuować pracę w innych obszarach programu Visual Studio, podczas uruchamiania emulatora magazynu.

Do wyświetlania zasobów w ramach konta magazynu, rozwiń węzeł konta magazynu, w Eksploratorze serwera, gdzie widać **obiektów blob**, **kolejek**, i **tabel** węzłów.

## <a name="work-with-blob-resources"></a>Praca z zasobami obiektów blob

**Obiektów blob** węzła Wyświetla listę kontenerów dla wybranego konta magazynu. Kontenery obiektów blob zawierają pliki obiektów blob, a tych obiektów blob można organizować w foldery i podfoldery. Aby uzyskać więcej informacji, zobacz [jak używać magazynu obiektów Blob w języku .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Aby utworzyć kontener obiektów blob

1. Otwórz menu skrótów dla **obiektów blob** węzeł, a następnie wybierz **Utwórz kontener obiektów Blob**.
1. W **Utwórz kontener obiektów Blob** okna dialogowego wprowadź nazwę nowego kontenera.
1. Naciśnij klawisz Enter na klawiaturze lub możesz kliknąć lub nacisnąć poza pole nazwy, aby zapisać kontenera obiektów blob.

   > [!NOTE]
   > Nazwa kontenera obiektu blob musi zaczynać się od liczby (0 – 9) lub małą literą (a – z).

### <a name="to-delete-a-blob-container"></a>Aby usunąć kontener obiektów blob

Otwórz menu skrótów dla kontenera obiektów blob, który chcesz usunąć, a następnie wybierz **Usuń**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Aby wyświetlić listę elementów w kontenerze obiektów blob

Otwórz menu skrótów dla nazwy kontenera obiektów blob na liście, a następnie wybierz pozycję **Otwórz**.

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

1. Wybierz kontener obiektów blob w Eksploratorze chmury. W oknie kontenera wybierz **przekazywanie obiektu Blob** przycisku.

1. W **Przekaż nowy plik** okno dialogowe, wybierz opcję **Przeglądaj** przycisk, aby określić plik, który chcesz przekazać, a następnie wprowadź nazwę folderu, w **folderu (opcjonalnie)** pole.

   ![Próba przekazania pliku do folderu obiektów blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Możesz dodać podfoldery w folderach kontenera, postępując zgodnie z tego samego kroku. Jeśli nie określisz nazwy folderu, plik jest przekazywany do najwyższego poziomu określonego kontenera obiektów blob. Plik pojawi się w określonym folderze w kontenerze.

   ![Folder dodany do kontenera obiektów blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Kliknij dwukrotnie folder lub wybierz klawisz Enter, aby wyświetlić zawartość tego folderu. Gdy jesteś w folderze kontenera, wróć do głównego kontenera, wybierając **Otwórz katalog nadrzędny** przycisku (strzałka).

### <a name="to-delete-a-container-folder"></a>Aby usunąć folder kontenera

Usuń wszystkie pliki w folderze.

Ponieważ folderów w kontenerach obiektów blob są foldery wirtualne, nie można utworzyć pustego folderu. Również nie można usunąć folderu, aby usunąć jej zawartość pliku, ale zamiast tego należy usunąć całą zawartość folderu można usunąć folderu, sam.

### <a name="to-filter-blobs-in-a-container"></a>Aby odfiltrować obiekty BLOB w kontenerze

Można filtrować obiektów blob, które są wyświetlane, określając Wspólny prefiks.

Na przykład, jeśli wprowadzony prefiks **hello** w polu tekstowym filtru, a następnie wybierz **Execute** (**!**) są wyświetlane tylko obiekty BLOB, które zaczynają się ciągiem "hello" przycisku.

![Pole tekstowe filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

W polu tekstowym filtru jest rozróżniana wielkość liter i nie obsługuje filtrowanie przy użyciu symboli wieloznacznych. Obiekty BLOB można filtrować tylko według prefiksu. Prefiks mogą zawierać ogranicznik, korzystając z ogranicznika do organizowania obiektów blob w wirtualnej hierarchii. Na przykład filtrowania według prefiksu "HelloFabric /" zwraca wszystkie obiekty BLOB, które zaczynają się od tego ciągu.

### <a name="to-download-blob-data"></a>Aby pobrać dane obiektów blob

W programie Cloud Explorer należy użyć jednej z następujących metod:

* Otwórz menu skrótów dla jednego lub więcej obiektów blob, a następnie wybierz **Otwórz**.
* Wybierz nazwę obiektu blob, a następnie wybierz pozycję **Otwórz** przycisku.
* Kliknij dwukrotnie nazwę obiektu blob.

Postęp pobierania obiektów blob, który pojawia się w **dziennika aktywności platformy Azure** okna.

Obiekt blob zostanie otwarty w domyślny edytor dla tego typu pliku. System operacyjny rozpoznaje typ pliku, plik jest otwierany w aplikacji zainstalowanej lokalnie. W przeciwnym razie zostanie wyświetlony monit wybierz aplikację, która jest odpowiednia dla typu pliku obiektu blob. Plik lokalny, który jest tworzony podczas pobierania obiektu blob jest oznaczony jako tylko do odczytu.

Dane obiektu blob jest lokalnie w pamięci podręcznej i sprawdza, czy czas ostatniej modyfikacji obiektu blob w usłudze Azure Blob storage. Jeśli obiekt blob został zaktualizowany od czasu ostatniego pobrania, zostanie pobrana ponownie. W przeciwnym razie obiekt blob jest ładowany z dysku lokalnego.

Domyślnie obiekt blob jest pobierany do katalogu tymczasowego. Aby pobrać obiekty BLOB do określonego katalogu, otwórz menu skrótów dla nazwy wybranego obiektu blob, a następnie wybierz **Zapisz jako**. Po zapisaniu obiektu blob w ten sposób pliku obiektu blob nie jest otwarty, a plik lokalny jest tworzony za pomocą atrybutów odczytu/zapisu.

### <a name="to-upload-blobs"></a>Do przekazania obiektów blob

Do przekazania obiektów blob, wybierz **przekazywanie obiektu Blob** przycisku, gdy kontener jest otwarte na potrzeby wyświetlania w widoku do kontenera obiektów blob.

Można wybrać jeden lub więcej plików do przekazania, a następnie możesz przekazać pliki dowolnego typu. **Dziennika aktywności platformy Azure** okno pokazuje postęp przekazywania. Aby uzyskać więcej informacji o tym, jak pracować z danymi obiektów blob, zobacz [jak używać usługi Azure Blob storage na platformie .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Aby wyświetlić dzienniki przekazywane do obiektów blob

Jeśli używasz usługi Azure Diagnostics dane dziennika z aplikacji systemu Azure i dzienników zostały przeniesione do swojego konta magazynu, zostanie wyświetlone kontenerów, które platformy Azure utworzone dla tych dzienników. Wyświetlanie dzienników w Eksploratorze serwera jest prosty sposób zidentyfikować problemy z aplikacją, zwłaszcza, jeśli jest został wdrożony na platformie Azure.

Aby uzyskać więcej informacji na temat usługi Azure Diagnostics, zobacz [zbierania danych rejestrowania przez diagnostykę platformy Azure przy użyciu](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Aby uzyskać adres URL obiektu blob

Otwórz menu skrótów obiektu blob, a następnie wybierz pozycję **URL kopii**.

### <a name="to-edit-a-blob"></a>Aby edytować obiekt blob

Wybierz obiekt blob, a następnie wybierz pozycję **otwarty obiekt Blob** przycisku.

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

Aby uzyskać więcej informacji na temat magazynu usług kolejek, zobacz [Rozpoczynanie pracy z usługą Azure Queue storage przy użyciu platformy .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Uzyskać informacji na temat usługi sieci web dla magazynu usług kolejek, zobacz [pojęcia dotyczące usługi kolejki](http://go.microsoft.com/fwlink/?LinkId=264788). Aby uzyskać informacje o sposobie wysyłania komunikatów do kolejki usługi storage przy użyciu programu Visual Studio, zobacz [wysyłanie komunikatów do kolejki usługi Storage](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Kolejki usługi magazynu różnią się od kolejek usługi Azure Service Bus. Aby uzyskać więcej informacji na temat usługi Service Bus, zobacz [kolejek usługi Service Bus, tematy i subskrypcje](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Praca z tabeli zasobów

Usługa Azure Table storage przechowuje duże ilości danych strukturalnych. Usługa jest magazynem danych NoSQL, który przyjmuje uwierzytelnione wywołania z wewnątrz i na zewnątrz chmury platformy Azure. Tabele platformy Azure są idealnym rozwiązaniem do przechowywania strukturalnych danych nierelacyjnych.

### <a name="to-create-a-table"></a>Aby utworzyć tabelę

1. W programie Cloud Explorer, wybierz **tabel** węzeł konta magazynu, a następnie wybierz **Create Table**.
1. W **Create Table** okna dialogowego wprowadź nazwę tabeli.

### <a name="to-view-table-data"></a>Aby wyświetlić dane w tabeli

1. W Eksploratorze chmury Otwórz **Azure** węzeł, a następnie otwórz **magazynu** węzła.
1. Otwórz węzeł konta magazynu, że są Państwo zainteresowani, a następnie otwórz **tabel** węzeł, aby wyświetlić listę tabel dla konta magazynu.
1. Otwórz menu skrótów dla tabeli, a następnie wybierz **widok tabeli**.

    ![Tabelę platformy Azure w Eksploratorze rozwiązań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tabela są zorganizowane według jednostek (pokazane w wierszach) i właściwości (pokazane w kolumnach). Na przykład Następna ilustracja przedstawia podmioty wymienione w Projektancie tabel.

### <a name="to-edit-table-data"></a>Aby edytować dane w tabeli

W Projektancie tabel, otwórz menu skrótów dla jednostki (pojedynczy wiersz) lub właściwości (jedną komórkę), a następnie wybierz **Edytuj**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Jednostki w jednej tabeli nie są wymagane do tego samego zestawu właściwości (kolumny). Mieć na uwadze następujące ograniczenia na wyświetlanie i edytowanie danych w tabeli:

* Nie można wyświetlić ani edytować danych binarnych (`type byte[]`), ale można go przechowywać w tabeli.
* Nie można edytować **PartitionKey** lub **RowKey** wartości, ponieważ Magazyn tabel na platformie Azure nie obsługuje tej operacji.
* Nie można utworzyć właściwość o nazwie **sygnatura czasowa**. Usługi magazynu platformy Azure Użyj właściwości o tej nazwie.
* Jeśli wprowadzasz **daty/godziny** wartości, należy wykonać, format, który jest odpowiedni do ustawienia regionalne i językowe komputera (na przykład, MM/DD/rrrr hh: mm: [AM | PM] w Stanach Zjednoczonych w języku angielskim).

### <a name="to-add-entities"></a>Aby dodać jednostki

1. W Projektancie tabel wybierz **Dodaj jednostkę** przycisku.

    ![Dodawanie jednostki przycisku](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. W **Dodaj jednostkę** okna dialogowego wprowadź wartości **PartitionKey** i **RowKey** właściwości.

    ![Dodaj jednostki, okno dialogowe](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Należy dokładnie wprowadzić wartości. Nie można ich zmienić po zamknięciu okna dialogowego, o ile nie można usunąć jednostki i dodaj go ponownie.

### <a name="to-filter-entities"></a>Aby filtrować jednostek

Można dostosować zestaw jednostek, które pojawiają się w tabeli, jeśli Użyj konstruktora zapytań.

1. Aby otworzyć Konstruktora zapytań, otwórz tabelę do wyświetlenia.
1. Wybierz **konstruktora zapytań** na listwie narzędziowej widoku tabeli.

    **Konstruktora zapytań** pojawi się okno dialogowe. Poniższa ilustracja przedstawia kwerendę, która jest tworzona w Konstruktorze zapytań.

    ![Konstruktor zapytań](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Po zakończeniu tworzenia zapytania, zamknij okno dialogowe. Tekst w formularzu, zapytania pojawia się w polu tekstowym jako filtr usługi danych WCF.
1. Aby uruchomić zapytanie, wybierz ikonę zielony trójkąt.

Można także filtrować dane jednostki, która pojawia się w Projektancie tabel po wprowadzeniu ciąg filtru WCF Data Services bezpośrednio w polu tekstowym filtru. Tego rodzaju ciągu przypomina klauzulę WHERE języka SQL, ale jest wysyłane do serwera jako żądanie HTTP. Aby uzyskać informacje dotyczące sposobu konstruowania parametry filtru, zobacz [Constructing parametry filtru dla projektanta tabel](vs-azure-tools-table-designer-construct-filter-strings.md).

Poniższa ilustracja przedstawia przykład ciągu prawidłowego filtru:

![Ciąg filtru](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Odświeżanie magazynu danych

Gdy Eksplorator serwera łączy się lub pobiera dane z konta magazynu, operacja może potrwać do minuty na zakończenie. Jeśli nie można nawiązać połączenia z Eksploratora serwera, operacja może upłynąć limit czasu. Gdy dane są pobierane, możesz kontynuować pracę w innych częściach programu Visual Studio. Aby anulować operację, jeśli trwa zbyt długo, wybierz pozycję **Zatrzymaj odświeżanie** przycisk na pasku narzędzi Eksploratora serwera.

### <a name="to-refresh-blob-container-data"></a>Aby odświeżyć dane w kontenerze obiektów blob

* Wybierz **obiektów blob** węźle poniżej **magazynu**, a następnie wybierz pozycję **Odśwież** przycisk na pasku narzędzi Eksploratora serwera.
* Aby odświeżyć listę obiektów blob, który jest wyświetlany, wybierz **Execute** przycisku.

### <a name="to-refresh-table-data"></a>Aby odświeżyć dane w tabeli

* Wybierz **tabel** węźle poniżej **magazynu**, a następnie wybierz pozycję **Odśwież** przycisk na pasku narzędzi Eksploratora serwera.
* Aby odświeżyć listę jednostek, który jest wyświetlany w Projektancie tabel, wybierz **Execute** przycisku w Projektancie tabel.

### <a name="to-refresh-queue-data"></a>Aby odświeżyć dane w kolejce

Wybierz **kolejek** węźle poniżej **magazynu**, a następnie wybierz pozycję **Odśwież** przycisk na pasku narzędzi Eksploratora serwera.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Aby odświeżyć wszystkie elementy w ramach konta magazynu

Wybierz nazwę konta, a następnie wybierz **Odśwież** przycisk na pasku narzędzi Eksploratora serwera.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Dodawanie kont magazynu za pomocą Eksploratora serwera

Istnieją dwa sposoby dodawania konta magazynu za pomocą Eksploratora serwera. Można utworzyć konta magazynu w ramach subskrypcji platformy Azure, lub można dołączyć istniejącego konta magazynu.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Aby utworzyć konto magazynu za pomocą Eksploratora serwera

1. W Eksploratorze serwera, otwórz menu skrótów dla **magazynu** węzeł, a następnie wybierz **Utwórz konto magazynu**.

1. W **Utwórz konto magazynu** okna dialogowego Wybierz lub wprowadź następujące informacje:

   * Subskrypcja platformy Azure, do której chcesz dodać konto magazynu.
   * Nazwa, którą chcesz użyć dla nowego konta magazynu.
   * Region lub grupa koligacji, (na przykład zachodnie stany USA lub Azja Wschodnia).
   * Typ replikacji, którego chcesz użyć dla konta magazynu, takich jak lokalnie nadmiarowy.

   ![Tworzenie konta usługi Azure storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Wybierz **tworzenie**.

Nowe konto magazynu jest wyświetlana w **magazynu** listy w Eksploratorze rozwiązań.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Można dołączyć istniejącego konta magazynu za pomocą Eksploratora serwera

1. W Eksploratorze serwera, otwórz menu skrótów dla platformy Azure **magazynu** węzeł, a następnie wybierz **dołączanie zewnętrznej usługi Storage**.

    ![Dodawanie istniejącego konta magazynu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. W **Utwórz konto magazynu** okna dialogowego Wybierz lub wprowadź następujące informacje:

   * Nazwa istniejącego konta magazynu, który chcesz dołączyć.
   * Klucz dla wybranego konta magazynu. Ta wartość jest zwykle zapewniany dla Ciebie, po wybraniu konta magazynu. Visual Studio do zapamiętania klucza konta magazynu, zaznacz **klucz konta Zapamiętaj** pole wyboru.
   * Protokół nawiązywania połączenia z kontem usługi storage, takie jak HTTP, HTTPS lub niestandardowego punktu końcowego. Aby uzyskać więcej informacji o niestandardowych punktach końcowych, zobacz [jak skonfigurować parametry połączenia](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Aby wyświetlić dodatkowych punktów końcowych

Jeśli utworzono konto magazynu przy użyciu **dostęp do odczytu z magazynu geograficznie nadmiarowego** opcji replikacji można wyświetlić jego dodatkowej punkty końcowe, otwierając menu skrótów dla nazwy konta i następnie wybierz pozycję **właściwości**.

![Dodatkowej punkty końcowe usługi Storage](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Aby usunąć konto storage z poziomu Eksploratora serwera

W Eksploratorze serwera, otwórz menu skrótów dla nazwy konta, a następnie wybierz **Usuń**.

Jeśli usuniesz konto magazynu, wszelkie zapisane informacje o kluczu dla tego konta zostaną również usunięte.

Jeśli usuniesz konto magazynu z poziomu Eksploratora serwera nie ma wpływu na, konta magazynu ani żadnych danych, którą zawiera. Po prostu usuwa odwołanie z poziomu Eksploratora serwera. Aby trwale usunąć konto magazynu, należy użyć [witryny Azure portal](https://portal.azure.com/).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o sposobie używania usługi Azure storage, zobacz [uzyskiwania dostępu do usług Azure Storage](/azure/storage/common/storage-introduction).
