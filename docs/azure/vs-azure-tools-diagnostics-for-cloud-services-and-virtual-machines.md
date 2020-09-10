---
title: Diagnostyka dla Cloud Services i maszyn wirtualnych platformy Azure
description: Dowiedz się, jak skonfigurować diagnostykę do debugowania usług Azure Cloud Services i maszyn wirtualnych w programie Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 7e0d261edfd946aed5d459ec732f652448fc46c0
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89740126"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Konfigurowanie diagnostyki dla usług w chmurze i maszyn wirtualnych platformy Azure
W przypadku konieczności rozwiązywania problemów z usługą w chmurze lub maszyną wirtualną platformy Azure można użyć programu Visual Studio, aby łatwiej skonfigurować Diagnostyka Azure. Diagnostyka przechwytuje dane systemowe i rejestruje dane na maszynach wirtualnych i wystąpieniach maszyn wirtualnych, na których działa usługa w chmurze. Dane diagnostyczne są przesyłane do wybranego konta magazynu. Aby uzyskać więcej informacji na temat rejestrowania diagnostycznego na platformie Azure, zobacz [Włączanie rejestrowania diagnostyki dla Web Apps w Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

W tym artykule pokazano, jak używać programu Visual Studio do włączania i konfigurowania Diagnostyka Azure, zarówno przed, jak i po wdrożeniu. Dowiedz się, jak skonfigurować diagnostykę na maszynach wirtualnych platformy Azure, jak wybierać typy zbieranych informacji diagnostycznych oraz jak wyświetlać informacje po ich zebraniu.

Aby skonfigurować Diagnostyka Azure, można użyć jednej z następujących opcji:

* Zmień ustawienia diagnostyki w oknie dialogowym **Konfiguracja diagnostyki** w programie Visual Studio. Ustawienia są zapisywane w pliku o nazwie Diagnostics. wadcfgx (w zestawie Azure SDK 2,4 i starszym, plik ma nazwę Diagnostics. wadcfg). Możesz również bezpośrednio zmodyfikować plik konfiguracji. Jeśli ręcznie zaktualizujesz plik, zmiany konfiguracji zaczną obowiązywać przy następnym wdrożeniu usługi w chmurze na platformie Azure lub w emulatorze.
* Użyj programu Cloud Explorer lub Eksplorator serwera w programie Visual Studio, aby zmienić ustawienia diagnostyki dla usługi w chmurze lub maszyny wirtualnej, która jest uruchomiona.

## <a name="azure-sdk-26-diagnostics-changes"></a>Zmiany diagnostyczne zestawu Azure SDK 2,6
Poniższe zmiany dotyczą zestawu Azure SDK 2,6 i nowszych projektów w programie Visual Studio:

* Emulator lokalny obsługuje teraz diagnostykę. Oznacza to, że można zbierać dane diagnostyczne i upewnić się, że aplikacja tworzy odpowiednie ślady podczas tworzenia i testowania w programie Visual Studio. Parametry połączenia `UseDevelopmentStorage=true` włączają zbieranie danych diagnostycznych podczas korzystania z projektu usługi w chmurze w programie Visual Studio przy użyciu emulatora usługi Azure Storage. Wszystkie dane diagnostyczne są zbierane na koncie magazynu magazynu deweloperskiego.
* Parametry połączenia konta magazynu diagnostyki `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` są przechowywane w pliku konfiguracji usługi (. cscfg). W zestawie Azure SDK 2,5 konto magazynu diagnostyki jest określone w pliku Diagnostics. wadcfgx.

Parametry połączenia działają inaczej w niektórych kluczowych sposobach zestawu Azure SDK 2,6 i nowszych, a w przypadku zestawów Azure SDK 2,4 i starszych:

* W zestawie Azure SDK 2,4 i starszych parametry połączenia są używane jako środowisko uruchomieniowe przez wtyczkę diagnostyki w celu uzyskania informacji o koncie magazynu na potrzeby przesyłania dzienników diagnostycznych.
* W zestawie Azure SDK 2,6 i nowszych program Visual Studio używa parametrów połączenia diagnostyki do konfigurowania rozszerzenia Diagnostyka Azure z odpowiednimi informacjami o koncie magazynu podczas publikowania. Parametry połączenia służą do definiowania różnych kont magazynu dla różnych konfiguracji usługi używanych przez program Visual Studio podczas publikowania. Jednak ponieważ wtyczka diagnostyki nie jest dostępna po zestawie Azure SDK 2,5, plik. cscfg przez samego siebie nie może skonfigurować rozszerzenia diagnostyki. Rozszerzenie należy skonfigurować oddzielnie przy użyciu narzędzi, takich jak Visual Studio lub PowerShell.
* Aby uprościć proces konfigurowania rozszerzenia diagnostyki przy użyciu programu PowerShell, dane wyjściowe pakietu z programu Visual Studio obejmują plik XML konfiguracji publicznej dla rozszerzenia diagnostyki dla każdej roli. Program Visual Studio używa parametrów połączenia diagnostyki, aby wypełnić informacje o koncie magazynu w konfiguracji publicznej. Pliki konfiguracji publicznej są tworzone w folderze rozszerzenia. Pliki konfiguracji publicznej używają wzorca nazewnictwa PaaSDiagnostics. &lt; Nazwa roli \>.PubConfig.xml. Wszystkie wdrożenia oparte na programie PowerShell mogą używać tego wzorca do mapowania każdej konfiguracji do roli.
* [Azure Portal](https://portal.azure.com) używa parametrów połączenia w pliku cscfg w celu uzyskania dostępu do danych diagnostycznych. Dane są wyświetlane na karcie **monitorowanie** . Aby skonfigurować usługę do wyświetlania pełnych danych monitorowania w portalu, wymagane są parametry połączenia.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrowanie projektów do zestawu Azure SDK 2,6 i nowszego
W przypadku migrowania z zestawu Azure SDK 2,5 do zestawu Azure SDK 2,6 lub nowszego, jeśli w pliku wadcfgx określono konto magazynu diagnostyki, konto magazynu pozostaje w tym pliku. Aby skorzystać z elastyczności korzystania z różnych kont magazynu dla różnych konfiguracji magazynu, należy ręcznie dodać parametry połączenia do projektu. W przypadku migrowania projektu z zestawu Azure SDK 2,4 lub starszego do zestawu Azure SDK 2,6 parametry połączenia diagnostyki są zachowywane. Należy jednak pamiętać o zmianach sposobu traktowania parametrów połączenia w zestawie Azure SDK 2,6, opisanym w poprzedniej sekcji.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Jak program Visual Studio Określa konto magazynu diagnostyki
* Jeśli w pliku cscfg określono parametry połączenia diagnostyki, program Visual Studio użyje go do skonfigurowania rozszerzenia diagnostyki podczas publikowania i gdy generuje pliki XML konfiguracji publicznej podczas tworzenia pakietów.
* Jeśli w pliku cscfg nie określono parametrów połączenia diagnostyki, program Visual Studio powraca do korzystania z konta magazynu określonego w pliku. wadcfgx w celu skonfigurowania rozszerzenia diagnostyki do publikowania i generowania plików XML konfiguracji publicznej podczas tworzenia pakietów.
* Parametry połączenia diagnostyki w pliku cscfg mają pierwszeństwo przed kontem magazynu w pliku. wadcfgx. Jeśli w pliku cscfg określono parametry połączenia diagnostyki, program Visual Studio używa tych parametrów połączenia i zignoruje konto magazynu w. wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Co to jest "Aktualizacja parametrów połączenia magazynu programistycznego"... " Zaznacz pole wyboru?
**Parametry połączenia magazynu deweloperskiego aktualizacji dla celów diagnostyki i buforowania przy użyciu poświadczeń konta magazynu Microsoft Azure przy publikowaniu w Microsoft Azure** pole wyboru jest wygodnym sposobem aktualizacji parametrów połączenia konta magazynu deweloperskiego za pomocą konta usługi Azure Storage określonego podczas publikowania.

Na przykład, jeśli zaznaczysz to pole wyboru, a parametry połączenia diagnostyki określają `UseDevelopmentStorage=true` , podczas publikowania projektu na platformie Azure program Visual Studio automatycznie aktualizuje parametry połączenia diagnostyki przy użyciu konta magazynu określonego w Kreatorze publikacji. Jeśli jednak prawdziwe konto magazynu zostało określone jako parametry połączenia diagnostyki, to konto jest używane zamiast tego.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Różnice między funkcjami diagnostyki w zestawie Azure SDK 2,4 i wcześniejszymi a zestawem Azure SDK 2,5 lub nowszym
Jeśli uaktualniasz projekt z zestawu Azure SDK 2,4 i wcześniejszego do zestawu Azure SDK 2,5 lub nowszego, pamiętaj o następujących różnicach w funkcjonalności diagnostyki:

* **Interfejsy API konfiguracji są przestarzałe**. Programistyczna konfiguracja diagnostyki jest dostępna w zestawie Azure SDK 2,4 i starszych wersjach, ale jest przestarzała w zestawie Azure SDK 2,5 lub nowszym. Jeśli konfiguracja diagnostyki jest obecnie zdefiniowana w kodzie, należy ponownie skonfigurować te ustawienia od podstaw w migrowanym projekcie na potrzeby diagnostyki, aby kontynuować pracę. Plik konfiguracji diagnostyki dla zestawu Azure SDK 2,4 to Diagnostics. wadcfg. Plik konfiguracji diagnostyki dla zestawu Azure SDK 2,5 i nowszego to Diagnostics. wadcfgx.
* **Diagnostykę aplikacji usługi w chmurze można skonfigurować tylko na poziomie roli**. W zestawie Azure SDK 2,5 i nowszych nie można skonfigurować diagnostyki dla aplikacji usługi w chmurze na poziomie wystąpienia.
* **Za każdym razem, gdy wdrażana jest aplikacja, konfiguracja diagnostyki zostanie zaktualizowana**. Może to spowodować problemy z parzystością w przypadku zmiany konfiguracji diagnostyki z programu Visual Studio Eksplorator serwera a następnie ponownego wdrożenia aplikacji.
* **W zestawie Azure SDK 2,5 i nowszych Zrzuty awaryjne są konfigurowane w pliku konfiguracji diagnostyki, a nie w kodzie**. Jeśli w kodzie skonfigurowano Zrzuty awaryjne, należy ręcznie przenieść konfigurację z kodu do pliku konfiguracji. Zrzuty awaryjne nie są transferowane podczas migracji do zestawu Azure SDK 2,6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Włącz diagnostykę w projektach usługi w chmurze przed ich wdrożeniem
W programie Visual Studio można zbierać dane diagnostyczne dla ról działających na platformie Azure po uruchomieniu usługi w emulatorze przed wdrożeniem. Wszystkie zmiany ustawień diagnostycznych w programie Visual Studio są zapisywane w pliku konfiguracji Diagnostics. wadcfgx. Te ustawienia określają konto magazynu, w którym są zapisywane dane diagnostyczne podczas wdrażania usługi w chmurze.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Aby włączyć diagnostykę w programie Visual Studio przed wdrożeniem

1. W menu skrótów dla roli wybierz pozycję **Właściwości**. W oknie dialogowym **Właściwości** roli wybierz kartę **Konfiguracja** .
2. W sekcji **Diagnostyka** upewnij się, że zaznaczone jest pole wyboru **Włącz diagnostykę** .

    ![Dostęp do opcji Włącz diagnostykę](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Aby określić konto magazynu dla danych diagnostycznych, wybierz przycisk wielokropka (...).

    ![Określ konto magazynu do użycia](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. W oknie dialogowym **Tworzenie parametrów połączenia magazynu** Określ, czy chcesz nawiązać połączenie za pomocą emulatora usługi Azure Storage, subskrypcji platformy Azure, czy ręcznie wprowadzić poświadczenia.

    ![Konto magazynu — okno dialogowe](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * W przypadku wybrania **emulator magazynu Microsoft Azure**parametry połączenia są ustawiane na `UseDevelopmentStorage=true` .
   * Jeśli wybierzesz **subskrypcję**, możesz wybrać subskrypcję platformy Azure, której chcesz użyć, a następnie wprowadzić nazwę konta. Aby zarządzać subskrypcjami platformy Azure, wybierz pozycję **Zarządzaj kontami**.
   * W przypadku wybrania **ręcznie wprowadzonych poświadczeń**wprowadź nazwę i klucz konta platformy Azure, którego chcesz użyć.
5. Aby wyświetlić okno dialogowe **Konfiguracja diagnostyki** , wybierz pozycję **Konfiguruj**. Każda karta reprezentuje źródło danych diagnostycznych, które można zbierać, z wyjątkiem katalogów **ogólnych** i **dzienników**. Domyślna karta **Ogólne** oferuje następujące opcje zbierania danych diagnostycznych: **tylko błędy**, **wszystkie informacje**i **plany niestandardowe**. Opcja **tylko błędy** domyślne używa najmniejszej ilości miejsca w magazynie, ponieważ nie przesyła ostrzeżeń ani śledzenia komunikatów. Opcja **wszystkie informacje** transferuje najwięcej informacji, korzysta z większości magazynu i dlatego jest najbardziej kosztowną opcją.

   > [!NOTE]
   > Minimalny obsługiwany rozmiar dla przydziału dysku w MB to 50 MB, a rozmiar domyślny to 4 GB. Jeśli jednak zbierasz zrzuty pamięci, zwiększ ten poziom do wyższej wartości, na przykład 10 GB.
   >

    ![Włącz diagnostykę i konfigurację platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Na potrzeby tego przykładu wybierz opcję **Plan niestandardowy** , aby można było dostosować zebrane dane.
7. W polu **limit przydziału dysku w MB** można ustawić ilość miejsca przydzielonego na koncie magazynu na potrzeby danych diagnostycznych. Można zmienić lub zaakceptować wartość domyślną.
8. Na każdej karcie danych diagnostycznych, które mają być zbierane, zaznacz pole wyboru **Włącz transfer \<log type\> dla** . Jeśli na przykład chcesz zbierać Dzienniki aplikacji, na karcie **Dzienniki aplikacji** zaznacz pole wyboru **Włącz transfer dzienników aplikacji** . Określ również inne informacje, które są wymagane przez poszczególne typy danych diagnostycznych. Informacje o konfiguracji poszczególnych kart znajdują się w sekcji **Konfigurowanie źródeł danych diagnostycznych** w dalszej części tego artykułu.
9. Po włączeniu zbierania wszystkich danych diagnostycznych wybierz pozycję **OK**.
10. Uruchom projekt usługi w chmurze platformy Azure w programie Visual Studio w zwykły sposób. Podczas korzystania z aplikacji informacje o dziennikach, które zostały włączone, są zapisywane na określonym koncie usługi Azure Storage.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Włączanie diagnostyki na maszynach wirtualnych platformy Azure
W programie Visual Studio można zbierać dane diagnostyczne dotyczące maszyn wirtualnych platformy Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Aby włączyć diagnostykę na maszynach wirtualnych platformy Azure

1. W Eksplorator serwera wybierz węzeł platformy Azure, a następnie połącz się z subskrypcją platformy Azure, jeśli jeszcze nie masz połączenia.
2. Rozwiń węzeł **Virtual Machines** . Można utworzyć nową maszynę wirtualną lub wybrać istniejący węzeł.
3. W menu skrótów dla wybranej maszyny wirtualnej wybierz pozycję **Konfiguruj**. Zostanie wyświetlone okno dialogowe Konfiguracja maszyny wirtualnej.

    ![Konfigurowanie maszyny wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Jeśli nie jest jeszcze zainstalowana, Dodaj rozszerzenie Diagnostyka Microsoft Monitoring Agent. Dzięki temu rozszerzeniu można zbierać dane diagnostyczne dla maszyny wirtualnej platformy Azure. W obszarze **zainstalowane rozszerzenia**, w polu listy rozwijanej **Wybierz dostępne rozszerzenie** wybierz pozycję **Diagnostyka Microsoft Monitoring Agent**.

    ![Instalowanie rozszerzenia maszyny wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Inne rozszerzenia diagnostyki są dostępne dla maszyn wirtualnych. Aby uzyskać więcej informacji, zobacz [rozszerzenia i funkcje maszyny wirtualnej dla systemu Windows](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Aby dodać rozszerzenie i wyświetlić okno dialogowe **konfiguracji diagnostyki** , wybierz pozycję **Dodaj**.
6. Aby określić konto magazynu, wybierz pozycję **Konfiguruj**, a następnie wybierz przycisk **OK**.

    Każda karta (z wyjątkiem katalogów **General** i Directory **log**) reprezentuje źródło danych diagnostycznych, które można zbierać.

    ![Włącz diagnostykę i konfigurację platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Karta domyślna, **Ogólne**, oferuje następujące opcje zbierania danych diagnostycznych: **tylko błędy**, **wszystkie informacje**i **plany niestandardowe**. Opcja domyślna, **tylko błędy**, wymaga co najmniej magazynu, ponieważ nie przesyła ostrzeżeń ani śledzenia komunikatów. Opcja **wszystkie informacje** transferuje najwięcej informacji i jest z tego powodu najbardziej kosztowną opcją w obszarze magazyn.
7. Na potrzeby tego przykładu wybierz opcję **Plan niestandardowy** , aby można było dostosować zbierane dane.
8. **Limit przydziału dysku w MB** określa, ile miejsca chcesz przydzielić na koncie magazynu na potrzeby danych diagnostycznych. Jeśli chcesz, możesz zmienić wartość domyślną.
9. Na każdej karcie danych diagnostycznych, które mają być zbierane, zaznacz pole wyboru **Włącz \<log type\> transfer dla** .

    Jeśli na przykład chcesz zbierać Dzienniki aplikacji, zaznacz pole wyboru **Włącz transfer dzienników aplikacji** na karcie **Dzienniki aplikacji** . Określ również inne informacje, które są wymagane dla każdego typu danych diagnostycznych. Informacje o konfiguracji poszczególnych kart znajdują się w sekcji **Konfigurowanie źródeł danych diagnostycznych** w dalszej części tego artykułu.
10. Po włączeniu zbierania wszystkich danych diagnostycznych wybierz pozycję **OK**.
11. Zapisz zaktualizowany projekt.

    Komunikat w oknie **Dziennik aktywności Microsoft Azure** wskazuje, że maszyna wirtualna została zaktualizowana.

## <a name="set-up-diagnostics-data-sources"></a>Konfigurowanie źródeł danych diagnostycznych
Po włączeniu zbierania danych diagnostycznych można wybrać dokładnie te źródła danych, które mają być zbierane, oraz informacje zbierane. W następnych sekcjach opisano karty w oknie dialogowym **Konfiguracja diagnostyki** oraz informacje o każdej opcji konfiguracji.

### <a name="application-logs"></a>Dzienniki aplikacji
Dzienniki aplikacji mają informacje diagnostyczne, które są tworzone przez aplikację sieci Web. Jeśli chcesz przechwytywać Dzienniki aplikacji, zaznacz pole wyboru **Włącz transfer dzienników aplikacji** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników aplikacji do konta magazynu, należy zmienić wartość **okres transferu (min)** . Możesz również zmienić ilość informacji przechwytywanych w dzienniku przez ustawienie wartości **poziom dziennika** . Na przykład wybierz pozycję **pełne** , aby uzyskać więcej informacji, lub wybierz opcję **krytyczne** , aby przechwytywać tylko błędy krytyczne. Jeśli masz określonego dostawcę diagnostyki, który emituje Dzienniki aplikacji, możesz przechwytywać dzienniki, dodając identyfikator GUID dostawcy w polu **Identyfikator GUID dostawcy** .

  ![Dzienniki aplikacji](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Aby uzyskać więcej informacji o dziennikach aplikacji, zobacz [Włączanie rejestrowania diagnostycznego dla Web Apps w Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Dzienniki zdarzeń systemu Windows
Aby przechwycić dzienniki zdarzeń systemu Windows, zaznacz pole wyboru **Włącz transfer dzienników zdarzeń systemu Windows** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników zdarzeń do konta magazynu, należy zmienić wartość **okres transferu (min)** . Zaznacz pola wyboru dla typów zdarzeń, które mają być śledzone.

![Dzienniki zdarzeń](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Jeśli używasz zestawu Azure SDK 2,6 lub nowszego i chcesz określić niestandardowe źródło danych, wprowadź je w **\<Data source name\>** polu tekstowym, a następnie wybierz pozycję **Dodaj**. Źródło danych jest dodawane do pliku Diagnostics. cfcfg.

Jeśli korzystasz z zestawu Azure SDK 2,5 i chcesz określić niestandardowe źródło danych, możesz dodać je do `WindowsEventLog` sekcji pliku Diagnostics. wadcfgx, jak w poniższym przykładzie:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Liczniki wydajności
Informacje o liczniku wydajności mogą pomóc w znalezieniu wąskich gardeł systemu i dostosowaniu wydajności systemu i aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie liczników wydajności w aplikacji platformy Azure](/azure/cloud-services/diagnostics-performance-counters). Aby przechwytywać liczniki wydajności, zaznacz pole wyboru **Włącz transfer liczników wydajności** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników zdarzeń do konta magazynu, należy zmienić wartość **okres transferu (min)** . Zaznacz pola wyboru dla liczników wydajności, które mają być śledzone.

![Liczniki wydajności](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Aby śledzić licznik wydajności, który nie znajduje się na liście, wprowadź licznik wydajności przy użyciu sugerowanej składni. a następnie wybierz pozycję **Dodaj**. System operacyjny na maszynie wirtualnej określa, które liczniki wydajności można śledzić. Aby uzyskać więcej informacji na temat składni, zobacz [Określanie ścieżki licznika](/windows/win32/perfctrs/specifying-a-counter-path).

### <a name="infrastructure-logs"></a>Dzienniki infrastruktury
Dzienniki infrastruktury zawierają informacje o infrastrukturze diagnostyki platformy Azure, module RemoteAccess i module RemoteForwarder. Aby zebrać informacje o dziennikach infrastruktury, zaznacz pole wyboru **Włącz transfer dzienników infrastruktury** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników infrastruktury do konta magazynu, należy zmienić wartość **okres transferu (min)** .

![Dzienniki infrastruktury diagnostyki](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Aby uzyskać więcej informacji, zobacz [zbieranie danych rejestrowania przy użyciu Diagnostyka Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="log-directories"></a>Katalogi dzienników
Katalogi dzienników mają zebrane dane z katalogów dzienników dla żądań Internet Information Services (IIS), żądań zakończonych niepowodzeniem lub wybranych folderów. Aby przechwycić katalogi dzienników, zaznacz pole wyboru **Włącz transfer katalogów dzienników** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników do konta magazynu, należy zmienić wartość **okresu transferu (min)** .

Zaznacz pola wyboru dzienników, które mają być zbierane, takie jak **dzienniki usług IIS** i dzienniki **żądań zakończonych niepowodzeniem** . Podane są domyślne nazwy kontenerów magazynu, ale można zmienić ich nazwy.

Dzienniki można przechwytywać z dowolnego folderu. Określ ścieżkę w sekcji **Dziennik z katalogu bezwzględnego** , a następnie wybierz pozycję **Dodaj katalog**. Dzienniki są przechwytywane w określonych kontenerach.

![Katalogi dzienników](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Dzienniki ETW
Jeśli używasz funkcji [Śledzenie zdarzeń systemu Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) i chcesz przechwytywać dzienniki ETW, zaznacz pole wyboru **Włącz transfer dzienników ETW** . Aby zwiększyć lub zmniejszyć interwał między transferem dzienników do konta magazynu, należy zmienić wartość **okresu transferu (min)** .

Zdarzenia są przechwytywane z określonych źródeł zdarzeń i manifestów zdarzeń. Aby określić źródło zdarzenia, w sekcji **źródła zdarzeń** wprowadź nazwę, a następnie wybierz pozycję **Dodaj źródło zdarzenia**. Analogicznie, można określić manifest zdarzenia w sekcji **manifesty zdarzeń** , a następnie wybrać pozycję **Dodaj manifest zdarzeń**.

![Dzienniki ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

Platforma ETW jest obsługiwana w ASP.NET za pomocą klas w przestrzeni nazw [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) . Przestrzeń nazw Microsoft. WindowsAzure. Diagnostics, która dziedziczy z i rozszerza standardowe klasy [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) , umożliwia korzystanie z programu [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) jako struktury rejestrowania w środowisku platformy Azure. Aby uzyskać więcej informacji, zobacz [przejmowanie kontroli nad rejestrowaniem i śledzeniem w Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) i [Włączanie diagnostyki na platformie Azure Cloud Services i maszynach wirtualnych](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Zrzuty awaryjne
Aby przechwytywać informacje o tym, kiedy wystąpienie roli ulega awarii, zaznacz pole wyboru **Włącz transfer zrzutów awaryjnych** . (Ponieważ ASP.NET obsługuje większość wyjątków, jest to zazwyczaj przydatne tylko w przypadku ról procesów roboczych). Aby zwiększyć lub zmniejszyć wartość procentową miejsca do magazynowania na Zrzuty awaryjne, należy zmienić wartość **przydziału katalogu (%)** . Można zmienić kontener magazynu, w którym są przechowywane Zrzuty awaryjne, a także określić, czy ma być przechwytywany **pełny** czy **minipasek** .

Aktualnie śledzone procesy są wymienione na następnym zrzucie ekranu. Zaznacz pola wyboru dla procesów, które mają być przechwytywane. Aby dodać kolejny proces do listy, wprowadź nazwę procesu, a następnie wybierz pozycję **Dodaj proces**.

![Zrzuty awaryjne](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Aby uzyskać więcej informacji, zobacz [przejmowanie kontroli nad rejestrowaniem i śledzeniem w Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) i [Diagnostyka Microsoft Azure część 4: niestandardowe składniki rejestrowania i zmiany Diagnostyka Azure 1,3](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Wyświetlanie danych diagnostycznych
Po zebraniu danych diagnostycznych dla usługi w chmurze lub maszyny wirtualnej można ją wyświetlić.

### <a name="to-view-cloud-service-diagnostics-data"></a>Aby wyświetlić dane diagnostyczne usługi w chmurze
1. Wdróż usługę w chmurze w zwykły sposób, a następnie uruchom ją.
2. Dane diagnostyczne można wyświetlić w raporcie wygenerowanym przez program Visual Studio lub w tabelach na koncie magazynu. Aby wyświetlić dane w raporcie, Otwórz program Cloud Explorer lub Eksplorator serwera, otwórz menu skrótów węzła dla roli, a następnie wybierz pozycję **Wyświetl dane diagnostyczne**.

    ![Wyświetlanie danych diagnostycznych](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Zostanie wyświetlony raport pokazujący dostępne dane.

    ![Raport Diagnostyka Microsoft Azure w programie Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Jeśli najnowsze dane nie są wyświetlane, może być konieczne poczekanie, aż upłynie okres transferu.

    Aby natychmiast zaktualizować dane, wybierz łącze **Odśwież** . Aby automatycznie aktualizować dane, wybierz interwał w polu listy rozwijanej **automatyczne odświeżanie** . Aby wyeksportować dane błędu, wybierz przycisk **Eksportuj do pliku CSV** , aby utworzyć plik z wartościami rozdzielanymi przecinkami, który można otworzyć w arkuszu programu Excel.

    W programie Cloud Explorer lub Eksplorator serwera Otwórz konto magazynu skojarzone ze wdrożeniem.
3. Otwórz tabele diagnostyki w przeglądarce tabel, a następnie przejrzyj zebrane dane. W przypadku dzienników usług IIS i dzienników niestandardowych można otworzyć kontener obiektów BLOB. W poniższej tabeli wymieniono tabele lub kontenery obiektów blob zawierające dane dla różnych plików dziennika. Oprócz danych dla tego pliku dziennika, wpisy tabeli zawierają **EventTickCount**, **DeploymentId**, **role**i **RoleInstance**, aby ułatwić identyfikację, która maszyna wirtualna i rola wygenerowała dane oraz kiedy.

   | Dane diagnostyczne | Opis | Lokalizacja |
   | --- | --- | --- |
   | Dzienniki aplikacji |Rejestruje kod generowany przez wywołanie metod klasy **System. Diagnostics. Trace** . |WADLogsTable |
   | Dzienniki zdarzeń |Dane z dzienników zdarzeń systemu Windows na maszynach wirtualnych. System Windows przechowuje informacje w tych dziennikach, ale aplikacje i usługi również używają dzienników do raportowania błędów lub informacji dziennika. |WADWindowsEventLogsTable |
   | Liczniki wydajności |Dane można zbierać na dowolnym liczniku wydajności, który jest dostępny na maszynie wirtualnej. System operacyjny zawiera liczniki wydajności, w tym wiele statystyk, takich jak użycie pamięci i czas procesora. |WADPerformanceCountersTable |
   | Dzienniki infrastruktury |Dzienniki generowane na podstawie samej infrastruktury diagnostyki. |WADDiagnosticInfrastructureLogsTable |
   | Dzienniki usług IIS |Rejestruje zarejestrowane żądania sieci Web. Jeśli usługa w chmurze pobiera znaczną ilość ruchu, te dzienniki mogą być dłuższe. Dobrym pomysłem jest gromadzenie i przechowywanie tych danych tylko wtedy, gdy ich potrzebujesz. |Dzienniki żądań zakończonych niepowodzeniem można znaleźć w kontenerze obiektów BLOB w obszarze funkcji wad-IIS-failedreqlogs, w ścieżce dla tego wdrożenia, roli i wystąpienia. Kompletne Dzienniki można znaleźć w obszarze funkcji wad-IIS-LogFiles. Wpisy dla każdego pliku są wprowadzane w tabeli WADDirectories. |
   | Zrzuty awaryjne |Udostępnia obrazy binarne procesu usługi w chmurze (zazwyczaj rolę proces roboczy). |funkcji wad-zgniataj — kontener obiektów BLOB |
   | Pliki dziennika niestandardowego |Dzienniki wstępnie zdefiniowanych danych. |Można określić w kodzie lokalizację niestandardowych plików dziennika na koncie magazynu. Na przykład można określić niestandardowy kontener obiektów BLOB. |
4. Jeśli dane dowolnego typu są obcinane, można spróbować zwiększyć bufor dla tego typu danych lub skrócić interwał między transferami danych z maszyny wirtualnej na konto magazynu.
5. Obowiązkowe Sporadyczne przeczyszczanie danych z konta magazynu w celu zmniejszenia ogólnych kosztów magazynowania.
6. Po wykonaniu pełnego wdrożenia plik Diagnostics. cscfg (. wadcfgx for Azure SDK 2,5) zostanie zaktualizowany na platformie Azure, a usługa w chmurze pobiera wszelkie zmiany w konfiguracji diagnostyki. Jeśli zamiast tego zaktualizujesz istniejące wdrożenie, plik. cscfg nie zostanie zaktualizowany na platformie Azure. Można nadal zmieniać ustawienia diagnostyczne, wykonując czynności opisane w następnej sekcji. Aby uzyskać więcej informacji na temat wykonywania pełnego wdrożenia i aktualizowania istniejącego wdrożenia, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Aby wyświetlić dane diagnostyczne maszyny wirtualnej
1. W menu skrótów dla maszyny wirtualnej wybierz pozycję **Wyświetl dane diagnostyczne**.

    ![Wyświetlanie danych diagnostycznych na maszynie wirtualnej platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Zostanie wyświetlone okno dialogowe **Podsumowanie diagnostyki** .

    ![Podsumowanie diagnostyki maszyn wirtualnych platformy Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Jeśli najnowsze dane nie są wyświetlane, może być konieczne poczekanie, aż upłynie okres transferu.

    Aby natychmiast zaktualizować dane, wybierz łącze **Odśwież** . Aby automatycznie aktualizować dane, wybierz interwał w polu listy rozwijanej **automatyczne odświeżanie** . Aby wyeksportować dane błędu, wybierz przycisk **Eksportuj do pliku CSV** , aby utworzyć plik z wartościami rozdzielanymi przecinkami, który można otworzyć w arkuszu programu Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Konfigurowanie diagnostyki usługi w chmurze po wdrożeniu
Jeśli badasz problem z usługą w chmurze, która jest już uruchomiona, możesz chcieć zebrać dane, które nie zostały określone przed pierwotnym wdrożeniem roli. W takim przypadku można rozpocząć zbieranie danych, zmieniając ustawienia w Eksplorator serwera. Można skonfigurować diagnostykę dla jednego wystąpienia lub dla wszystkich wystąpień w roli, w zależności od tego, czy okno dialogowe **Konfiguracja diagnostyki** ma zostać otwarte z menu skrótów dla tego wystąpienia, czy dla roli. W przypadku skonfigurowania węzła roli wszystkie wprowadzone zmiany są stosowane do wszystkich wystąpień. W przypadku skonfigurowania węzła wystąpienie wszystkie wprowadzone zmiany są stosowane tylko do tego wystąpienia.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Aby skonfigurować diagnostykę dla działającej usługi w chmurze
1. W Eksplorator serwera rozwiń węzeł **Cloud Services** , a następnie rozwiń listę węzłów, aby zlokalizować rolę lub wystąpienie (lub oba), które chcesz zbadać.

    ![Konfigurowanie diagnostyki](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. W menu skrótów węzła wystąpienia lub węzła roli wybierz opcję **Aktualizuj ustawienia diagnostyczne**, a następnie wybierz ustawienia diagnostyczne, które chcesz zebrać.

    Informacje o ustawieniach konfiguracji znajdują się w sekcji **Konfigurowanie źródeł danych diagnostycznych** w tym artykule. Informacje o sposobie wyświetlania danych diagnostycznych znajdują się w sekcji **Wyświetlanie danych diagnostycznych** w tym artykule.

    W przypadku zmiany zbierania danych w Eksplorator serwera zmiany będą obowiązywać do momentu całkowitego wdrożenia usługi w chmurze. Jeśli używasz domyślnych ustawień publikowania, zmiany nie są zastępowane. Domyślnym ustawieniem publikowania jest Aktualizowanie istniejącego wdrożenia, a nie wykonanie pełnego ponownego wdrożenia. Aby upewnić się, że ustawienia są jasne w czasie wdrażania, przejdź do karty **Ustawienia zaawansowane** w Kreatorze publikacji, a następnie wyczyść pole wyboru **Aktualizacja wdrożenia** . Po ponownym wdrożeniu za pomocą tego pola wyboru ustawienia są przywracane do tych w pliku. wadcfgx (lub. wadcfg), jak określono za pomocą edytora **Właściwości** dla roli. Jeśli zaktualizujesz wdrożenie, platforma Azure zachowuje wcześniejsze ustawienia.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Rozwiązywanie problemów z usługą w chmurze platformy Azure
Jeśli wystąpią problemy z projektami usług w chmurze, takimi jak rola, która jest zablokowana w stanie "zajęty", wielokrotnie odtwarza lub zgłasza wewnętrzny błąd serwera, istnieją narzędzia i techniki, których można użyć do diagnozowania i rozwiązywania problemu. Aby zapoznać się z konkretnymi przykładami typowych problemów i rozwiązań oraz zapoznać się z omówieniem pojęć i narzędzi, których można użyć do diagnozowania i rozwiązywania tych błędów, zobacz [dane diagnostyczne usługi Azure PaaS COMPUTE](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data).

## <a name="q--a"></a>Pytania i odpowiedzi
**Jaki jest rozmiar buforu i jak jest on duży?**

W każdym wystąpieniu maszyny wirtualnej limity przydziału ograniczają ilość danych diagnostycznych, które można przechowywać w lokalnym systemie plików. Ponadto należy określić rozmiar buforu dla każdego typu danych diagnostycznych, które są dostępne. Ten rozmiar buforu działa jak indywidualny przydział dla tego typu danych. Aby określić całkowity limit przydziału i ilość pamięci, która pozostała, zobacz dolną część okna dialogowego dla typu danych diagnostycznych. Jeśli określisz większą liczbę buforów lub więcej typów danych, zbliżasz się do ogólnego limitu przydziału. Całkowity limit przydziału można zmienić, modyfikując plik konfiguracyjny Diagnostics. wadcfg lub. wadcfgx. Dane diagnostyczne są przechowywane w tym samym systemie plików co dane aplikacji. Jeśli aplikacja używa dużej ilości miejsca na dysku, nie należy zwiększać całkowitego limitu przydziału diagnostyki.

**Co to jest okres transferu i jak długo powinien być?**

Okres transferu to czas, jaki upływa między przechwytywaniem danych. Po każdym okresie transferu dane są przenoszone z lokalnego systemu plików na maszynę wirtualną do tabel na koncie magazynu. Jeśli ilość zbieranych danych przekracza limit przydziału przed końcem okresu transferu, starsze dane są odrzucane. Jeśli utracisz dane, ponieważ dane przekroczą rozmiar buforu lub całkowity limit przydziału, możesz chcieć skrócić okres transferu.

**Jaka strefa czasowa jest sygnaturą czasową?**

Sygnatury czasowe znajdują się w lokalnej strefie czasowej centrum danych, które hostuje usługę w chmurze. Używane są następujące trzy kolumny sygnatur czasowych w tabelach dziennika:

* **PreciseTimeStamp**: sygnatura czasowa ETW zdarzenia. Oznacza to, że czas rejestrowania zdarzenia przez klienta.
* **Sygnatura czasowa**: wartość **PreciseTimeStamp** zaokrąglana w dół do granicy częstotliwości przekazywania. Na przykład jeśli częstotliwość przekazywania wynosi 5 minut, a czas zdarzenia 00:17:12, SYGNATURa czasowa to 00:15:00.
* **Timestamp**: sygnatura czasowa, w której jednostka została utworzona w tabeli platformy Azure.

**Jak mogę zarządzać kosztami podczas zbierania informacji diagnostycznych?**

Ustawienia domyślne (**poziom dziennika** ustawiony na **błąd**i **okres transferu** ustawiony na **1 minutę**) zostały zaprojektowane w celu zminimalizowania kosztów. Koszty obliczeń zwiększają się w przypadku zbierania większej ilości danych diagnostycznych lub zmniejszenia okresu transferu. Nie Zbieraj więcej danych niż jest to potrzebne i nie zapomnij, aby wyłączyć zbieranie danych, gdy nie jest już potrzebne. Zawsze można włączyć ją ponownie, nawet w czasie wykonywania, zgodnie z opisem we wcześniejszej części tego artykułu.

**Jak mogę zbierać Dzienniki żądań zakończonych niepowodzeniem z usług IIS?**

Domyślnie usługi IIS nie zbierają dzienników żądań zakończonych niepowodzeniem. Można skonfigurować usługi IIS do zbierania dzienników żądań zakończonych niepowodzeniem, edytując plik web.config dla roli sieci Web.

**Nie otrzymuję informacji śledzenia z metod RoleEntryPoint, takich jak OnStart. Co jest nie tak?**

Metody **RoleEntryPoint** są wywoływane w kontekście WAIISHost.exe, a nie w usługach IIS. Informacje o konfiguracji w web.config, które zwykle umożliwiają śledzenie, nie są stosowane. Aby rozwiązać ten problem, Dodaj plik. config do projektu roli sieci Web i Nadaj plikowi nazwę zgodną z zestawem danych wyjściowych zawierającym kod **RoleEntryPoint** . W domyślnym projekcie roli sieci Web nazwa pliku. config powinna być WAIISHost.exe.config. Dodaj następujące wiersze do tego pliku:

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

W oknie **Właściwości** ustaw wartość właściwości **Kopiuj do katalogu wyjściowego** na **zawsze Kopiuj**.

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o rejestrowaniu diagnostyki na platformie Azure, zobacz [Włączanie diagnostyki na platformie azure Cloud Services i maszynach wirtualnych](/azure/cloud-services/cloud-services-dotnet-diagnostics) oraz [Włączanie rejestrowania diagnostyki dla Web Apps w Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
