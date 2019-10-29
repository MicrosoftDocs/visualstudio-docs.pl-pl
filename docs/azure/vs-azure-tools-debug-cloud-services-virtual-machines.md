---
title: Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure
description: Debugowanie usługi w chmurze lub maszyny wirtualnej w programie Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: a353ac12f7477bf40393f83de5fe41ede4d9aa95
ms.sourcegitcommit: bb5425b9c6d8fd7135d9584c2963831754071347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73024582"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio

Program Visual Studio oferuje różne opcje debugowania usług Azure Cloud Services i Virtual Machines.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debugowanie usługi w chmurze na komputerze lokalnym

Możesz zaoszczędzić czas i pieniądze, korzystając z emulatora obliczeń platformy Azure w celu debugowania usługi w chmurze na komputerze lokalnym. Przez debugowanie usługi lokalnie przed jej wdrożeniem można zwiększyć niezawodność i wydajność bez płacenia za czas obliczeń. Niektóre błędy mogą jednak wystąpić tylko w przypadku uruchomienia usługi w chmurze na platformie Azure. Można debugować te błędy w przypadku włączenia debugowania zdalnego podczas publikowania usługi, a następnie dołączenia debugera do wystąpienia roli.

Emulator symuluje usługę obliczeniową platformy Azure i działa w środowisku lokalnym, dzięki czemu można testować i debugować usługę w chmurze przed jej wdrożeniem. Emulator obsługuje cykl życia wystąpień roli i zapewnia dostęp do symulowanych zasobów, takich jak magazyn lokalny. Podczas debugowania lub uruchamiania usługi z programu Visual Studio automatycznie uruchamia emulator jako aplikację w tle, a następnie wdraża usługę na emulatorze. Możesz użyć emulatora, aby wyświetlić swoją usługę, gdy działa w środowisku lokalnym. Możesz uruchomić pełną wersję lub wersję Express emulatora. (Począwszy od platformy Azure 2,3, wersja Express emulatora jest domyślna). Zobacz [Używanie emulatora Express do lokalnego uruchamiania i debugowania usługi w chmurze](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Aby debugować usługę w chmurze na komputerze lokalnym

1. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** , aby uruchomić projekt usługi w chmurze platformy Azure. Alternatywnie możesz nacisnąć klawisz F5. Zobaczysz komunikat informujący o tym, że emulator obliczeń jest uruchamiany. Po uruchomieniu emulatora ikona na pasku zadań zostanie poprawna.

    ![Emulator platformy Azure na pasku zadań](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Wyświetl interfejs użytkownika dla emulatora obliczeń, otwierając menu skrótów dla ikony platformy Azure w obszarze powiadomień, a następnie wybierając pozycję **Pokaż interfejs użytkownika emulatora obliczeń**.

    W lewym okienku interfejsu użytkownika są wyświetlane usługi, które są obecnie wdrożone w emulatorze obliczeniowym i wystąpieniach ról, które są uruchomione w poszczególnych usługach. Możesz wybrać usługę lub role do wyświetlania informacji o cyklu życia, rejestrowania i diagnostyki w okienku po prawej stronie. Jeśli fokus zostanie umieszczony na górnym marginesie dołączonego okna, rozszerza się w celu wypełnienia okienka po prawej stronie.

3. Przejdź do aplikacji, wybierając polecenia z menu **Debuguj** i ustawiając punkty przerwania w kodzie. Po przekroczeniu przez aplikację w debugerze okienka są aktualizowane z bieżącym stanem aplikacji. Po zatrzymaniu debugowania wdrożenie aplikacji zostanie usunięte. Jeśli aplikacja zawiera rolę sieci Web i ustawisz właściwość Akcja uruchamiania na uruchamianie przeglądarki sieci Web, program Visual Studio uruchamia aplikację sieci Web w przeglądarce. W przypadku zmiany liczby wystąpień roli w konfiguracji usługi należy zatrzymać usługę w chmurze, a następnie ponownie uruchomić debugowanie, aby można było debugować te nowe wystąpienia roli.

    > [!NOTE]
    > Po zatrzymaniu lub debugowaniu usługi lokalny emulator obliczeniowy i emulator magazynu nie zostaną zatrzymane. Należy je zatrzymywać jawnie w obszarze powiadomień.

## <a name="debug-a-cloud-service-in-azure"></a>Debugowanie usługi w chmurze na platformie Azure

Aby debugować usługę chmurową z komputera zdalnego, należy włączyć tę funkcję jawnie podczas wdrażania usługi w chmurze, tak aby wymagane usługi (na przykład msvsmon. exe) zostały zainstalowane na maszynach wirtualnych, na których działają wystąpienia roli. Jeśli podczas publikowania usługi nie włączono debugowania zdalnego, należy ponownie opublikować usługę z włączonym debugowaniem zdalnym.

Włączenie debugowania zdalnego dla usługi w chmurze nie powoduje obniżenia wydajności ani ponoszenia dodatkowych opłat. Nie używaj debugowania zdalnego w usłudze produkcyjnej, ponieważ może to mieć negatywny wpływ na klientów korzystających z usługi.

> [!NOTE]
> Po opublikowaniu usługi w chmurze w programie Visual Studio można włączyć **IntelliTrace** dla wszystkich ról w tej usłudze, które są przeznaczone dla .NET Framework 4 lub .NET Framework 4,5. Za pomocą **IntelliTrace**można testować zdarzenia, które wystąpiły w wystąpieniu roli w przeszłości, i odtworzyć kontekst od tego czasu. Zobacz [debugowanie opublikowanej usługi w chmurze za pomocą IntelliTrace i programu Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) oraz [Korzystanie z IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Aby włączyć debugowanie zdalne dla usługi w chmurze

1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.

2. Wybierz środowisko **przejściowe** i konfigurację **debugowania** .

    Jest to tylko wytyczne. Możesz wybrać opcję uruchamiania środowisk testowych w środowisku produkcyjnym. Jednak użytkownik może niekorzystnie wpłynąć na użytkowników w przypadku włączenia debugowania zdalnego w środowisku produkcyjnym. Można wybrać konfigurację wydania, ale Konfiguracja debugowania ułatwia debugowanie.

    ![Wybierz konfigurację debugowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Postępuj zgodnie z typowymi krokami, ale zaznacz pole wyboru **Włącz debuger zdalny dla wszystkich ról** na karcie **Ustawienia zaawansowane** .

    ![Debuguj konfigurację](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Aby dołączyć debuger do usługi w chmurze na platformie Azure

1. W Eksplorator serwera rozwiń węzeł usługi w chmurze.

2. Otwórz menu skrótów dla roli lub wystąpienia roli, do którego chcesz dołączyć, a następnie wybierz pozycję **Dołącz debuger**.

    W przypadku debugowania roli debuger programu Visual Studio dołącza do każdego wystąpienia tej roli. Debuger przerwie się w punkcie przerwania dla pierwszego wystąpienia roli, które uruchamia ten wiersz kodu i spełnia wszystkie warunki tego punktu przerwania. Jeśli debugujesz wystąpienie, debuger dołącza tylko do tego wystąpienia i przerwie w punkcie przerwania tylko wtedy, gdy to konkretne wystąpienie uruchamia ten wiersz kodu i spełnia warunki punktu przerwania.

    ![Dołącz debuger](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po dołączeniu debugera do wystąpienia Debuguj je w zwykły sposób. Debuger automatycznie dołącza do odpowiedniego procesu hosta dla Twojej roli. W zależności od roli programu debuger dołącza do w3wp. exe, WaWorkerHost. exe lub WaIISHost. exe. Aby sprawdzić proces, do którego jest podłączony debuger, rozwiń węzeł wystąpienia w Eksplorator serwera. Aby uzyskać więcej informacji na temat procesów platformy Azure, zobacz [Architektura roli platformy Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) .

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Aby zidentyfikować procesy, do których jest dołączony debuger, Otwórz okno dialogowe procesy, klikając na pasku menu pozycję Debugowanie, okna i procesy. (Klawiatura: Ctrl + Alt + Z) Aby odłączyć określony proces, otwórz jego menu skrótów, a następnie wybierz polecenie **Odłącz proces**. Lub zlokalizuj węzeł wystąpienia w Eksplorator serwera, Znajdź proces, otwórz jego menu skrótów, a następnie wybierz polecenie **Odłącz proces**.

    ![Debugowanie procesów](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Unikaj długotrwałych zatrzymań w punktach przerwania podczas debugowania zdalnego. Platforma Azure traktuje proces, który jest zatrzymany przez czas dłuższy niż kilka minut i zatrzymuje wysyłanie ruchu do tego wystąpienia. Jeśli zatrzymano za długo, program msvsmon. exe odłącza się od procesu.

Aby odłączyć debuger od wszystkich procesów w wystąpieniu lub roli, otwórz menu skrótów dla używanej roli lub wystąpienia, a następnie wybierz polecenie **Odłącz debuger**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Ograniczenia zdalnego debugowania na platformie Azure

W zestawie Azure SDK 2,3 zdalne debugowanie ma następujące ograniczenia:

* Po włączeniu debugowania zdalnego nie można opublikować usługi w chmurze, w której każda rola ma więcej niż 25 wystąpień.
* Debuger używa portów 30400 do 30424, 31400 do 31424 i 32400 do 32424. Jeśli spróbujesz użyć dowolnego z tych portów, nie będzie można opublikować swojej usługi, a w dzienniku aktywności platformy Azure zostanie wyświetlony jeden z następujących komunikatów o błędach:

  * Wystąpił błąd podczas sprawdzania poprawności pliku cscfg względem pliku. csdef.
    Zarezerwowany zakres portów "Range" dla punktu końcowego Microsoft. WindowsAzure. plugins. RemoteDebugger. Connector roli "role" nakłada się na już zdefiniowany port lub zakres.
  * Alokacja nie powiodła się. Spróbuj ponownie później, spróbuj zmniejszyć rozmiar maszyny wirtualnej lub liczbę wystąpień roli lub spróbuj wykonać wdrożenie w innym regionie.

## <a name="debugging-azure-virtual-machines"></a>Debugowanie maszyn wirtualnych platformy Azure

Programy uruchamiane na maszynach wirtualnych platformy Azure można debugować za pomocą Eksplorator serwera w programie Visual Studio. Po włączeniu debugowania zdalnego na maszynie wirtualnej platformy Azure Program Azure instaluje rozszerzenie zdalnego debugowania na maszynie wirtualnej. Następnie można dołączyć do procesów na maszynie wirtualnej i debugować się jak zwykle.

> [!NOTE]
> Maszyny wirtualne utworzone za pośrednictwem stosu usługi Azure Resource Manager można zdalnie debugować za pomocą programu Cloud Explorer w programie Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami platformy Azure za pomocą programu Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Aby debugować maszynę wirtualną platformy Azure

1. W Eksplorator serwera rozwiń węzeł Virtual Machines i wybierz węzeł maszyny wirtualnej, którą chcesz debugować.

2. Otwórz menu kontekstowe i wybierz polecenie **Włącz debugowanie**. Po wyświetleniu monitu, jeśli na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz pozycję **tak**.

    Na platformie Azure zostanie zainstalowane rozszerzenie debugowania zdalnego na maszynie wirtualnej w celu włączenia debugowania.

    ![Polecenie włączenia debugowania dla maszyny wirtualnej](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po zakończeniu instalacji rozszerzenia debugowania zdalnego Otwórz menu kontekstowe maszyny wirtualnej i wybierz pozycję **Dołącz debuger...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i wyświetla je w oknie dialogowym Dołącz do procesu.

    ![Dołącz debuger — polecenie](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. W oknie dialogowym **Dołącz do procesu** wybierz pozycję **Wybierz** , aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, które chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod natywny lub oba te elementy.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wybierz procesy, które mają być debugowane na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład można wybrać proces W3wp. exe, jeśli chcesz debugować aplikację sieci Web na maszynie wirtualnej. Aby uzyskać więcej informacji, zobacz [debugowanie co najmniej jednego procesu w programie Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) i [architekturze roli platformy Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) .

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Tworzenie projektu sieci Web i maszyny wirtualnej na potrzeby debugowania

Przed opublikowaniem projektu platformy Azure przydatne może być przetestowanie go w środowisku zawartego, które obsługuje scenariusze debugowania i testowania oraz miejsce, w którym można zainstalować testy i programy monitorowania. Jednym ze sposobów uruchamiania takich testów jest zdalne debugowanie aplikacji na maszynie wirtualnej.

Projekty programu Visual Studio ASP.NET oferują opcję tworzenia przydatnej maszyny wirtualnej, której można użyć do testowania aplikacji. Maszyna wirtualna obejmuje często odpowiednie punkty końcowe, takie jak PowerShell, Pulpit zdalny i webdeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Aby utworzyć projekt sieci Web i maszynę wirtualną na potrzeby debugowania

1. W programie Visual Studio Utwórz nową aplikację sieci Web ASP.NET.

2. W oknie dialogowym Nowy projekt ASP.NET w sekcji Azure wybierz pozycję **maszyna wirtualna** w polu listy rozwijanej. Pozostaw zaznaczone pole wyboru **Utwórz zasoby zdalne** . Wybierz **przycisk OK** , aby wykonać operację.

    Zostanie wyświetlone okno dialogowe **Tworzenie maszyny wirtualnej w systemie Azure** .

    ![Okno dialogowe Tworzenie projektu sieci Web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Użytkownik zostanie poproszony o zalogowanie się do konta platformy Azure, jeśli jeszcze nie jest zalogowany.

3. Wybierz różne ustawienia dla maszyny wirtualnej, a następnie wybierz przycisk **OK**. Aby uzyskać więcej informacji, zobacz [Virtual Machines](/azure/virtual-machines/) .

    Nazwa wprowadzona dla nazwy DNS będzie nazwą maszyny wirtualnej.

    ![Tworzenie maszyny wirtualnej w systemie Azure — okno dialogowe](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Platforma Azure tworzy maszynę wirtualną, a następnie inicjuje i konfiguruje punkty końcowe, takie jak Pulpit zdalny i Web Deploy

4. Po całkowitym skonfigurowaniu maszyny wirtualnej wybierz węzeł maszyny wirtualnej w Eksplorator serwera.

5. Otwórz menu kontekstowe i wybierz polecenie **Włącz debugowanie**. Po wyświetleniu monitu, jeśli na pewno chcesz włączyć debugowanie na maszynie wirtualnej, wybierz pozycję **tak**.

    Platforma Azure instaluje rozszerzenie zdalnego debugowania na maszynie wirtualnej w celu włączenia debugowania.

    ![Polecenie włączenia debugowania dla maszyny wirtualnej](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Dziennik aktywności platformy Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Opublikuj projekt zgodnie z opisem w temacie [jak: wdrażanie projektu sieci Web za pomocą jednego kliknięcia przycisku Publikuj w programie Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Ponieważ chcesz debugować maszynę wirtualną, na stronie **Ustawienia** kreatora **publikacji w sieci Web** wybierz opcję **Debuguj** jako konfigurację. Daje to pewność, że symbole kodu są dostępne podczas debugowania.

    ![Ustawienia publikowania](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. W **opcjach publikowania plików**wybierz opcję **Usuń dodatkowe pliki w miejscu docelowym** , jeśli projekt został już wdrożony wcześniej.

8. Po opublikowaniu projektu w menu kontekstowym maszyny wirtualnej w Eksplorator serwera wybierz pozycję **Dołącz debuger...**

    Platforma Azure pobiera listę procesów na maszynie wirtualnej i wyświetla je w oknie dialogowym Dołącz do procesu.

    ![Dołącz debuger — polecenie](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. W oknie dialogowym **Dołącz do procesu** wybierz pozycję **Wybierz** , aby ograniczyć listę wyników, aby wyświetlić tylko typy kodu, które chcesz debugować. Można debugować 32-bitowy lub 64-bitowy kod zarządzany, kod natywny lub oba te elementy.

    ![Okno dialogowe Wybieranie typu kodu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wybierz procesy, które mają być debugowane na maszynie wirtualnej, a następnie wybierz pozycję **Dołącz**. Na przykład można wybrać proces W3wp. exe, jeśli chcesz debugować aplikację sieci Web na maszynie wirtualnej. Aby uzyskać więcej informacji [, zobacz Debugowanie co najmniej jednego procesu w programie Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) .

## <a name="next-steps"></a>Następne kroki

* Użyj **IntelliTrace** , aby zebrać dziennik wywołań i zdarzeń z serwera wersji. Zobacz [debugowanie opublikowanej usługi w chmurze za pomocą IntelliTrace i programu Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Użyj **Diagnostyka Azure** , aby rejestrować szczegółowe informacje z kodu działającego w ramach ról, niezależnie od tego, czy role są uruchomione w środowisku programistycznym, czy na platformie Azure. Zobacz [zbieranie danych rejestrowania przy użyciu Diagnostyka Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).
