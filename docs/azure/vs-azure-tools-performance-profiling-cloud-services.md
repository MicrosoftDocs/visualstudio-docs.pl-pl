---
title: Testowanie wydajności usługi w chmurze | Microsoft Docs
description: Testowanie wydajności usługi w chmurze przy użyciu profilera programu Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: 5c92a2bb2349f1b5543672d7ecd944e3d82bb500
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508434"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Testowanie wydajności usługi w chmurze
## <a name="overview"></a>Omówienie
Wydajność usługi w chmurze można przetestować w następujący sposób:

* Użyj Diagnostyka Azure, aby zebrać informacje o żądaniach i połączeniach oraz przejrzeć statystyki lokacji, które pokazują, jak usługa wykonuje z perspektywy klienta. Aby rozpocząć pracę z usługą, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).
* Użyj profilera programu Visual Studio, aby uzyskać szczegółową analizę aspektów obliczeniowych sposobu działania usługi. Jak opisano w tym temacie, można użyć profilera do mierzenia wydajności jako usługi na platformie Azure. Aby dowiedzieć się, jak używać profilera do mierzenia wydajności jako usługi uruchomionej lokalnie w emulatorze obliczeniowym, zobacz [testowanie wydajności usługi w chmurze platformy Azure lokalnie w emulatorze obliczeniowym przy użyciu profilera programu Visual Studio](/azure/cloud-services/cloud-services-performance-testing-visual-studio-profiler).

## <a name="choosing-a-performance-testing-method"></a>Wybieranie metody testowania wydajności
### <a name="use-azure-diagnostics-to-collect"></a>Użyj Diagnostyka Azure do zebrania:
* Statystyki dotyczące stron lub usług sieci Web, takich jak żądania i połączenia.
* Statystyki dotyczące ról, takie jak częstotliwość ponownego uruchamiania roli.
* Ogólne informacje o wykorzystaniu pamięci, takie jak procent czasu trwania modułu wyrzucania elementów bezużytecznych lub zestaw pamięci uruchomionej roli.

### <a name="use-the-visual-studio-profiler-to"></a>Użyj profilera programu Visual Studio, aby:
* Ustal, które funkcje są najbardziej czasochłonne.
* Zmierz, ile czasu zajmie każda część programu intensywnie korzystających z obliczeń.
* Porównaj szczegółowe raporty dotyczące wydajności dla dwóch wersji usługi.
* Przeanalizuj alokację pamięci bardziej szczegółowo niż poziom poszczególnych alokacji pamięci.
* Analizuj problemy współbieżności w kodzie wielowątkowym.

Korzystając z profilera, można zbierać dane, gdy usługa w chmurze działa lokalnie lub na platformie Azure.

### <a name="collect-profiling-data-locally-to"></a>Zbierz lokalnie dane profilowania do:
* Przetestuj wydajność części usługi w chmurze, taką jak wykonywanie konkretnej roli procesu roboczego, która nie wymaga realistycznych obciążeń symulowanych.
* Przetestuj wydajność usługi w chmurze w izolacji w kontrolowanych warunkach.
* Przetestuj wydajność usługi w chmurze przed wdrożeniem jej na platformie Azure.
* Przetestuj wydajność usługi w chmurze prywatnie, bez zakłócania istniejących wdrożeń.
* Przetestuj wydajność usługi bez naliczania opłat za uruchamianie na platformie Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Zbierz dane profilowania na platformie Azure, aby:
* Przetestuj wydajność usługi w chmurze w symulowanym lub rzeczywistym obciążeniu.
* Użyj metody instrumentacji zbierania danych profilowania, jak opisano to w dalszej części tego tematu.
* Przetestuj wydajność usługi w tym samym środowisku, co w przypadku, gdy usługa jest uruchamiana w produkcji.

Zazwyczaj symulowane jest obciążenie w celu przetestowania usług w chmurze w warunkach normalnych lub obciążeniowych.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilowanie usługi w chmurze na platformie Azure
Po opublikowaniu usługi w chmurze w programie Visual Studio można profilować usługę i określić ustawienia profilowania, które udostępniają odpowiednie informacje. Sesja profilowania jest uruchamiana dla każdego wystąpienia roli. Aby uzyskać więcej informacji o sposobach publikowania usługi w programie Visual Studio, zobacz [Publikowanie w usłudze Azure Cloud Service w programie Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

Aby dowiedzieć się więcej na temat profilowania wydajności w programie Visual Studio, zobacz [początkując Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md) i [analizowania wydajności aplikacji przy użyciu narzędzia profilowania](../profiling/performance-explorer.md).

> [!NOTE]
> Podczas publikowania usługi w chmurze można włączyć opcję IntelliTrace lub profilowania. Nie można włączyć obu tych wartości.
>
>

### <a name="profiler-collection-methods"></a>Metody zbierania profilera
Możesz użyć różnych metod zbierania na potrzeby profilowania na podstawie problemów z wydajnością:

* **Próbkowanie procesora** — ta metoda zbiera dane statystyczne aplikacji, które są przydatne do początkowej analizy problemów z użyciem procesora CPU. Próbkowanie procesora jest sugerowaną metodą uruchamiania większości badań wydajności. Istnieje niewielki wpływ na aplikację, która jest profilowania podczas zbierania danych próbkowania procesora.
* **Instrumentacja** — ta metoda umożliwia zbieranie szczegółowych danych o chronometrażu, które są przydatne w przypadku analizy ukierunkowanej i analizowania problemów z wydajnością danych wejściowych/wyjściowych. Metoda Instrumentacji rejestruje każde wejście, wyjście i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Ta metoda jest przydatna do zbierania szczegółowych informacji o chronometrażu w sekcji kodu oraz do poznania wpływu operacji wejścia i wyjścia na wydajność aplikacji. Ta metoda jest wyłączona dla komputera z 32-bitowym systemem operacyjnym. Ta opcja jest dostępna tylko wtedy, gdy uruchamiasz usługę w chmurze na platformie Azure, a nie lokalnie w emulatorze obliczeniowym.
* **Alokacja pamięci platformy .NET** — ta metoda zbiera dane alokacji pamięci .NET Framework przy użyciu metody profilowania próbkowania. Zebrane dane obejmują liczbę i rozmiar przyznanych obiektów.
* **Współbieżność** — ta metoda zbiera dane rywalizacji o zasoby oraz dane dotyczące procesu i wykonywania wątku, które są przydatne podczas analizowania aplikacji wielowątkowych i wieloprocesowych. Metoda współbieżności zbiera dane dla każdego zdarzenia, które blokuje wykonywanie kodu, na przykład gdy wątek oczekuje na zwolnienie zablokowanego dostępu do zasobu aplikacji. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.
* Można również włączyć **profilowanie interakcji między warstwami**, co zapewnia dodatkowe informacje o czasach wykonywania synchronicznych wywołań ADO.NET w funkcjach wielowarstwowych aplikacji, które komunikują się z co najmniej jedną bazą danych. Dane interakcji warstwy można zbierać przy użyciu dowolnej metody profilowania. Aby uzyskać więcej informacji na temat profilowania interakcji między warstwami, zobacz [Widok interakcji między warstwami](../profiling/tier-interactions-view.md).

## <a name="configuring-profiling-settings"></a>Konfigurowanie ustawień profilowania
Na poniższej ilustracji przedstawiono sposób konfigurowania ustawień profilowania przy użyciu okna dialogowego publikowanie aplikacji platformy Azure.

![Konfigurowanie ustawień profilowania](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Aby włączyć pole wyboru **Włącz profilowanie** , musisz mieć zainstalowany Profiler na komputerze lokalnym używanym do publikowania usługi w chmurze. Domyślnie Profiler jest instalowany podczas instalowania programu Visual Studio.
>
>

### <a name="to-configure-profiling-settings"></a>Aby skonfigurować ustawienia profilowania
1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz polecenie **Publikuj**. Aby uzyskać szczegółowe instrukcje dotyczące publikowania usługi w chmurze, zobacz [publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure](vs-azure-tools-publishing-a-cloud-service.md).
2. W oknie dialogowym **publikowanie aplikacji platformy Azure** wybierz kartę **Ustawienia zaawansowane** .
3. Aby włączyć profilowanie, zaznacz pole wyboru **Włącz profilowanie** .
4. Aby skonfigurować ustawienia profilowania, wybierz hiperłącze **Ustawienia** . Zostanie wyświetlone okno dialogowe Ustawienia profilowania.
5. Z **jakiej metody profilowania chcesz korzystać** z przycisków opcji, wybierz wymagany typ profilowania.
6. Aby zebrać dane profilowania interakcji między warstwami, zaznacz pole wyboru **Włącz profilowanie interakcji między warstwami** .
7. Aby zapisać ustawienia, wybierz przycisk **OK** .

    Podczas publikowania tej aplikacji te ustawienia są używane do tworzenia sesji profilowania dla każdej roli.

## <a name="viewing-profiling-reports"></a>Wyświetlanie raportów profilowania
Dla każdego wystąpienia roli w usłudze w chmurze zostanie utworzona sesja profilowania. Aby wyświetlić raporty profilowania dla każdej sesji z programu Visual Studio, można wyświetlić okno Eksplorator serwera a następnie wybrać węzeł obliczenia platformy Azure w celu wybrania wystąpienia roli. Następnie można wyświetlić raport profilowania, jak pokazano na poniższej ilustracji.

![Wyświetlanie raportu profilowania z platformy Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Aby wyświetlić raporty profilowania
1. Aby wyświetlić okno Eksplorator serwera w programie Visual Studio, na pasku menu wybierz widok, Eksplorator serwera.
2. Wybierz węzeł obliczenia platformy Azure, a następnie wybierz węzeł wdrożenia platformy Azure dla usługi w chmurze, która została wybrana do profilowania przy publikowaniu z programu Visual Studio.
3. Aby wyświetlić raporty profilowania dla wystąpienia, wybierz rolę w usłudze, otwórz menu skrótów dla określonego wystąpienia, a następnie wybierz polecenie **Wyświetl raport profilowania**.

    Raport, plik. vsp, jest teraz pobierany z platformy Azure, a w dzienniku aktywności platformy Azure zostanie wyświetlony stan pobierania. Po zakończeniu pobierania raport profilowania zostanie wyświetlony na karcie w edytorze dla programu Visual Studio o nazwie <nazwa roli \> *<numerem \> wystąpienia*<identyfikator \> . vsp. Dane podsumowujące raportu są wyświetlane.
4. Aby wyświetlić różne widoki raportu, na liście bieżący widok wybierz odpowiedni typ widoku. Aby uzyskać więcej informacji, zobacz [narzędzia profilowania widoków raportów](../profiling/performance-report-views.md).

## <a name="next-steps"></a>Następne kroki
[Debugowanie Cloud Services](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Publikowanie w usłudze w chmurze platformy Azure z poziomu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)
