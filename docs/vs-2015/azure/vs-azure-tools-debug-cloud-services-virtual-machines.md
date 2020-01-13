---
title: Debugowanie usługi w chmurze platformy Azure lub maszynie wirtualnej
description: Debugowanie usługi w chmurze lub maszyny wirtualnej w programie Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: ac1f47d3daabf800a308d73727f750f971ace4e6
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919166"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debugowanie usługi w chmurze platformy Azure lub maszynie wirtualnej w programie Visual Studio

Program Visual Studio zapewnia różne opcje debugowania usług Azure cloud services i maszyn wirtualnych.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debugowanie usługi w chmurze na komputerze lokalnym

Możesz zaoszczędzić czas i pieniądze za pomocą usługi Azure compute emulatora do debugowania na maszynie lokalnej usługi w chmurze. Debugowanie usługi lokalnie przed przystąpieniem do wdrażania, może zwiększyć niezawodność i wydajność bez konieczności płacenia za czas obliczeń. Jednak niektóre mogą wystąpić błędy, tylko po uruchomieniu usługi w chmurze na platformie Azure sam. Te błędy można debugować po włączeniu zdalnego debugowania, gdy Opublikuj usługę i następnie dołączyć debuger do wystąpienia roli.

Emulator usługi Azure Compute symuluje i jest uruchamiana w środowisku lokalnym, tak aby umożliwić testowanie i debugowanie usługi w chmurze, przed przystąpieniem do wdrażania. Emulator obsługuje cyklu życia wystąpienia ról użytkownika i zapewnia dostęp do zasobów symulowane, takich jak magazyn lokalny. Podczas debugowania i uruchamiania usługi za pomocą programu Visual Studio automatycznie uruchomienie emulatora, jako tło aplikacji, a następnie wdraża usługi w emulatorze. Emulator można użyć, aby wyświetlić usługi, po uruchomieniu w środowisku lokalnym. Możesz uruchomić pełną wersję lub wersja ekspresowa emulatora. (Począwszy od platformy Azure 2,3, wersja Express emulatora jest domyślna). Zobacz [Używanie emulatora Express do lokalnego uruchamiania i debugowania usługi w chmurze](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Debugowanie usługi w chmurze na komputerze lokalnym

1. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia projekt usługi w chmurze platformy Azure. Alternatywnie naciśnij klawisz F5. Zostanie wyświetlony komunikat, który rozpocznie się emulatora obliczeń. Po uruchomieniu emulatora ikoną w zasobniku systemowym potwierdza go.

    ![Emulator usługi Azure na pasku zadań](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Wyświetlanie interfejsu użytkownika dla emulatora obliczeń, otwierając menu skrótów dla usługi Azure ikony w obszarze powiadomień, a następnie wybierz **Pokaż interfejs użytkownika emulatora obliczeń**.

    Okienka po lewej stronie interfejsu użytkownika zawiera usługi, które są aktualnie zaimplementowane w emulatorze obliczeń i wystąpień roli, które każda usługa jest uruchomiona. Możesz wybrać usługi lub role do wyświetlenia w okienku po prawej stronie cyklu życia, rejestrowanie i informacji diagnostycznych. Jeśli umieścisz fokus na górnym marginesie dołączone okno rozwija Wypełnij okienku po prawej stronie.

3. Krok za pośrednictwem aplikacji, wybierając polecenia na **debugowania** menu i ustawiania punktów przerwania w kodzie. Podczas wykonywania kroków za pomocą aplikacji w debugerze okienka zostaną zaktualizowane o bieżący stan aplikacji. Gdy zatrzymasz debugowanie, wdrażanie aplikacji zostaną usunięte. Jeśli aplikacja zawiera rolę sieci web i ustawiono właściwość akcji uruchamiania do uruchomienia przeglądarki sieci web, programu Visual Studio uruchamia aplikację sieci web w przeglądarce. Jeśli zmienisz liczbę wystąpień roli w konfiguracji usługi, należy zatrzymać usługi w chmurze i ponownie uruchom debugowanie tak, aby można było debugować te nowe wystąpienia roli.

    > [!NOTE]
    > Po zatrzymaniu lub debugowaniu usługi lokalny emulator obliczeniowy i emulator magazynu nie zostaną zatrzymane. Należy zatrzymać je jawnie przy użyciu obszaru powiadomień.

## <a name="debug-a-cloud-service-in-azure"></a>Debugowanie usługi w chmurze na platformie Azure

Aby debugować usługę w chmurze z komputera zdalnego, należy włączyć tę funkcję jawnie podczas wdrażania usługi w chmurze, więc, że wymagane usługi (na przykład msvsmon.exe) są zainstalowane na maszynach wirtualnych działających wystąpień roli. Jeśli nie zostały włączone, zdalne debugowanie po opublikowaniu usługi, musisz ponownie opublikować usługę z włączonym debugowaniem zdalnym.

Po włączeniu funkcji debugowania zdalnego dla usługi w chmurze, go nie wykazują pogorszenie wydajności lub naliczone dodatkowe opłaty za. Nie należy używać zdalnego debugowania na usługę produkcyjną, ponieważ klienci, którzy korzystają z usługi może to mieć niekorzystny wpływ.

> [!NOTE]
> Podczas publikowania usługi w chmurze w programie Visual Studio, aby umożliwić **IntelliTrace** wszystkich ról w tej usłudze, których platformą docelową jest program .NET Framework 4 lub .NET Framework 4.5. Za pomocą **IntelliTrace**, można zbadać zdarzenia, które wystąpiły w wystąpieniu roli w przeszłości i odtworzenia kontekstu po tym czasie. Zobacz [debugowanie opublikowanych usług w chmurze za pomocą IntelliTrace i Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md) i [przy użyciu funkcji IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Aby włączyć zdalne debugowanie dla usługi w chmurze

1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.

2. Wybierz **przemieszczania** środowiska i **debugowania** konfiguracji.

    To jest tylko wskazówką. Możesz zdecydować się na uruchomienie środowiska testowego w środowisku produkcyjnym. Jednak użytkownik może niekorzystnie wpłynąć na użytkowników po włączeniu zdalnego debugowania w środowisku produkcyjnym. Można wybrać konfigurację wydania, ale z konfiguracji debugowania sprawia, że ułatwia debugowanie.

    ![Wybierz konfigurację debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Postępuj zgodnie z instrukcjami zwykle, ale wybierz **Włączanie zdalnego debugera dla wszystkich ról** pole wyboru na **Zaawansowane ustawienia** kartę.

    ![Konfiguracja debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Aby dołączyć debuger do usługi w chmurze na platformie Azure

1. W Eksploratorze serwera rozwiń węzeł usługi w chmurze.

2. Otwórz menu skrótów dla roli lub wystąpienia roli, do której chcesz dołączyć, a następnie wybierz **dołączyć debuger**.

    Jeśli debugujesz rolę, debuger programu Visual Studio dołącza do każde wystąpienie tej roli. Debuger przerywał działanie punkt przerwania w pierwszym wystąpieniu roli, uruchamia ten wiersz kodu, który spełnia wszelkie warunki ten punkt przerwania. Jeśli debugujesz wystąpienie dołącza debuger do tego wystąpienia i podziału punkt przerwania tylko wtedy, gdy tego konkretnego wystąpienia uruchamia ten wiersz kodu i spełnia warunki punktu przerwania.

    ![Dołącz debuger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po dołącza debuger do wystąpienia, debugowanie w zwykły sposób. Debuger automatycznie dołącza do procesu odpowiedniego hosta dla roli użytkownika. W zależności od roli debuger dołącza do w3wp.exe, WaWorkerHost.exe lub WaIISHost.exe. Aby sprawdzić, czy Proces, do której jest dołączony debuger, rozwiń węzeł wystąpienia w Eksploratorze serwera. Zobacz [architektura ról platformy](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) Aby uzyskać więcej informacji na temat przetwarzanych przez platformę Azure.

    ![Wybieranie typu kodu — okno dialogowe](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Aby zidentyfikować procesy, do których jest dołączony debuger, należy otworzyć okno dialogowe procesów, na pasku menu, wybierając debugowania, Windows, procesy. (Klawiatura: Ctrl + Alt + Z) Aby odłączyć określonego procesu, otwórz jego menu skrótów, a następnie wybierz **odłączanie procesu**. Lub, zlokalizuj węzeł wystąpienia w Eksploratorze serwera, Znajdź proces, otwórz jego menu skrótów, a następnie wybierz **odłączanie procesu**.

    ![Debugowanie procesów](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Unikaj długich zatrzymuje w punktach przerwania podczas zdalnego debugowania. Azure traktuje procesu, który jest zablokowany przez czas dłuższy niż kilka minut. nie odpowiada i przestaje wysyłać ruch do tego wystąpienia. Jeśli użytkownik zaprzestanie zbyt długo msvsmon.exe odłączy się od procesu.

Aby odłączyć debuger od wszystkich procesów w ramach wystąpienia lub roli, otwórz menu skrótów dla roli lub wystąpienia, debugowania, a następnie wybierz pozycję **odłączyć debuger**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Ograniczenia dotyczące zdalnego debugowania na platformie Azure

W systemie Azure SDK 2.3 debugowania zdalnego ma następujące ograniczenia:

* Dzięki zdalnemu debugowaniu, włączone, nie można opublikować w którym znajduje się więcej niż 25 wystąpień każdej roli usługi w chmurze.
* Debuger korzysta z portów 30400 do 30424, 31400 do 31424 i 32400 do 32424. Jeśli spróbujesz użyć dowolnego z tych portów, nie będzie można opublikować usługę, a jeden z następujących komunikatów o błędzie pojawi się w dzienniku aktywności platformy Azure:

  * Wystąpił błąd podczas sprawdzania pliku .cscfg względem pliku csdef.
    Zakres portów zarezerwowanych "range" dla punktu końcowego Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector roli "rola" nakłada się na już zdefiniowany port lub zakres.
  * Alokacja nie powiodła się. Spróbuj ponownie później, Ogranicz rozmiar maszyny Wirtualnej lub liczbę wystąpień roli lub spróbuj wdrożyć w innym regionie.

## <a name="debugging-azure-virtual-machines"></a>Profilowanie maszyn wirtualnych platformy Azure

Umożliwia debugowanie programów uruchamianych na maszynach wirtualnych platformy Azure za pomocą Eksploratora serwera w programie Visual Studio. Po włączeniu zdalnego debugowania na maszynie wirtualnej platformy Azure, Azure instaluje rozszerzenie debugowania zdalnego na maszynie wirtualnej. Następnie można dołączyć do procesów na maszynie wirtualnej, a debugowanie w zwykły sposób.

> [!NOTE]
> Maszyny wirtualne utworzone za pomocą stosu usługi Azure resource manager można zdalnie debugować za pomocą programu Cloud Explorer programu Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [zarządzania zasobami platformy Azure za pomocą Eksploratora chmury](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Aby debugować maszynie wirtualnej platformy Azure

1. W Eksploratorze serwera rozwiń węzeł maszyn wirtualnych, a następnie wybierz węzeł maszyny wirtualnej, który chcesz debugować.

2. Otwórz menu kontekstowe i wybierz **włączyć debugowanie**. Po wyświetleniu monitu, jeśli wiesz, jeśli chcesz umożliwić debugowanie na maszynie wirtualnej, wybierz opcję **tak**.

    Azure instaluje rozszerzenie debugowania zdalnego na maszynie wirtualnej, aby włączyć debugowanie.

    ![Maszyny wirtualnej Włącz polecenie debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po ukończeniu instalowania zdalnego debugowania rozszerzenia, otwórz menu kontekstowe maszyny wirtualnej i wybierz **dołączanie debugera...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i pokazuje, w oknie Dołącz do procesu, okno dialogowe.

    ![Dołącz polecenia debugera](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. W **dołączyć do procesu** okno dialogowe, wybierz opcję **wybierz** ograniczyć listę wyników, aby wyświetlić tylko typy kodu, który chcesz debugować. Można debugować 32-bitową lub 64-bitowego kodu zarządzanego i natywnego kodu.

    ![Wybieranie typu kodu — okno dialogowe](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wybierz procesy, aby debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład wybierz proces w3wp.exe, jeśli chcesz debugować aplikację sieci web na maszynie wirtualnej. Zobacz [debugować jeden lub więcej procesów w programie Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) i [architektura ról platformy](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) Aby uzyskać więcej informacji.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Tworzenie projektu sieci web i maszyny wirtualnej do debugowania

Przed opublikowaniem projekt platformy Azure, może okazać przydatne w celu przetestowania jej w środowisku zawarte, która obsługuje debugowania i testowania scenariuszy i gdzie można zainstalować testowaniu i monitorowaniu programów. Jednym ze sposobów uruchamiania tych testów jest zdalne debugowanie aplikacji na maszynie wirtualnej.

Projekty języka Visual Studio ASP.NET oferuje opcję, aby utworzyć maszynę wirtualną pod ręką, używanej do testowania aplikacji. Maszyna wirtualna zawiera potrzebnych punktów końcowych, takich jak program PowerShell, pulpitu zdalnego i WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Aby utworzyć projekt sieci web i maszyny wirtualnej do debugowania

1. W programie Visual Studio Utwórz nową aplikację sieci Web platformy ASP.NET.

2. W oknie dialogowym Nowy projekt ASP.NET, w sekcji platformy Azure wybierz **maszyny wirtualnej** w polu listy rozwijanej. Pozostaw **Utwórz zasoby zdalne** zaznaczone pole wyboru. Wybierz **OK** aby kontynuować.

    **Utwórz maszynę wirtualną na platformie Azure** pojawi się okno dialogowe.

    ![Utwórz okno dialogowe projektu sieci web platformy ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Użytkownik zostanie poproszony o zalogowanie się do konta platformy Azure, jeśli jeszcze nie jest zalogowany.

3. Wybierz różne ustawienia dla maszyny wirtualnej, a następnie wybierz pozycję **OK**. Zobacz [maszyn wirtualnych](/previous-versions/azure/jj156003(v=azure.100)) Aby uzyskać więcej informacji.

    Nazwa wprowadzona dla nazwy DNS będzie nazwa maszyny wirtualnej.

    ![Tworzenie maszyny wirtualnej na okno dialogowe platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Platforma Azure tworzy maszynę wirtualną, a następnie aprowizuje i konfiguruje punktów końcowych, takich jak pulpitu zdalnego i narzędzia Web Deploy

4. Po maszyny wirtualnej jest w pełni skonfigurowane, wybierz węzeł maszyny wirtualnej, w Eksploratorze serwera.

5. Otwórz menu kontekstowe i wybierz **włączyć debugowanie**. Po wyświetleniu monitu, jeśli wiesz, jeśli chcesz umożliwić debugowanie na maszynie wirtualnej, wybierz opcję **tak**.

    Azure instaluje rozszerzenie debugowania zdalnego z maszyną wirtualną, aby włączyć debugowanie.

    ![Maszyny wirtualnej Włącz polecenie debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publikowanie projektu, co zostało opisane w [jak: wdrożyć publikowania projektu sieci Web za pomocą jednego kliknięcia w programie Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Aby można było debugować na maszynie wirtualnej na **ustawienia** strony **publikowanie w sieci Web** kreatora wybierz pozycję **debugowania** jako konfiguracji. Dzięki temu kod symbole są dostępne podczas debugowania.

    ![Ustawienia publikowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. W **opcji publikowania pliku**, wybierz opcję **Usuń dodatkowe pliki w lokalizacji docelowej** Jeżeli projekt został już wdrożony wcześniej.

8. Po publikuje projektu, w menu kontekstowym maszyny wirtualnej w Eksploratorze serwera wybierz **dołączanie debugera...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i pokazuje, w oknie Dołącz do procesu, okno dialogowe.

    ![Dołącz polecenia debugera](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. W **dołączyć do procesu** okno dialogowe, wybierz opcję **wybierz** ograniczyć listę wyników, aby wyświetlić tylko typy kodu, który chcesz debugować. Można debugować 32-bitową lub 64-bitowego kodu zarządzanego i natywnego kodu.

    ![Wybieranie typu kodu — okno dialogowe](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wybierz procesy, aby debugować na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład wybierz proces w3wp.exe, jeśli chcesz debugować aplikację sieci web na maszynie wirtualnej. Zobacz [debugować jeden lub więcej procesów w programie Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) Aby uzyskać więcej informacji.

## <a name="next-steps"></a>Następne kroki

* Użyj **IntelliTrace** , aby zebrać dziennik wywołań i zdarzeń z serwera wersji. Zobacz [debugowanie opublikowanych usług w chmurze za pomocą IntelliTrace i programu Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

* Użyj **diagnostyki Azure** się szczegółowe informacje na uruchamianie kodu w ramach ról, czy role są uruchomione w środowisku deweloperskim lub na platformie Azure. Zobacz [zbieranie danych rejestrowania przy użyciu usługi Azure Diagnostics](https://msdn.microsoft.com/library/gg433048.aspx).
