---
title: Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure
description: Debugowanie usługi w chmurze lub maszyny wirtualnej w programie Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 2536a56f76a048cab6a3bf9a5ec026d22fe112a7
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489743"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio

Program Visual Studio udostępnia różne opcje debugowania usług w chmurze platformy Azure i maszyn wirtualnych.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debugowanie usługi w chmurze na komputerze lokalnym

Możesz zaoszczędzić czas i pieniądze, używając emulatora obliczeń platformy Azure do debugowania usługi w chmurze na komputerze lokalnym. Debugowanie usługi lokalnie przed wdrożeniem, można poprawić niezawodność i wydajność bez płacenia za czas obliczeń. Jednak niektóre błędy mogą wystąpić tylko po uruchomieniu usługi w chmurze na samej platformie Azure. Można debugować te błędy, jeśli włączysz debugowanie zdalne podczas publikowania usługi, a następnie dołączysz debuger do wystąpienia roli.

Emulator symuluje usługę Azure Compute i działa w środowisku lokalnym, dzięki czemu można przetestować i debugować usługę w chmurze przed wdrożeniem. Emulator obsługuje cykl życia wystąpień roli i zapewnia dostęp do symulowanych zasobów, takich jak magazyn lokalny. Po debugowaniu lub uruchomieniu usługi z programu Visual Studio automatycznie uruchamia emulator jako aplikację w tle, a następnie wdraża usługę do emulatora. Emulatora można użyć do wyświetlania usługi, gdy działa w środowisku lokalnym. Można uruchomić pełną wersję lub ekspresową wersję emulatora. (Począwszy od platformy Azure 2.3, wersja ekspresowa emulatora jest domyślna.) Zobacz [Używanie emulatora express do uruchamiania i debugowania usługi w chmurze lokalnie](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Aby debugować usługę w chmurze na komputerze lokalnym

1. Na pasku menu wybierz **debugowanie**, **Rozpocznij debugowanie,** aby uruchomić projekt usługi w chmurze platformy Azure. Alternatywnie można nacisnąć klawisz F5. Zostanie wyświetlony komunikat, który jest uruchamiany emulator obliczeń. Po uruchomieniu emulatora ikona zasobnika systemowego to potwierdza.

    ![Emulator platformy Azure w zasobniku systemowym](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Wyświetl interfejs użytkownika emulatora obliczeniowego, otwierając menu skrótów dla ikony platformy Azure w obszarze powiadomień, a następnie wybierz pozycję Pokaż interfejs **użytkownika emulatora obliczeń**.

    W lewym okienku interfejsu użytkownika są wyświetlane usługi, które są obecnie wdrażane w emulatorze obliczeniowym i wystąpienia roli, które są uruchomione każda usługa. Można wybrać usługę lub role, aby wyświetlić cykl życia, rejestrowanie i informacje diagnostyczne w prawym okienku. Jeśli umieścisz fokus w górnym marginesie dołączonego okna, zostanie ono rozwinięte, aby wypełnić prawe okienko.

3. Krok po aplikacji, wybierając polecenia w menu **debugowania** i ustawienie punktów przerwania w kodzie. Podczas przechodzenia przez aplikację w debugerze okienka są aktualizowane o bieżący stan aplikacji. Po zatrzymaniu debugowania wdrożenie aplikacji jest usuwane. Jeśli aplikacja zawiera rolę sieci web i ustawiono właściwość akcji uruchamiania, aby uruchomić przeglądarkę sieci web, program Visual Studio uruchamia aplikację sieci web w przeglądarce. Jeśli zmienisz liczbę wystąpień roli w konfiguracji usługi, należy zatrzymać usługę w chmurze, a następnie ponownie uruchomić debugowanie, aby można było debugować te nowe wystąpienia roli.

    > [!NOTE]
    > Po zatrzymaniu uruchomionego lub debugowania usługi, emulator obliczeń lokalnych i emulator magazynu nie są zatrzymywane. Należy je zatrzymać jawnie z obszaru powiadomień.

## <a name="debug-a-cloud-service-in-azure"></a>Debugowanie usługi w chmurze na platformie Azure

Aby debugować usługę w chmurze z komputera zdalnego, należy włączyć tę funkcję jawnie podczas wdrażania usługi w chmurze, tak aby wymagane usługi (na przykład msvsmon.exe) były instalowane na maszynach wirtualnych, które uruchamiają wystąpienia roli. Jeśli podczas publikowania usługi nie włączono zdalnego debugowania, musisz ponownie opublikować usługę z włączoną debugowaniem zdalnym.

Jeśli włączysz zdalne debugowanie dla usługi w chmurze, nie wykazuje ona obniżonej wydajności ani nie wiąże się z dodatkowymi opłatami. Nie należy używać zdalnego debugowania w usłudze produkcyjnej, ponieważ może to mieć negatywny wpływ na klientów korzystających z usługi.

> [!NOTE]
> Podczas publikowania usługi w chmurze z programu Visual Studio, można włączyć **IntelliTrace** dla wszystkich ról w tej usłudze, które są przeznaczone dla .NET Framework 4 lub .NET Framework 4.5. Za pomocą **IntelliTrace**, można sprawdzić zdarzenia, które wystąpiły w wystąpieniu roli w przeszłości i odtworzyć kontekst z tego czasu. Zobacz [Debugowanie opublikowanej usługi w chmurze za pomocą funkcji IntelliTrace i Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) oraz korzystanie z funkcji [IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Aby włączyć zdalne debugowanie usługi w chmurze

1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.

2. Wybierz środowisko **przejściowe** i konfigurację **debugowania.**

    To tylko wytyczna. Można zdecydować się na uruchomienie środowisk testowych w środowisku produkcyjnym. Jednak może to niekorzystnie wpłynąć na użytkowników, jeśli włączysz debugowanie zdalne w środowisku produkcyjnym. Można wybrać konfigurację wersji, ale konfiguracja debugowania ułatwia debugowanie.

    ![Wybieranie konfiguracji debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Wykonaj zwykłe kroki, ale zaznacz pole wyboru **Włącz debuger zdalny dla wszystkich ról** na karcie Ustawienia **zaawansowane.**

    ![Konfiguracja debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Aby dołączyć debuger do usługi w chmurze na platformie Azure

1. W Eksploratorze serwera rozwiń węzeł usługi w chmurze.

2. Otwórz menu skrótów dla wystąpienia roli lub roli, do którego chcesz dołączyć, a następnie wybierz pozycję **Dołącz debuger**.

    Jeśli debugujesz rolę, debuger programu Visual Studio dołącza do każdego wystąpienia tej roli. Debuger zostanie przerwany w punkcie przerwania dla pierwszego wystąpienia roli, który uruchamia ten wiersz kodu i spełnia wszelkie warunki tego punktu przerwania. Jeśli debugować wystąpienie, debuger dołącza tylko do tego wystąpienia i dzieli się na punkt przerwania tylko wtedy, gdy to konkretne wystąpienie uruchamia ten wiersz kodu i spełnia warunki punktu przerwania.

    ![Dołącz debuger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po debuger dołącza do wystąpienia, debugowania jak zwykle. Debuger automatycznie dołącza do odpowiedniego procesu hosta dla twojej roli. W zależności od roli debuger dołącza do pliku w3wp.exe, WaWorkerHost.exe lub WaIISHost.exe. Aby sprawdzić proces, do którego jest dołączony debuger, rozwiń węzeł wystąpienia w Eksploratorze serwera. Zobacz [architektura roli platformy Azure, aby](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) uzyskać więcej informacji na temat procesów platformy Azure.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Aby zidentyfikować procesy, do których jest dołączony debuger, otwórz okno dialogowe Procesy, wybierając debugowanie, Windows, Procesy. (Klawiatura: Ctrl+Alt+Z) Aby odłączyć określony proces, otwórz menu skrótów, a następnie wybierz pozycję **Odłącz proces**. Możesz też zlokalizować węzeł wystąpienia w Eksploratorze serwera, znaleźć proces, otworzyć menu skrótów, a następnie wybrać pozycję **Odłącz proces**.

    ![Debugowanie procesów](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Unikaj długich postojów w punktach przerwania podczas zdalnego debugowania. Platforma Azure traktuje proces, który został zatrzymany na dłużej niż kilka minut, jako nie odpowiada i zatrzymuje wysyłanie ruchu do tego wystąpienia. Jeśli zatrzymasz się zbyt długo, msvsmon.exe odłączy się od procesu.

Aby odłączyć debuger od wszystkich procesów w wystąpieniu lub roli, otwórz menu skrótów dla roli lub wystąpienia, które debugujesz, a następnie wybierz polecenie **Deuger odłączania**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Ograniczenia zdalnego debugowania na platformie Azure

Z usługi Azure SDK 2.3 zdalne debugowanie ma następujące ograniczenia:

* Po włączeniu zdalnego debugowania nie można opublikować usługi w chmurze, w której żadna rola ma więcej niż 25 wystąpień.
* Debuger używa portów 30400 do 30424, 31400 do 31424 i 32400 do 32424. Jeśli spróbujesz użyć dowolnego z tych portów, nie będzie można opublikować usługi, a jeden z następujących komunikatów o błędach pojawi się w dzienniku aktywności dla platformy Azure:

  * Błąd sprawdzania poprawności pliku cscfg względem pliku csdef.
    Zarezerwowany zakres portów 'zakres' dla punktu końcowego Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector roli "rola" nakłada się z już zdefiniowanym portem lub zakresem.
  * Alokacja nie powiodła się. Ponów próbę później, spróbuj zmniejszyć rozmiar maszyny Wirtualnej lub liczbę wystąpień roli lub spróbuj wdrożyć w innym regionie.

## <a name="debugging-azure-virtual-machines"></a>Debugowanie maszyn wirtualnych platformy Azure

Można debugować programy uruchamiane na maszynach wirtualnych platformy Azure przy użyciu Eksploratora serwera w programie Visual Studio. Po włączeniu zdalnego debugowania na maszynie wirtualnej platformy Azure instaluje rozszerzenie zdalnego debugowania na maszynie wirtualnej. Następnie można dołączyć do procesów na maszynie wirtualnej i debugowania, jak zwykle.

> [!NOTE]
> Maszyny wirtualne utworzone za pośrednictwem stosu menedżera zasobów platformy Azure można zdalnie debugować przy użyciu Eksploratora chmury w programie Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami platformy Azure za pomocą Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Aby debugować maszynę wirtualną platformy Azure

1. W Eksploratorze serwera rozwiń węzeł Maszyny wirtualne i wybierz węzeł maszyny wirtualnej, którą chcesz debugować.

2. Otwórz menu kontekstowe i wybierz pozycję **Włącz debugowanie**. Gdy pojawi się pytanie, czy na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz opcję **Tak**.

    Platforma Azure instaluje zdalne rozszerzenie debugowania na maszynie wirtualnej, aby włączyć debugowanie.

    ![Maszyna wirtualna włącza polecenie debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po zakończeniu instalacji rozszerzenia zdalnego debugowania otwórz menu kontekstowe maszyny wirtualnej i wybierz **pozycję Dołącz debuger...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i pokazuje je w oknie dialogowym Dołącz do procesu.

    ![Dołączanie debugera, polecenie](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. W oknie dialogowym **Dołączanie do procesu** wybierz pozycję **Wybierz,** aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, który chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod macierzysty lub oba.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wybierz procesy, które chcesz debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład można wybrać proces w3wp.exe, jeśli chcesz debugować aplikację sieci web na maszynie wirtualnej. Aby uzyskać więcej informacji, zobacz [Debugować jeden lub więcej procesów w programie Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) i [architekturze roli platformy Azure.](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/)

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Tworzenie projektu sieci Web i maszyny wirtualnej do debugowania

Przed opublikowaniem projektu platformy Azure może okazać się przydatne do przetestowania go w środowisku zawartym w środowisku, które obsługuje debugowanie i testowanie scenariuszy i gdzie można zainstalować programy testowe i monitorujące. Jednym ze sposobów uruchomienia takich testów jest zdalne debugowanie aplikacji na maszynie wirtualnej.

Projekty ASP.NET programu Visual Studio oferują opcję utworzenia poręcznej maszyny wirtualnej, której można użyć do testowania aplikacji. Maszyna wirtualna zawiera często potrzebne punkty końcowe, takie jak PowerShell, pulpit zdalny i WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Aby utworzyć projekt sieci web i maszynę wirtualną do debugowania

1. W programie Visual Studio utwórz nową ASP.NET aplikacji sieci Web.

2. W oknie dialogowym Nowy projekt ASP.NET w sekcji Azure wybierz pozycję **Maszyna wirtualna** w polu listy rozwijanej. Pozostaw zaznaczone pole wyboru **Utwórz zasoby zdalne.** Wybierz **przycisk OK,** aby kontynuować.

    Zostanie wyświetlone okno dialogowe **Tworzenie maszyny wirtualnej na platformie Azure.**

    ![Okno dialogowe Tworzenie ASP.NET projektu sieci Web](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Jeśli nie jesteś jeszcze zalogowany, zostaniesz poproszony o zalogowanie się na swoje konto platformy Azure.

3. Wybierz różne ustawienia maszyny wirtualnej, a następnie wybierz **przycisk OK**. Zobacz [maszyny wirtualne, aby](/azure/virtual-machines/) uzyskać więcej informacji.

    Nazwa wprowadzona dla nazwy DNS będzie nazwą maszyny wirtualnej.

    ![Okno dialogowe Tworzenie maszyny wirtualnej w usłudze Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Platforma Azure tworzy maszynę wirtualną, a następnie aprobuje i konfiguruje punkty końcowe, takie jak pulpit zdalny i wdrażanie w sieci Web

4. Po pełnej konfiguracji maszyny wirtualnej wybierz węzeł maszyny wirtualnej w Eksploratorze serwera.

5. Otwórz menu kontekstowe i wybierz pozycję **Włącz debugowanie**. Gdy pojawi się pytanie, czy na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz opcję **Tak**.

    Platforma Azure instaluje zdalne rozszerzenie debugowania na maszynie wirtualnej, aby włączyć debugowanie.

    ![Maszyna wirtualna włącza polecenie debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publikowanie projektu zgodnie z opisem w [programie Jak: Wdrażanie projektu sieci Web przy użyciu jednego kliknięcia publikuj w programie Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Ponieważ chcesz debugować na maszynie wirtualnej, na stronie **Ustawienia** **kreatora publikowania sieci Web** wybierz **debugowanie** jako konfigurację. Dzięki temu upewnij się, że symbole kodu są dostępne podczas debugowania.

    ![Ustawienia publikowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. W **opcji publikowania plików**wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym,** jeśli projekt został już wdrożony wcześniej.

8. Po opublikowaniu projektu w menu kontekstowym maszyny wirtualnej w Eksploratorze serwera wybierz pozycję **Dołącz debuger...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i pokazuje je w oknie dialogowym Dołącz do procesu.

    ![Dołączanie debugera, polecenie](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. W oknie dialogowym **Dołączanie do procesu** wybierz pozycję **Wybierz,** aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, który chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod macierzysty lub oba.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wybierz procesy, które chcesz debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład można wybrać proces w3wp.exe, jeśli chcesz debugować aplikację sieci web na maszynie wirtualnej. Aby uzyskać więcej informacji, zobacz [Debug One lub Więcej procesów w programie Visual Studio.](https://msdn.microsoft.com/library/jj919165.aspx)

## <a name="next-steps"></a>Następne kroki

* **IntelliTrace** służy do zbierania dziennika wywołań i zdarzeń z serwera wersji. Zobacz [Debugowanie opublikowanej usługi w chmurze za pomocą funkcji IntelliTrace i visual studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Użyj **diagnostyki platformy Azure,** aby rejestrować szczegółowe informacje z kodu uruchomionego w ramach ról, niezależnie od tego, czy role są uruchomione w środowisku programistycznym, czy na platformie Azure. Zobacz [Zbieranie danych rejestrowania przy użyciu usługi Azure Diagnostics](/azure/cloud-services/cloud-services-dotnet-diagnostics).
