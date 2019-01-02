---
title: Konfigurowanie diagnostyki dla usług Azure Cloud Services i virtual machines | Dokumentacja firmy Microsoft
description: Dowiedz się, jak skonfigurować diagnostykę dla debugowania usług Azure cloud services i maszyn wirtualnych (VM) w programie Visual Studio.
author: ghogen
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7fe172d0baf9f27e8cb1a3858b49e1e1be3b9adb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829055"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Konfigurowanie diagnostyki dla usług w chmurze i maszyn wirtualnych platformy Azure
Gdy zachodzi potrzeba Rozwiązywanie problemów z usługą w chmurze platformy Azure lub maszynie wirtualnej, można użyć programu Visual Studio na łatwiejsze konfigurowanie diagnostyki platformy Azure. Diagnostyka przechwytuje dane systemu i rejestrowania danych na maszynach wirtualnych i wystąpień maszyn wirtualnych, które są uruchamiane usługi w chmurze. Dane diagnostyczne jest przekazywany do wybranego konta magazynu. Aby uzyskać więcej informacji o diagnostyce rejestrowania na platformie Azure, zobacz [Włączanie rejestrowania diagnostycznego dla aplikacji sieci Web w usłudze Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

W tym artykule pokazujemy, jak używać programu Visual Studio, aby włączyć i skonfigurować diagnostykę platformy Azure, przed i po wdrożeniu. Dowiedz się, jak skonfigurować diagnostykę na maszynach wirtualnych platformy Azure, jak wybrać typy informacji diagnostycznych do zbierania i sposób wyświetlania informacji po ich zebraniu.

Jedną z następujących opcji umożliwia konfigurowanie diagnostyki platformy Azure:

* Zmień ustawienia diagnostyki **konfiguracji diagnostyki** okno dialogowe w programie Visual Studio. Ustawienia są zapisywane w pliku o nazwie diagnostics.wadcfgx (w usłudze Azure SDK 2.4 i starszych, plik nosi nazwę diagnostics.wadcfg). Możesz również bezpośrednio zmodyfikować plik konfiguracji. Jeśli ręcznie zaktualizować plik, konfiguracja zmiany zaczęły obowiązywać przy następnym wdrażanie chmury usługi na platformie Azure lub uruchom usługę w emulatorze.
* Użyj Eksploratora chmury lub Eksploratora serwera w programie Visual Studio, aby zmienić ustawienia diagnostyki dla usługi w chmurze lub maszyny wirtualnej, która jest uruchomiona.

## <a name="azure-sdk-26-diagnostics-changes"></a>Platforma Azure zmienia diagnostyki 2.6 zestawu SDK
Następujące zmiany dotyczą 2.6 zestawu SDK platformy Azure i nowszych projektów w programie Visual Studio:

* Lokalne emulator obsługuje teraz diagnostyki. Oznacza to, że można zbierać dane diagnostyczne i upewnij się, że aplikacja tworzy odpowiednie dane śledzenia podczas tworzenia i testowania w programie Visual Studio. Parametry połączenia `UseDevelopmentStorage=true` powoduje włączenie zbierania danych diagnostycznych, po uruchomieniu projektu usługi w chmurze w programie Visual Studio przy użyciu emulatora usługi Azure storage. Wszystkie dane diagnostyczne są zbierane w ramach konta magazynu magazynem projektowym.
* Parametry połączenia konta magazynu diagnostyki `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` są przechowywane w pliku konfiguracji (cscfg) usługi. W systemie Azure SDK 2.5, w pliku diagnostics.wadcfgx określono konto magazynu diagnostyki.

Parametry połączenia, zmieniło pod pewnymi względami klucza w wersji 2.6 zestawu SDK platformy Azure i później w stosunku do Azure SDK 2.4 i starszych wersji:

* W Azure SDK 2.4 lub starszej ciąg połączenia służy jako środowisko uruchomieniowe przez diagnostykę wtyczki Aby uzyskać informacje o koncie magazynu, przesyłania dzienników diagnostycznych.
* W wersji 2.6 zestawu SDK platformy Azure i później Visual Studio używa parametrów połączenia diagnostyki skonfigurować rozszerzenie diagnostyki platformy Azure z informacjami o koncie magazynu odpowiednie podczas publikowania. Parametry połączenia służy do definiowania różnych kont magazynu dla konfiguracji innej usługi, używanych przez program Visual Studio podczas publikowania. Jednak wtyczki Diagnostyka nie jest dostępne po Azure SDK 2.5, przez siebie pliku nie może skonfigurować rozszerzenie diagnostyki. Możesz ustawić rozszerzenie oddzielnie za pomocą narzędzi, takich jak Visual Studio lub programu PowerShell.
* Aby uprościć proces konfigurowania rozszerzenia diagnostyki przy użyciu programu PowerShell, dane wyjściowe pakietu Visual Studio zawiera publiczna Konfiguracja XML dla rozszerzenia diagnostyki dla każdej roli. Visual Studio używa parametrów połączenia diagnostyki do wypełniania informacje o koncie magazynu w konfiguracji publicznego. Pliki konfiguracji publicznego są tworzone w folderze rozszerzenia. Pliki konfiguracji publicznego, użyj wzorca nazewnictwa PaaSDiagnostics. &lt;nazwy roli\>. PubConfig.xml. Wszystkie wdrożenia oparte na programie PowerShell może używać tego wzorca, aby zamapować każdej konfiguracji do roli.
* [Witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) używa parametrów połączenia w pliku .cscfg dostępu do danych diagnostycznych. Dane są wyświetlane na **monitorowanie** kartę. Aby ustawić usługę, aby wyświetlić pełne dane monitorowania w portalu wymagany jest ciąg połączenia.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrację projektów do zestawu SDK platformy Azure w wersji 2.6 lub nowszy
Podczas migracji z zestawu SDK Azure 2.5 do zestawu SDK platformy Azure w wersji 2.6 lub nowszej, i jeśli masz konto magazynu diagnostyki, określone w pliku .wadcfgx, pozostaje na koncie magazynu, w tym pliku. Aby skorzystać z elastyczności przy użyciu różnych kont magazynu dla konfiguracji innego magazynu, należy ręcznie dodać parametry połączenia do swojego projektu. W przypadku migrowania projektów z systemu Azure SDK 2.4 lub jego starszej wersji 2.6 zestawu SDK platformy Azure, Diagnostyka parametry połączenia zostaną zachowane. Należy jednak zwrócić uwagę na zmiany w jak parametry połączenia są traktowane w wersji 2.6 zestawu SDK platformy Azure, opisanego w poprzedniej sekcji.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Jak program Visual Studio Określa konto magazynu diagnostyki
* Jeśli ciąg połączenia diagnostyki jest określona w pliku .cscfg, Visual Studio używa skonfigurować rozszerzenie diagnostyki podczas publikowania i generuje pliki XML konfiguracji publicznego podczas tworzenia pakietów.
* Jeśli nie określono parametrów połączenia diagnostyki w pliku .cscfg, Visual Studio powraca do przy użyciu konta magazynu, który jest określony w pliku .wadcfgx, aby skonfigurować rozszerzenie diagnostyki do publikowania oraz do generowania publiczna Konfiguracja XML pliki podczas pakowania.
* Diagnostyka parametry połączenia w pliku .cscfg mają pierwszeństwo przed konta magazynu w pliku .wadcfgx. Jeśli ciąg połączenia diagnostyki jest określona w pliku .cscfg programu Visual Studio używa tego ciągu połączenia i ignoruje konta magazynu w .wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Do czego służy pole wyboru "Aktualizuj parametry połączenia magazynu rozwoju..."?
**Zaktualizować parametry połączenia magazynu rozwoju dotyczące danych diagnostycznych i pamięci podręcznej przy użyciu poświadczeń konta magazynu Microsoft Azure podczas publikowania w systemie Microsoft Azure** pole wyboru jest wygodny sposób zaktualizować wszelkie magazynem projektowym połączenie konta ciągi przy użyciu konta usługi Azure storage, który jest określany podczas publikowania.

Na przykład, jeśli zaznaczysz to pole wyboru i parametry połączenia diagnostyki Określa `UseDevelopmentStorage=true`, gdy opublikujesz projekt na platformie Azure, programu Visual Studio automatycznie aktualizuje diagnostyki parametry połączenia z kontem magazynu, który określiłeś w Kreator publikowania. Jednak jeśli konto magazynu w rzeczywistych został określony jako parametry połączenia, Diagnostyka, to konto jest używana zamiast tego.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Różnice w funkcjonalności diagnostyki Azure SDK 2.4 i wcześniejszych programu vs. Zestaw Azure SDK 2.5 lub nowszej
Jeśli wykonujesz uaktualnienie projektu z usługi Azure SDK 2.4 i wcześniej do zestawu SDK Azure 2.5 lub nowszej, należy wziąć pod uwagę następujące różnice funkcji diagnostyki:

* **Interfejsy API konfiguracji są przestarzałe**. Konfigurację programistyczną diagnostyki jest dostępna w usłudze Azure SDK 2.4 i starszych, ale jest przestarzała w programie Azure SDK 2.5 i nowszych. Jeśli konfigurację diagnostyki jest obecnie zdefiniowany w kodzie, należy ponownie skonfigurować te ustawienia od podstaw w projekcie zmigrowane do diagnostyki, aby kontynuować pracę. Plik konfiguracji diagnostyki Azure SDK 2.4 jest diagnostics.wadcfg. Plik konfiguracji diagnostyki Azure SDK 2.5 i nowszych jest diagnostics.wadcfgx.
* **Diagnostyka dla aplikacji usługi w chmurze można skonfigurować tylko na poziomie roli**. W Azure SDK 2.5 lub nowszej nie można skonfigurować diagnostykę dla aplikacji usługi w chmurze, na poziomie wystąpienia.
* **Za każdym razem, gdy aplikacja jest wdrażana, zostaje aktualizowana Konfiguracja diagnostyki**. Może to spowodować problemy z parzystością, jeśli zmiana konfiguracji diagnostyki za pomocą Eksploratora serwera w usłudze Visual Studio, a następnie ponownie wdrożyć aplikację.
* **W Azure SDK 2.5 lub nowszej, zrzuty awaryjne skonfigurowanych w pliku konfiguracyjnym Diagnostyka, a nie w kodzie**. Jeśli masz zrzuty awaryjne skonfigurowane w kodzie, musisz ręcznie przetransferować konfiguracji z kodu do pliku konfiguracji. Zrzuty awaryjne nie są przekazywane podczas migracji 2.6 zestawu SDK platformy Azure.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Włącz diagnostykę w projekty usługi w chmurze, przed ich wdrożeniem
W programie Visual Studio może zbierać dane diagnostyczne dla ról, które działają na platformie Azure, gdy usługi jest uruchamiane w emulatorze przed przystąpieniem do wdrożenia. Wszystkie zmiany do ustawień diagnostyki w programie Visual Studio są zapisywane w pliku konfiguracyjnym diagnostics.wadcfgx. Te ustawienia określają konto magazynu, w którym dane diagnostyczne jest zapisywana, gdy wdrażanie usługi w chmurze.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Aby włączyć diagnostykę w programie Visual Studio przed przystąpieniem do wdrożenia

1. W menu skrótów dla roli, wybierz **właściwości**. W tej roli **właściwości** okno dialogowe, wybierz opcję **konfiguracji** kartę.
2. W **diagnostyki** sekcji, upewnij się, że **Włącz diagnostykę** pole wyboru jest zaznaczone.
   
    ![Dostęp do opcji Włącz diagnostykę](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Aby określić konto magazynu dla danych diagnostycznych, wybierz przycisk wielokropka (...).
   
    ![Określ konto magazynu do użycia](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. W **utworzyć parametry połączenia magazynu** okna dialogowego należy określić, czy chcesz nawiązać połączenie przy użyciu emulatora usługi Azure storage, subskrypcję platformy Azure, lub ręcznie wprowadzić poświadczenia.
   
    ![Okno dialogowe konta magazynu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Jeśli wybierzesz **emulator usługi Microsoft Azure storage**, ciąg połączenia jest ustawiona na `UseDevelopmentStorage=true`.
   * Jeśli wybierzesz **subskrypcji**, wybierz subskrypcję platformy Azure, którego chcesz używać i wprowadź nazwę konta. Aby zarządzać subskrypcjami platformy Azure, wybierz pozycję **Zarządzanie kontami**.
   * Jeśli wybierzesz **ręcznie wprowadzić poświadczenia**, wprowadź nazwę i klucz konta platformy Azure, którego chcesz używać.
5. Aby wyświetlić **konfiguracji diagnostyki** okno dialogowe, wybierz opcję **Konfiguruj**. Z wyjątkiem **ogólne** i **katalogi dzienników**, każda karta reprezentuje źródło danych diagnostyki, które można zbierać. Wartość domyślna **ogólne** kartę oferuje następujące diagnostyki opcji zbierania danych: **Tylko błędy**, **wszystkie informacje**, i **niestandardowy plan**. Wartość domyślna **tylko błędy** opcja przy użyciu najmniejszą ilością miejsca, ponieważ nie transferu, ostrzeżenia i komunikaty dotyczące śledzenia. **Wszystkie informacje** opcji przesyła najwięcej informacji, używa najwięcej pamięci masowej i dlatego jest to opcja najbardziej kosztowne.

   > [!NOTE]
   > Minimalny rozmiar obsługiwanych "Dysku limitu przydziału w MB" wynosi 4GB. Jednak przypadku zbierania zrzutów pamięci zwiększyć to wyższej wartości, np. 10GB.
   >
  
    ![Włącz diagnostykę platformy Azure i Konfiguracja](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. W tym przykładzie wybierz **niestandardowy plan** opcji, dzięki czemu możesz dostosować zebranych danych.
7. W **przydział dysku w MB** pole, można ustawić ilości wykorzystanego miejsca można przydzielić na koncie usługi storage dla danych diagnostycznych. Można zmienić lub zaakceptuj wartość domyślną.
8. Na każdej karcie danych diagnostycznych, które mają być zbierane, wybierz **Włączanie przekazywania \<typ dziennika\>**  pole wyboru. Na przykład, jeśli chcesz zbierać Dzienniki aplikacji na **Dzienniki aplikacji** zaznacz **Włączanie przekazywania dzienników aplikacji** pole wyboru. Ponadto określ wszelkie inne informacje wymagane przez każdego typu danych diagnostycznych. Aby uzyskać informacje o konfiguracji dla każdej z kart, zobacz sekcję **konfigurowania źródeł danych diagnostycznych** w dalszej części tego artykułu. 
9. Po włączeniu zbierania danych diagnostycznych chcesz, aby wybrać **OK**.
10. Uruchom projekt usługi w chmurze platformy Azure w programie Visual Studio w zwykły sposób. Ponieważ korzystać z aplikacji, informacje dziennika, które zostały włączone są zapisywane do konta usługi Azure storage, który określiłeś.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Włącz diagnostykę na maszynach wirtualnych platformy Azure
W programie Visual Studio może zbierać dane diagnostyczne maszyn wirtualnych platformy Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Aby włączyć diagnostykę na maszynach wirtualnych platformy Azure

1. W Eksploratorze serwera wybierz węzeł platformy Azure, a następnie połącz się z subskrypcją platformy Azure, jeśli jeszcze nie zostało nawiązane.
2. Rozwiń **maszyn wirtualnych** węzła. Możesz utworzyć nową maszynę wirtualną lub wybierz istniejący węzeł.
3. W menu skrótów dla maszyny wirtualnej, należy wybrać **Konfiguruj**. Zostanie wyświetlone okno dialogowe konfiguracji maszyny wirtualnej.
   
    ![Skonfiguruj maszynę wirtualną platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Jeśli nie jest jeszcze zainstalowany, należy dodać rozszerzenie diagnostyki agenta monitorowania Microsoft. Za pomocą tego rozszerzenia można zbierać dane diagnostyczne dla maszyny wirtualnej platformy Azure. W obszarze **zainstalowane rozszerzenia**w **Wybierz dostępne rozszerzenie** polu listy rozwijanej wybierz **diagnostyki agenta monitorowania Microsoft**.
   
    ![Instalowanie rozszerzenia maszyny wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Inne rozszerzenia diagnostyki są dostępne dla maszyn wirtualnych. Aby uzyskać więcej informacji, zobacz [rozszerzeń maszyn wirtualnych i funkcji dla Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Aby dodać rozszerzenie i wyświetl jego **konfiguracji diagnostyki** okno dialogowe, wybierz opcję **Dodaj**.
6. Aby określić konto magazynu, zaznacz **Konfiguruj**, a następnie wybierz pozycję **OK**.
   
    Każda karta (z wyjątkiem **ogólne** i **katalogi dzienników**) reprezentuje źródło danych diagnostyki, które można zbierać.
   
    ![Włącz diagnostykę platformy Azure i Konfiguracja](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    Na karcie domyślnej **ogólne**, oferuje następujące opcje zbierania danych diagnostycznych: **Tylko błędy**, **wszystkie informacje**, i **niestandardowy plan**. Opcja domyślna **tylko błędy**, przyjmuje najmniejszą ilością miejsca, ponieważ nie transferu, ostrzeżenia i komunikaty dotyczące śledzenia. **Wszystkie informacje** opcji przekazuje najbardziej informacje i dlatego jest opcja najbardziej kosztowne pod względem magazynu.
7. W tym przykładzie wybierz **niestandardowy plan** opcji, dzięki czemu możesz dostosować dane zbierane.
8. **Przydział dysku w MB** pole określa ilość miejsca, które mają zostać przydzielone na koncie usługi storage dla danych diagnostycznych. Jeśli chcesz, możesz zmienić wartość domyślną.
9. Na każdej karcie danych diagnostycznych, które mają być zbierane, wybierz jego **Włączanie przekazywania \<typ dziennika\>**  pole wyboru.
   
    Na przykład jeśli chcesz zbierać Dzienniki aplikacji, wybierz pozycję **Włączanie przekazywania dzienników aplikacji** pole wyboru na **Dzienniki aplikacji** kartę. Ponadto określ wszelkie inne informacje, które są wymagane dla każdego typu danych diagnostycznych. Aby uzyskać informacje o konfiguracji dla każdej z kart, zobacz sekcję **konfigurowania źródeł danych diagnostycznych** w dalszej części tego artykułu.
10. Po włączeniu kolekcji wszystkich danych diagnostycznych, które chcesz zaznaczyć **OK**.
11. Zapisz zaktualizowany projekt.
    
    Wiadomości w **dziennik aktywności platformy Microsoft** okno wskazuje, czy maszyna wirtualna została zaktualizowana.

## <a name="set-up-diagnostics-data-sources"></a>Konfigurowanie źródła danych diagnostycznych
Po włączeniu zbierania danych diagnostycznych, możesz wybrać dokładnie z jakimi źródłami danych, które chcesz zebrać i jakie informacje są zbierane. W kolejnych sekcjach opisano ustawienia na kartach **konfiguracji diagnostyki** okno dialogowe i oznacza, że każda opcja konfiguracji.

### <a name="application-logs"></a>Dzienniki aplikacji
Dzienniki aplikacji mają informacje diagnostyczne, które są generowane przez aplikację sieci web. Jeśli chcesz przechwytywać Dzienniki aplikacji, wybierz **Włączanie przekazywania dzienników aplikacji** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między przekazywania dzienników aplikacji do swojego konta magazynu, należy zmienić **transferu okres (w min)** wartość. Możesz również zmienić ilość informacji przechwyconych w dzienniku, ustawiając **poziom dziennika** wartość. Na przykład wybierz **pełne** Aby uzyskać więcej informacji, lub zaznacz **krytyczny** do przechwycenia tylko błędy krytyczne. Jeśli masz działania diagnostyczne zależne od dostawcy, który emituje Dzienniki aplikacji, można przechwycić dzienniki przez dodanie jego identyfikator GUID w **identyfikator GUID dostawcy** pole.

  ![Dzienniki aplikacji](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Aby uzyskać więcej informacji na temat dzienników aplikacji, zobacz [Włączanie rejestrowania diagnostycznego dla aplikacji sieci Web w usłudze Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Dzienniki zdarzeń Windows
Aby przechwycić Windows, dzienniki zdarzeń, wybierz **Włącz transferu dzienniki zdarzeń Windows** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między przekazywania dzienników zdarzeń do konta magazynu, należy zmienić **transferu okres (w min)** wartość. Zaznacz pola wyboru dla typów zdarzeń, które mają być śledzone.

![Dzienniki zdarzeń](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Jeśli używasz zestawu Azure SDK 2.6 lub nowszej, aby określić niestandardowe źródło danych, wprowadź go w **\<nazwa źródła danych\>** pola tekstowego, a następnie wybierz **Dodaj**. Źródło danych jest dodawane do pliku diagnostics.cfcfg.

Jeśli używasz zestawu SDK Azure 2.5, aby określić niestandardowe źródło danych można dodać go do `WindowsEventLog` sekcji diagnostics.wadcfgx plików, takie jak w poniższym przykładzie:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Liczniki wydajności
Informacje o liczniku wydajności może pomóc w zlokalizować wąskie gardła systemu oraz dostosowywać wydajność systemu i aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenia i używania liczników wydajności w aplikacji Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Aby przechwycić liczników wydajności, wybierz **Włącz transferu liczników wydajności** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między przekazywania dzienników zdarzeń do konta magazynu, należy zmienić **transferu okres (w min)** wartość. Zaznacz pola wyboru dla liczników wydajności, które mają być śledzone.

![Liczniki wydajności](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Aby śledzić licznika wydajności, który nie ma na liście, wprowadź licznika wydajności przy użyciu składni sugerowane. a następnie wybierz **Dodaj**. System operacyjny na maszynie wirtualnej Określa liczniki wydajności, które można śledzić. Aby uzyskać więcej informacji na temat składni, zobacz [ścieżkę licznika](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Protokoly infrastruktury
Dzienniki infrastruktury mają informacje dotyczące infrastruktury diagnostyki platformy Azure, modułu RemoteAccess i modułu RemoteForwarder. Aby zebrać informacje o dziennikach infrastruktury, wybierz **Włącz transferu dzienniki infrastruktury** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między transferu dzienniki infrastruktury do swojego konta magazynu, należy zmienić **transferu okres (w min)** wartość.

![Dzienniki infrastruktury diagnostycznej](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Aby uzyskać więcej informacji, zobacz [zbieranie danych rejestrowania za pomocą diagnostyki Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Katalogi dzienników
Katalogi dzienników zostały dane zbierane z dziennika katalogów do żądań, żądań zakończonych niepowodzeniem lub foldery, które możesz wybrać Internet Information Services (IIS). Aby przechwycić katalogi dzienników, wybierz **Włącz transferu katalogi dzienników** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między przekazywania dzienników do konta magazynu, należy zmienić **transferu okres (w min)** wartość.

Zaznacz pola wyboru dzienników, które mają być zbierane, takich jak **dzienniki usług IIS** i **żądań zakończonych niepowodzeniem** dzienniki. Znajdują się domyślne nazwy kontenera magazynu, ale można zmienić nazwy.

Można przechwycić dzienniki z dowolnego folderu. Określ ścieżkę w **dziennika z bezwzględną katalogu** sekcji, a następnie wybierz **Dodaj katalog**. Dzienniki są przechwytywane z określonego kontenerów.

![Katalogi dzienników](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Dzienniki zdarzeń systemu Windows
Jeśli używasz [Event Tracing for Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) i przechwytywania dzienników zdarzeń systemu Windows, wybierz **Włączanie przekazywania dzienników zdarzeń systemu Windows** pole wyboru. Aby zwiększyć lub zmniejszyć interwał między przekazywania dzienników do konta magazynu, należy zmienić **transferu okres (w min)** wartość.

Zdarzenia są przechwytywane z źródła zdarzeń i manifestów zdarzeń, które określisz. Do określania źródła zdarzeń w **źródła zdarzeń** sekcji, wprowadź nazwę, a następnie wybierz **Dodaj źródło zdarzeń**. Podobnie, można określić manifest zdarzeń w **manifesty zdarzeń** sekcji, a następnie wybierz **Dodaj Manifest zdarzeń**.

![Dzienniki zdarzeń systemu Windows](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW framework jest obsługiwana na platformie ASP.NET przy użyciu klas w [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) przestrzeni nazw. Przestrzeń nazw Microsoft.WindowsAzure.Diagnostics dziedziczy, która rozszerza standardowe [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) klasy, umożliwia korzystanie z [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) jako rejestrowania Struktura w środowisku platformy Azure. Aby uzyskać więcej informacji, zobacz [przejąć kontrolę nad rejestrowanie i śledzenie na platformie Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) i [Włączanie diagnostyki w usługach Azure Cloud Services i virtual machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Zrzuty awaryjne
Aby zebrać informacje o podczas awarii wystąpienia roli, wybierz **włączyć przesyłanie awarii zrzuty** pole wyboru. (Ponieważ ASP.NET obsługuje większość wyjątków, to jest zazwyczaj przydatne tylko w przypadku ról procesów roboczych). Aby zwiększyć lub zmniejszyć wartości procentowej miejsca do magazynowania poświęcone zrzuty awaryjne, należy zmienić **katalog, przydział (%)** wartość. Możesz zmienić kontener magazynu, w którym są przechowywane zrzuty awaryjne oraz określ, czy mają być przechwytywane **pełne** lub **Mini** zrzutu.

Procesy obecnie śledzone są wymienione na następnym zrzucie ekranu. Zaznacz pola wyboru dla procesów, które mają być przechwytywane. Aby dodać inny proces na liście, wprowadź nazwę procesu, a następnie wybierz **proces dodawania**.

![Zrzuty awaryjne](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Aby uzyskać więcej informacji, zobacz [przejąć kontrolę nad rejestrowanie i śledzenie na platformie Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) i [Microsoft Azure Diagnostics część 4: Rejestrowanie niestandardowe składniki i zmiany Azure Diagnostyka 1.3](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Wyświetl dane diagnostyczne
Po po zebraniu danych diagnostycznych dotyczących usługi w chmurze lub maszyny wirtualnej, można je wyświetlić.

### <a name="to-view-cloud-service-diagnostics-data"></a>Aby wyświetlić dane diagnostyki usługi w chmurze
1. Wdrażanie usługi w chmurze w zwykły sposób, a następnie uruchom go.
2. Mogą wyświetlać dane diagnostyczne w raporcie, który generuje programie Visual Studio lub w tabelach, w ramach konta magazynu. Aby wyświetlić dane w raporcie, otwórz Eksploratora chmury lub Eksploratora serwera, otwórz menu skrótów węzła dla roli, a następnie wybierz **widoku danych diagnostycznych**.
   
    ![Wyświetl dane diagnostyczne](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Zostanie wyświetlony raport, który pokazuje dostępne dane.
   
    ![Microsoft Azure Diagnostics raportu w programie Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    Najnowsze dane nie jest widoczne, trzeba czekać na okres transfer może upłynąć.
   
    Aby natychmiast zaktualizować dane, wybierz **Odśwież** łącza. Aby dane aktualizowane automatycznie, wybierz interwał w **automatyczne odświeżanie** pole listy rozwijanej. Aby wyeksportować dane błędu, wybierz **Eksportuj do pliku CSV** przycisk, aby utworzyć plik wartości rozdzielanych przecinkami, które można otworzyć w arkuszu programu Excel.
   
    W programie Cloud Explorer lub w Eksploratorze serwera należy otworzyć konto magazynu, która jest skojarzona z wdrożenia.
3. Otwórz w tabelach diagnostycznych w podglądzie tabeli, a następnie przejrzyj dane, które zostały zebrane. Dzienniki usług IIS i niestandardowe dzienniki można otworzyć kontenera obiektów blob. W poniższej tabeli wymieniono tabele lub kontenery obiektów blob, które zawierają dane dla różnych plikach dziennika. Oprócz danych dla tego pliku dziennika zawiera wpisy tabeli **EventTickCount**, **DeploymentId**, **roli**, i **RoleInstance** , aby pomóc w zidentyfikowaniu, które maszyny wirtualnej i roli wygenerowanych danych i kiedy. 
   
   | Dane diagnostyczne | Opis | Lokalizacja |
   | --- | --- | --- |
   | Dzienniki aplikacji |Dzienniki generowane przez kod przez wywołanie metody **System.Diagnostics.Trace** klasy. |WADLogsTable |
   | Dzienniki zdarzeń |Dane z dzienników zdarzeń Windows na maszynach wirtualnych. Windows przechowuje informacje w tych dziennikach, ale aplikacje i usługi, również przy użyciu dzienników, aby włączyć raportowanie błędów lub rejestrować informacje. |WADWindowsEventLogsTable |
   | Liczniki wydajności |Możesz zbierać dane na wszelkie licznika wydajności, które są dostępne na maszynie wirtualnej. System operacyjny udostępnia liczników wydajności, które obejmują wiele statystyki, takie jak pamięć użycia i czasu procesora. |WADPerformanceCountersTable |
   | Protokoly infrastruktury |Dzienniki, które są generowane na podstawie infrastruktury diagnostyki, sam. |WADDiagnosticInfrastructureLogsTable |
   | Dzienniki usług IIS |Dzienniki służące do rejestrowania żądań sieci web. Jeśli usługa w chmurze pobiera znacznej ilości ruchu sieciowego, dzienniki te mogą być długi. To dobry pomysł, aby zebrać i zapisać te dane, tylko wtedy, gdy ich potrzebujesz. |Można znaleźć dzienników żądanie nie powiodło się w kontenerze obiektów blob w ramach wad-iis-failedreqlogs w ścieżce dla tego wdrożenia, roli i wystąpienia. Możesz znaleźć pełne dzienniki w obszarze wad-iis-logfiles. Dla każdego pliku wpisów w tabeli WADDirectories. |
   | Zrzuty awaryjne |Udostępnia binarnych obrazów usługi w chmurze firmy proces (zazwyczaj rola proces roboczy). |kontener obiektów blob wad — firma zrzutów |
   | Pliki dziennika niestandardowego |Dzienniki danych, który zostanie wstępnie zdefiniowane. |Można określić w kodzie lokalizacji plików dzienników niestandardowych na koncie magazynu. Na przykład można wskazać kontener obiektów blob niestandardowych. |
4. Jeśli zostały obcięte danymi dowolnego typu, możesz spróbować zwiększyć buforu dla tych danych typu lub skrócić interwał między transferów danych z maszyny wirtualnej do swojego konta magazynu.
5. (Opcjonalnie) Usuwanie danych z konta magazynu, co pewien czas w celu zmniejszenia ogólnych kosztów przechowywania.
6. Po wykonaniu pełne wdrożenie, plik diagnostics.cscfg (.wadcfgx dla zestawu SDK Azure 2.5) zostanie zaktualizowany w systemie Azure i usługi w chmurze przejmuje wszystkie zmiany w konfiguracji diagnostyki. Jeśli zamiast tego możesz zaktualizować istniejącego wdrożenia, plik .cscfg nie są aktualizowane na platformie Azure. Nadal można zmienić ustawienia diagnostyki, wykonując kroki opisane w następnej sekcji. Aby uzyskać więcej informacji na temat wykonywania pełnego wdrożenia i aktualizowania istniejącego wdrożenia, zobacz [Kreator publikowania aplikacji Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Aby wyświetlić dane diagnostyczne maszyny wirtualnej
1. W menu skrótów dla maszyny wirtualnej wybierz **dane diagnostyczne widoku**.
   
    ![Wyświetl dane diagnostyczne w maszynie wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    **Souhrn Diagnostiky** pojawi się okno dialogowe.
   
    ![Souhrn diagnostiky maszyny wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    Najnowsze dane nie jest widoczne, trzeba czekać na okres transfer może upłynąć.
   
    Aby natychmiast zaktualizować dane, wybierz **Odśwież** łącza. Aby dane aktualizowane automatycznie, wybierz interwał w **automatyczne odświeżanie** pole listy rozwijanej. Aby wyeksportować dane błędu, wybierz **Eksportuj do pliku CSV** przycisk, aby utworzyć plik wartości rozdzielanych przecinkami, które można otworzyć w arkuszu programu Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Konfigurowanie diagnostyki usługi w chmurze po wdrożeniu
Jeśli badasz problem z usługą w chmurze, która jest już uruchomiona, można zebrać dane, które nie określił zanim pierwotnie wdrożono rolę. W takim przypadku możesz rozpocząć zbieranie danych, zmieniając ustawienia w oknie Eksploratora serwera. Możesz skonfigurować diagnostykę dla pojedynczego wystąpienia lub dla wszystkich wystąpień w roli, w zależności od tego, czy otworzysz **konfiguracji diagnostyki** okno dialogowe z menu skrótów dla tego wystąpienia lub roli. Jeśli skonfigurujesz węzeł roli, wszelkie zmiany, które dotyczą wszystkich wystąpień. Jeśli skonfigurujesz węzła wystąpienia, wszelkie zmiany, które dotyczą tylko tego wystąpienia.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Aby skonfigurować diagnostykę dla uruchomionej usługi w chmurze
1. W oknie Eksploratora serwera rozwiń **usług w chmurze** węzła, a następnie rozwiń listę węzłów, aby zlokalizować rolę wystąpienia (i/lub), którą chcesz zbadać.
   
    ![Konfigurowanie diagnostyki](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. W menu skrótów dla węzła wystąpienia lub węzeł roli wybierz **aktualizacji ustawień diagnostycznych**, a następnie wybierz pozycję Ustawienia diagnostyczne, które mają być zbierane.
   
    Aby uzyskać informacje o ustawieniach konfiguracji, zobacz sekcję **konfigurowania źródeł danych diagnostycznych** w tym artykule. Aby dowiedzieć się, jak wyświetlać dane diagnostyczne, zobacz sekcję **wyświetlać dane diagnostyczne** w tym artykule.
   
    Jeśli zmienisz zbierania danych w Eksploratorze serwera, zmiany obowiązują do momentu, w pełni ponownie wdrożyć usługę w chmurze. Jeśli użytkownik korzysta z domyślnych ustawień publikowania, zmiany nie zostaną zastąpione. Domyślne ustawienie publikowania jest, aby zaktualizować istniejące wdrożenie, a nie robić pełne ponowne wdrożenie. Aby upewnić się, że ustawienia wyczyść w czasie wdrażania, przejdź do **Zaawansowane ustawienia** kartę w Kreatorze publikacji, a następnie wyczyść **wdrożenia aktualizacji** pole wyboru. Podczas ponownego wdrażania za pomocą tego pola wyboru wyczyszczone przywrócone do tych w pliku .wadcfgx (lub .wadcfg) według stawki ustalonej przez **właściwości** edytora dla roli. Jeśli zaktualizujesz wdrożenia, Azure przechowuje wcześniejsze ustawienia.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Rozwiązywanie problemów z usługami w chmurze platformy Azure
Jeśli masz problemy z swoje projekty usługi w chmurze, jak rolę, która zablokowania "zajęty" status wielokrotnie odtwarza, zgłasza błąd wewnętrzny serwera, istnieją narzędzia i techniki, których można użyć, aby zdiagnozować i rozwiązać problem. Przykładem typowe problemy i rozwiązania oraz omówienie pojęć i narzędzi, których można użyć, aby zdiagnozować i naprawić te błędy, zobacz [dane diagnostyki obliczeniowej usługi Azure PaaS](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Pytania i odpowiedzi
**Co to jest rozmiar buforu i rozmiar, jaki ma być?**

W każdym wystąpieniu maszyny wirtualnej przydziały ograniczyć ilość danych diagnostycznych mogą być przechowywane w lokalnym systemie plików. Ponadto należy określić rozmiar bufora dla każdego typu danych diagnostycznych, który jest dostępny. Ten rozmiar buforu zachowuje się jak poszczególne limitu przydziału dla tego typu danych. Aby określić całkowitej ilości i ilość pamięci, która pozostaje, zobacz dolnej części okna dialogowego dla typu danych diagnostycznych. Jeśli określisz zwiększyć bufory lub większą liczbę typów danych, będzie podejście całkowitej ilości. Ogólny limit przydziału można zmienić, modyfikując plik konfiguracyjny diagnostics.wadcfg lub .wadcfgx. Dane diagnostyczne są przechowywane w systemie plików jako dane aplikacji. Jeśli aplikacja używa dużej ilości miejsca na dysku, nie powinna zwiększyć ogólną przydział diagnostyki.

**Co to jest okres transferu i jak długo ma być?**

Okres transferu to ilość czasu, który przechwytuje upłynie między danymi. Po każdym okresie transferu przenoszenia danych z lokalnego systemu plików na maszynę wirtualną do tabel na koncie magazynu. Jeśli ilość zbieranych danych przekracza limit przydziału przed zakończeniem okresu transferu, starsze dane zostaną odrzucone. Jeśli są utraty danych, ponieważ dane przekracza rozmiar buforu lub całkowitej ilości, można skrócić czas transferu.

**Strefy czasowej są sygnatury czasowe w?**

Sygnatury czasowe znajdują się w lokalnej strefie czasowej centrum danych, który jest hostem usługi w chmurze. Używane są następujące trzy godziny sygnatury kolumny w tabelach dziennika:

* **PreciseTimeStamp**: ETW sygnatura czasowa zdarzenia. Oznacza to, że czas zdarzenie jest rejestrowane przez klienta.
* **SYGNATURA CZASOWA**: Wartość **PreciseTimeStamp** zaokrąglone w dół do granic częstotliwość przekazywania. Na przykład częstotliwość usługi przekazywania jest 5 minut i zdarzenia, czas 00:17:12, znacznik czasu: czy 00:15:00.
* **Sygnatura czasowa**: Sygnatura czasowa, w której jednostka została utworzona w tabeli platformy Azure.

**Jak zarządzać kosztami, podczas zbierania informacji diagnostycznych?**

Ustawienia domyślne (**poziom dziennika** równa **błąd**, i **okres transferu** równa **1 minutę**) zaprojektowano w celu zminimalizowania kosztów. Koszty operacji obliczeniowych zwiększyć zbierać więcej danych diagnostycznych lub Zmniejsz okres transferu. Nie zbieraj większej ilości danych niż wymagane i nie należy zapominać wyłączyć zbieranie danych, gdy nie są już potrzebne. Zawsze można włączyć ją ponownie, a nawet w czasie wykonywania, zgodnie z opisem we wcześniejszej części tego artykułu.

**Jak zebrać dzienniki nie powiodło się żądanie za pomocą programu IIS?**

Domyślnie usługi IIS nie zbiera dzienniki żądanie nie powiodło się. Można skonfigurować usługi IIS do zbierania dzienników żądanie nie powiodło się, edytując plik web.config dla roli sieci web.

**Nie uzyskuję informacje o śledzeniu RoleEntryPoint metod, takich jak dla metody OnStart. Co jest nie tak?**

Metody **RoleEntryPoint** są wywoływane w kontekście WAIISHost.exe nie w usługach IIS. Informacje o konfiguracji w pliku web.config, który normalnie umożliwia włączenie śledzenia nie ma zastosowania. Aby rozwiązać ten problem, Dodaj plik .config do projektu roli sieci web i nazwę pliku na zgodną z zestawu danych wyjściowych, który zawiera **RoleEntryPoint** kodu. W projekcie roli sieć web domyślna nazwa pliku .config powinien być WAIISHost.exe.config. Dodaj następujące wiersze do tego pliku:

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

W **właściwości** oknie **Kopiuj do katalogu wyjściowego** właściwości **zawsze Kopiuj**.

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o diagnostyce rejestrowania na platformie Azure, zobacz [Włączanie diagnostyki w usługach Azure Cloud Services i virtual machines](/azure/cloud-services/cloud-services-dotnet-diagnostics) i [Włączanie rejestrowania diagnostycznego dla aplikacji sieci Web w usłudze Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
