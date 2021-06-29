---
title: Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure
description: Debugowanie usługi w chmurze lub maszyny wirtualnej w Visual Studio
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 8669e4636be28d6462c6658a54fc818bae577905
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997673"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio

Visual Studio udostępnia różne opcje debugowania usług w chmurze i maszyn wirtualnych platformy Azure.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debugowanie usługi w chmurze na komputerze lokalnym

Możesz zaoszczędzić czas i pieniądze, używając emulatora Azure Compute do debugowania usługi w chmurze na komputerze lokalnym. Debugowanie usługi lokalnie przed jej wdrożeniem pozwala zwiększyć niezawodność i wydajność bez płacenia za czas obliczeń. Jednak niektóre błędy mogą wystąpić tylko wtedy, gdy uruchamiasz usługę w chmurze na samej platformie Azure. Te błędy można debugować, jeśli podczas publikowania usługi włączysz debugowanie zdalne, a następnie dołączysz debuger do wystąpienia roli.

Emulator symuluje usługę Azure Compute i działa w środowisku lokalnym, dzięki czemu można przetestować i debugować usługę w chmurze przed jej wdrożeniem. Emulator obsługuje cykl życia wystąpień roli i zapewnia dostęp do symulowanych zasobów, takich jak magazyn lokalny. Debugowanie lub uruchamianie usługi z programu Visual Studio spowoduje automatyczne uruchomienie emulatora jako aplikacji w tle, a następnie wdrożenie usługi w emulatorze. Możesz użyć emulatora, aby wyświetlić swoją usługę po jej użyciu w środowisku lokalnym. Możesz uruchomić pełną wersję lub ekspresową wersję emulatora. (Począwszy od platformy Azure 2.3, wersja ekspresowa emulatora jest wersją domyślną). Zobacz [Używanie emulatora Express do uruchamiania i debugowania usługi w chmurze lokalnie.](vs-azure-tools-emulator-express-debug-run.md)

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Aby debugować usługę w chmurze na komputerze lokalnym

1. Na pasku menu wybierz pozycję **Debuguj**  >  **rozpocznij debugowanie,** aby uruchomić projekt usługi w chmurze platformy Azure. Alternatywnie możesz nacisnąć klawisz F5. Zostanie wyświetlony komunikat informujący o uruchomieniu emulatora obliczeń. Gdy emulator zostanie uruchomiony, ikona na pasku zadań potwierdzi to.

    ![Emulator platformy Azure w zasobniku systemu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Wyświetl interfejs użytkownika emulatora obliczeń, otwierając menu skrótów ikony platformy Azure w obszarze powiadomień, a następnie wybierz pozycję Pokaż interfejs użytkownika **emulatora obliczeń.**

    W okienku po lewej stronie interfejsu użytkownika są dostępne usługi, które są obecnie wdrożone w emulatorze obliczeń, oraz wystąpienia roli, w których jest uruchomiona każda usługa. Możesz wybrać usługę lub role do wyświetlania cyklu życia, rejestrowania i informacji diagnostycznych w okienku po prawej stronie. Jeśli umieścisz fokus na górnym marginesie dołączonego okna, zostanie on rozwinięty, aby wypełnić prawe okienko.

3. Aby przejść przez aplikację, wybierz polecenia w menu **Debugowanie** i ustawiając punkty przerwania w kodzie. Podczas krok po kroku aplikacji w debugerze okienka są aktualizowane przy użyciu bieżącego stanu aplikacji. Po zatrzymaniu debugowania wdrożenie aplikacji zostanie usunięte. Jeśli aplikacja zawiera rolę sieci Web i ustawiono właściwość Akcja uruchamiania w celu uruchomienia przeglądarki internetowej, Visual Studio uruchomi aplikację internetową w przeglądarce. Jeśli zmienisz liczbę wystąpień roli w konfiguracji usługi, musisz zatrzymać usługę w chmurze, a następnie ponownie uruchomić debugowanie, aby można było debugować te nowe wystąpienia roli.

    > [!NOTE]
    > Po zatrzymaniu uruchamiania lub debugowania usługi lokalny emulator obliczeń i emulator magazynu nie są zatrzymywane. Należy je jawnie zatrzymać w obszarze powiadomień.

## <a name="debug-a-cloud-service-in-azure"></a>Debugowanie usługi w chmurze na platformie Azure

Aby debugować usługę w chmurze z maszyny zdalnej, należy jawnie włączyć tę funkcję podczas wdrażania usługi w chmurze, tak aby wymagane usługi (na przykład msvsmon.exe) zostały zainstalowane na maszynach wirtualnych z uruchomionymi wystąpieniami roli. Jeśli debugowanie zdalne nie było włączone podczas publikacji usługi, musisz ponownie opublikować usługę z włączonym debugowaniem zdalnym.

Włączenie zdalnego debugowania dla usługi w chmurze nie spowoduje pogorszenia wydajności ani naliczenie dodatkowych opłat. Nie używaj zdalnego debugowania w usłudze produkcyjnej, ponieważ może to mieć negatywny wpływ na klientów, którzy korzystają z usługi.

> [!NOTE]
> Podczas publikowania usługi w chmurze z usługi Visual Studio można włączyć funkcję **IntelliTrace** dla dowolnych ról w tej usłudze, które są docelowe dla usługi .NET Framework 4 lub .NET Framework 4.5. Za pomocą **funkcji IntelliTrace** można zbadać zdarzenia, które wystąpiły w wystąpieniu roli w przeszłości, i odtworzyć kontekst z tego czasu. Zobacz [Debugging a published cloud service with IntelliTrace and Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) Using IntelliTrace (Debugowanie opublikowanej usługi w chmurze za pomocą funkcji IntelliTrace i Visual Studio funkcji [IntelliTrace).](../debugger/intellitrace.md)

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Aby włączyć zdalne debugowanie dla usługi w chmurze

1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Opublikuj.**

2. Wybierz pozycję **Środowisko przejściowe** i **konfigurację Debugowanie.**

    Jest to tylko wy wytyczne. Środowiska testowe można uruchamiać w środowisku produkcyjnym. Jednak włączenie zdalnego debugowania w środowisku produkcyjnym może niekorzystnie wpłynąć na użytkowników. Możesz wybrać konfigurację Wydania, ale konfiguracja Debugowanie ułatwia debugowanie.

    ![Wybieranie konfiguracji debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Wykonaj typowe kroki, ale zaznacz pole wyboru **Włącz debuger** zdalny dla wszystkich ról na karcie **Ustawienia** zaawansowane.

    ![Konfiguracja debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Aby dołączyć debuger do usługi w chmurze na platformie Azure

1. W Eksplorator serwera rozwiń węzeł usługi w chmurze.

2. Otwórz menu skrótów dla roli lub wystąpienia roli, do którego chcesz dołączyć, a następnie wybierz pozycję Attach Debugger (Dołącz **debuger).**

    W przypadku debugowania roli debuger Visual Studio dołączany do każdego wystąpienia tej roli. Debuger przerwie punkt przerwania dla pierwszego wystąpienia roli, które uruchamia ten wiersz kodu i spełnia wszystkie warunki tego punktu przerwania. W przypadku debugowania wystąpienia debuger dołącza tylko do tego wystąpienia i przerywa go w punkcie przerwania tylko wtedy, gdy to określone wystąpienie uruchamia ten wiersz kodu i spełnia warunki punktu przerwania.

    ![Dołączanie debugera](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po dołączeniu debugera do wystąpienia debuguj go w zwykły sposób. Debuger automatycznie dołącza do procesu hosta odpowiedniego dla Twojej roli. W zależności od roli debuger jest dołączany do w3wp.exe, WaWorkerHost.exe lub WaIISHost.exe. Aby sprawdzić proces, do którego jest dołączony debuger, rozwiń węzeł wystąpienia w Eksplorator serwera. Aby uzyskać więcej informacji na temat procesów [platformy Azure,](/archive/blogs/kwill/windows-azure-role-architecture) zobacz Architektura ról platformy Azure.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Aby zidentyfikować procesy, do których jest dołączony debuger, na pasku menu wybierz pozycję **Debuguj** procesy systemu  >  **Windows**  >  i otwórz **okno dialogowe** Procesy. (Klawiatura: Ctrl+Alt+Z) Aby odłączyć określony proces, otwórz jego menu skrótów, a następnie wybierz pozycję **Odłącz proces**. Możesz też zlokalizować węzeł wystąpienia w Eksplorator serwera, znaleźć proces, otworzyć jego menu skrótów, a następnie wybrać pozycję **Odłącz proces**.

    ![Debugowanie procesów](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Unikaj długich zatrzymań w punktach przerwania podczas zdalnego debugowania. Platforma Azure traktuje proces, który został zatrzymany na dłużej niż kilka minut, jako nieosiągalny i przestaje wysyłać ruch do tego wystąpienia. Jeśli zatrzymasz się zbyt długo, msvsmon.exe odłączyć od procesu.

Aby odłączyć debuger od wszystkich procesów w wystąpieniu lub roli, otwórz menu skrótów dla debugera lub wystąpienia, które jest debugowane, a następnie wybierz pozycję **Odłącz debuger.**

## <a name="limitations-of-remote-debugging-in-azure"></a>Ograniczenia debugowania zdalnego na platformie Azure

W zestawie Azure SDK 2.3 debugowanie zdalne ma następujące ograniczenia:

* Po włączeniu zdalnego debugowania nie można opublikować usługi w chmurze, w której dowolna rola ma więcej niż 25 wystąpień.
* Debuger używa portów od 30400 do 30424, 31400 do 31424 i od 32400 do 32424. Jeśli spróbujesz użyć dowolnego z tych portów, nie będzie można opublikować usługi, a w dzienniku aktywności platformy Azure pojawi się jeden z następujących komunikatów o błędach:

  * Błąd podczas sprawdzania poprawności pliku cscfg względem pliku csdef.
    Zarezerwowany zakres portów "zakres" dla punktu końcowego Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector roli "role" nakłada się na już zdefiniowany port lub zakres.
  * Alokacja nie powiodła się. Spróbuj ponownie później, spróbuj zmniejszyć rozmiar maszyny wirtualnej lub liczbę wystąpień roli albo spróbuj wdrożyć w innym regionie.

## <a name="debugging-azure-virtual-machines"></a>Debugowanie maszyn wirtualnych platformy Azure

Programy uruchamiane na maszynach wirtualnych platformy Azure można debugować przy użyciu Eksplorator serwera w Visual Studio. Po włączeniu zdalnego debugowania na maszynie wirtualnej platformy Azure platforma Azure instaluje rozszerzenie debugowania zdalnego na maszynie wirtualnej. Następnie można dołączać do procesów na maszynie wirtualnej i debugować w zwykły sposób.

> [!NOTE]
> Maszyny wirtualne utworzone za pomocą stosu usługi Azure Resource Manager można debugować zdalnie przy użyciu eksploratora chmury w Visual Studio 2015 r. Aby uzyskać więcej informacji, zobacz [Managing Azure Resources with Cloud Explorer (Zarządzanie zasobami platformy Azure za pomocą eksploratora chmury).](vs-azure-tools-resources-managing-with-cloud-explorer.md)

### <a name="to-debug-an-azure-virtual-machine"></a>Aby debugować maszynę wirtualną platformy Azure

1. W Eksplorator serwera rozwiń węzeł Virtual Machines i wybierz węzeł maszyny wirtualnej, którą chcesz debugować.

2. Otwórz menu kontekstowe i wybierz pozycję **Włącz debugowanie.** Gdy zostanie pytanie, czy na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz pozycję **Tak.**

    Platforma Azure instaluje rozszerzenie debugowania zdalnego na maszynie wirtualnej, aby umożliwić debugowanie.

    ![Polecenie włączania debugowania maszyny wirtualnej](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po zakończeniu instalowania rozszerzenia debugowania zdalnego otwórz menu kontekstowe maszyny wirtualnej i wybierz pozycję **Dołącz debuger...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i wyświetla je w **oknie dialogowym Dołączanie do** procesu.

    ![Dołącz polecenie debugera](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. W **oknie dialogowym Dołączanie** do procesu wybierz **pozycję** Wybierz, aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, który chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod natywny lub oba te funkcje.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wybierz procesy, które chcesz debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Możesz na przykład wybrać proces w3wp.exe, jeśli chcesz debugować aplikację internetową na maszynie wirtualnej. Aby [uzyskać więcej informacji,](../debugger/debug-multiple-processes.md) zobacz Debugowanie co najmniej jednego procesu w Visual Studio i Architektura roli platformy [Azure.](/archive/blogs/kwill/windows-azure-role-architecture)

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Tworzenie projektu internetowego i maszyny wirtualnej na potrzeby debugowania

Przed opublikowaniem projektu platformy Azure przydatne może być przetestowanie go w zawartym środowisku, które obsługuje scenariusze debugowania i testowania oraz w miejscu, w którym można instalować programy testowania i monitorowania. Jednym ze sposobów uruchamiania takich testów jest zdalne debugowanie aplikacji na maszynie wirtualnej.

Visual Studio ASP.NET projektu oferują opcję utworzenia przydatnej maszyny wirtualnej, która może być przydatna do testowania aplikacji. Maszyna wirtualna zawiera często potrzebne punkty końcowe, takie jak PowerShell, Pulpit zdalny i WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Aby utworzyć projekt internetowy i maszynę wirtualną na potrzeby debugowania

1. W Visual Studio utwórz nową aplikację internetową ASP.NET Web Application.

2. W oknie dialogowym ASP.NET projekt platformy Azure w sekcji Azure wybierz pozycję **Maszyna** wirtualna w polu listy rozwijanej. Pozostaw **zaznaczone pole wyboru Utwórz** zasoby zdalne. Wybierz **przycisk OK,** aby kontynuować.

    Zostanie **wyświetlone okno dialogowe Tworzenie maszyny wirtualnej** na platformie Azure.

    ![Okno dialogowe ASP.NET projektu internetowego](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Jeśli jeszcze się nie zalogowano, zostanie poproszony o zalogowanie się do konta platformy Azure.

3. Wybierz różne ustawienia dla maszyny wirtualnej, a następnie wybierz przycisk **OK.** Zobacz [Virtual Machines,](/azure/virtual-machines/) aby uzyskać więcej informacji.

    Nazwa w wprowadzeniu nazwy DNS będzie nazwą maszyny wirtualnej.

    ![Okno dialogowe Tworzenie maszyny wirtualnej na platformie Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Platforma Azure tworzy maszynę wirtualną, a następnie apowiuje i konfiguruje punkty końcowe, takie jak Pulpit zdalny i Web Deploy.

4. Po pełnym skonfigurowaniu maszyny wirtualnej wybierz węzeł maszyny wirtualnej w Eksplorator serwera.

5. Otwórz menu kontekstowe i wybierz pozycję **Włącz debugowanie.** Gdy zostanie pytanie, czy na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz pozycję **Tak.**

    Platforma Azure instaluje rozszerzenie zdalnego debugowania na maszynie wirtualnej, aby włączyć debugowanie.

    ![Polecenie włączania debugowania maszyny wirtualnej](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Opublikuj projekt zgodnie z przedstawionych w [te tematu How to: Deploy a Web Project Using One-Click Publish in Visual Studio](/previous-versions/aspnet/dd465337(v=vs.110)). Ponieważ chcesz debugować na maszynie wirtualnej, na stronie Ustawienia kreatora Publikowanie w sieci **Web** wybierz pozycję **Debuguj** jako konfigurację.  Dzięki temu symbole kodu są dostępne podczas debugowania.

    ![Ustawienia publikowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Na stronie **Opcje publikowania plików** wybierz pozycję Usuń dodatkowe pliki w miejscu **docelowym,** jeśli projekt został już wdrożony wcześniej.

8. Po opublikowaniu projektu w menu kontekstowym maszyny wirtualnej w programie Eksplorator serwera pozycję **Attach Debugger...** (Dołącz debuger...

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i wyświetla je w **oknie dialogowym Dołączanie do** procesu.

    ![Dołącz polecenie debugera](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. W **oknie dialogowym Dołączanie** do procesu wybierz **pozycję** Wybierz, aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, które chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod natywny lub oba te funkcje.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wybierz procesy, które chcesz debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Możesz na przykład wybrać proces w3wp.exe, jeśli chcesz debugować aplikację internetową na maszynie wirtualnej. Aby [uzyskać więcej informacji,](../debugger/debug-multiple-processes.md) zobacz Debugowanie jednego lub Visual Studio procesów w programie .

## <a name="next-steps"></a>Następne kroki

* Użyj **funkcji IntelliTrace,** aby zebrać dziennik wywołań i zdarzeń z serwera wydań. Zobacz [Debugging a Published Cloud Service with IntelliTrace and Visual Studio (Debugowanie opublikowanej usługi w chmurze](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md)za pomocą funkcji IntelliTrace i Visual Studio ).

* Użyj **Diagnostyka Azure,** aby rejestrować szczegółowe informacje z kodu uruchomionego w ramach ról, niezależnie od tego, czy role są uruchomione w środowisku dewelopera, czy na platformie Azure. Zobacz [Zbieranie danych rejestrowania przy użyciu Diagnostyka Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).