---
title: Testowanie wydajności usługi w chmurze | Dokumentacja firmy Microsoft
description: Testowanie wydajności usługi w chmurze przy użyciu programu Visual Studio profiler
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: fd436a6b7e38c8f76de5d113c326e194e4011155
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62427412"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Testowanie wydajności usługi w chmurze
## <a name="overview"></a>Omówienie
Należy przetestować wydajność usługi w chmurze, w następujący sposób:

* Zbieranie informacji na temat połączeń i żądań i przejrzyj statystyki witryny, które pokazują, jak działa usługa z perspektywy klienta, należy użyć usługi Azure Diagnostics. Aby rozpocząć, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Użyj programu Visual Studio profiler, aby uzyskać szczegółowe analizy obliczeniowe aspektami działania usługi. Zgodnie z opisem w tym temacie, można użyć programu profilującego do pomiaru wydajności, ponieważ usługa działa na platformie Azure. Aby uzyskać informacje o sposobie używania programu profilującego do pomiaru wydajności, ponieważ usługa jest uruchamiany lokalnie w emulatorze obliczeń, zobacz [testowanie wydajności usługi Azure Cloud Service lokalnie na obliczenia Emulator za pomocą Profiler usługi Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Wybieranie metody testowania wydajnościowego
### <a name="use-azure-diagnostics-to-collect"></a>Umożliwia zbieranie diagnostyki platformy Azure:
* Statystyki na stronach sieci web lub usług, takich jak żądania i połączenia.
* Statystyki dotyczące ról, takich jak częstotliwość ponownego uruchamiania roli.
* Ogólne informacje na temat użycia pamięci, takie jak procent czasu, wykorzystującej przez moduł odśmiecania pamięci i pamięci zestaw uruchomionej roli.

### <a name="use-the-visual-studio-profiler-to"></a>Użyj programu Visual Studio profiler do:
* Określ, jakie funkcje zajmuje najwięcej czasu.
* Zmierz czas, jaki zajmuje każdej części programu wymaga dużej mocy obliczeniowej.
* Porównanie wydajności szczegółowe raporty dotyczące dwóch wersji usługi.
* Analizuj alokacji pamięci, które bardziej szczegółowo niż poziom alokacji pamięci indywidualnych.
* Analizy współbieżności problemów w kodzie wielowątkowych.

Gdy używasz programu profilującego, można zbierać dane, po uruchomieniu usługi w chmurze, lokalnie lub na platformie Azure.

### <a name="collect-profiling-data-locally-to"></a>Zbieranie danych profilowania lokalnie do:
* Testowanie wydajności część usługi w chmurze, takich jak wykonywanie roli procesu roboczego w określonych, która nie wymaga realistyczne symulowane obciążenia.
* Testowanie wydajności usługi w chmurze w przypadku izolacji w warunkach kontrolowanych.
* Testowanie wydajności usługi w chmurze, przed wdrożeniem na platformie Azure.
* Testowanie wydajności usługi w chmurze prywatnie, bez zakłócania działania istniejących wdrożeń.
* Testowanie wydajności usługi bez naliczania opłat do uruchamiania na platformie Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Zbierz profilowania danych na platformie Azure, aby:
* Testowanie wydajności usługi w chmurze w warunkach obciążenia symulowanego lub rzeczywistej.
* Metoda Instrumentacji zbierania danych profilowania, ponieważ w tym temacie opisano w dalszej części.
* Przetestuj wydajność usługi, w tym samym środowisku, co jeśli usługa jest uruchamiana w środowisku produkcyjnym.

Zazwyczaj można symulować ładowanie do usługi test cloud services w normalnych lub warunkach obciążenia.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilowanie usługi w chmurze na platformie Azure
Podczas publikowania usługi w chmurze w programie Visual Studio, możesz profilu usługi i określ ustawienia profilowania, dające informacje, które mają. Sesję profilowania jest uruchomiony dla każdego wystąpienia roli. Aby uzyskać więcej informacji o sposobie publikowania usługi w programie Visual Studio, zobacz [publikowanie do usługi w chmurze platformy Azure z programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

Aby dowiedzieć się więcej na temat profilowanie ich wydajności w programie Visual Studio, zobacz [profilowanie wydajności — przewodnik dla początkujących](https://msdn.microsoft.com/library/azure/ms182372.aspx) i [analizowanie wydajności aplikacji przy użyciu narzędzi profilowania](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Można włączyć funkcji IntelliTrace lub profilowania po opublikowaniu usługi w chmurze. Nie można włączyć jednocześnie.
>
>

### <a name="profiler-collection-methods"></a>Metody zbierania Profiler
Inną kolekcję metody służą do profilowania, oparte na problemy z wydajnością:

* **Próbkowanie Procesora** — ta metoda służy do zbierania statystyk aplikacji, które są przydatne w przypadku początkowej analizy problemy dotyczące użycia procesora CPU. Próbkowanie Procesora jest sugerowane metody uruchamiania większość badania wydajności. Istnieje mały wpływ na aplikację, która profilowany podczas zbierania danych próbkowania procesora CPU.
* **Instrumentacja** — ta metoda służy do zbierania danych o chronometrażu, które są przydatne na potrzeby ukierunkowanej analizy i analizowania problemów z wydajnością we/wy. Metody Instrumentacji rejestruje każdego wpisu, zakończenia i wywołanie funkcji funkcje w module podczas uruchomienia profilowania. Ta metoda jest przydatne do zbierania informacji chronometrażu o sekcji kodu i zrozumienie wpływu na operacje wejścia i wyjścia na wydajność aplikacji. Ta metoda jest wyłączona na komputerze 32-bitowym systemie operacyjnym. Ta opcja jest dostępna tylko po uruchomieniu usługi w chmurze na platformie Azure, nie lokalnie w emulatorze obliczeń.
* **Alokacji pamięci .NET** — ta metoda zbiera dane alokacji pamięci .NET Framework przy użyciu metoda profilowania próbkowanie. Zbierane dane obejmują liczbę i rozmiar istnienia przydzielonych obiektów.
* **Współbieżność** — ta metoda służy do zbierania danych kontencji zasobów i danych wykonywania procesu i wątku, który jest przydatny podczas analizowania aplikacji wielowątkowych i wielu procesów. Metody współbieżności zbiera dane dla każdego zdarzenia, że bloki wykonywania kodu, takie jak kiedy wątek czeka na zablokowany dostęp do zasobu aplikacji ma zostać zwolniony. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.
* Można również włączyć **profilowanie interakcji pomiędzy warstwami**, która zapewnia dodatkowe informacje na temat czasu wykonania ADO.NET synchroniczne wywołania w funkcje aplikacji wielowarstwowych, które komunikują się z co najmniej jednej bazy danych. Dane interakcji między warstwami można zbierać za pomocą dowolnej z metod profilowania. Aby uzyskać więcej informacji o profilowaniu interakcji między warstwami, zobacz [widok interakcji między warstwami](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Konfigurowanie ustawień profilowania
Na poniższej ilustracji pokazano, jak skonfigurować ustawienia profilowania w oknie dialogowym Publikowanie aplikacji platformy Azure.

![Konfigurowanie ustawień profilowania](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Aby włączyć **Włącz profilowanie** pole wyboru, konieczne jest posiadanie programu profilującego zainstalowane na komputerze lokalnym, którego używasz do publikowania swojej usługi w chmurze. Domyślnie program profilujący jest instalowany podczas instalowania programu Visual Studio.
>
>

### <a name="to-configure-profiling-settings"></a>Aby skonfigurować ustawienia profilowania
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz **Publikuj**. Aby uzyskać szczegółowe instrukcje dotyczące publikowania usługi w chmurze, zobacz [publikowania usługi w chmurze przy użyciu narzędzi Azure](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. W **publikowanie aplikacji platformy Azure** okno dialogowe, wybierz **Zaawansowane ustawienia** kartę.
3. Aby włączyć profilowanie, zaznacz **Włącz profilowanie** pole wyboru.
4. Aby skonfigurować ustawienia profilowania, wybierz **ustawienia** hiperłącze. Zostanie wyświetlone okno dialogowe Ustawienia profilowania.
5. Z **profilowanie jakiego metodą chcesz użyć** przyciski opcji, wybierz typ profilowania, że jest wymagane.
6. Aby zebrać obejrzeć takie dane, wybierz **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.
7. Aby zapisać ustawienia, wybierz opcję **OK** przycisku.

    Podczas publikowania tej aplikacji, te ustawienia są używane do tworzenia sesji profilowania dla każdej roli.

## <a name="viewing-profiling-reports"></a>Wyświetlanie raportów profilowania
Sesję profilowania jest tworzony dla każdego wystąpienia roli w usłudze w chmurze. Aby wyświetlić raporty profilowania każdej sesji z programu Visual Studio, można wyświetlić okno Eksploratora serwera, a następnie wybierz węzeł usługi Azure Compute, aby wybrać wystąpienie roli. Następnie możesz wyświetlić raport profilowania, jak pokazano na poniższej ilustracji.

![Zobrazit Sestavu Profilace z platformy Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Aby wyświetlić raporty profilowania
1. Aby wyświetlić okno Eksploratora serwera w programie Visual Studio, na pasku menu wybierz widok Eksploratora serwera.
2. Wybierz węzeł obliczeń Azure, a następnie wybierz węzeł wdrażania platformy Azure dla usługi w chmurze, wybranego profilu podczas publikowania z programu Visual Studio.
3. Aby wyświetlić raporty profilowania w przypadku wystąpienia, wybierz rolę, usługi, otwórz menu skrótów dla konkretnego wystąpienia, a następnie wybierz **Wyświetl raport profilowania**.

    Raport plik Vsp jest teraz pobierane z platformy Azure, a stan pobierania zostanie wyświetlony w dzienniku aktywności platformy Azure. Po zakończeniu pobierania raportu profilowania pojawia się na karcie w edytorze programu Visual Studio o nazwie < Nazwa roli\>*< numer wystąpienia\>*< identyfikator\>Vsp. Zostanie wyświetlone podsumowanie danych dla tego raportu.
4. Aby wyświetlić różne widoki tego raportu, na liście bieżącego widoku, wybierz typ widoku, który chcesz. Aby uzyskać więcej informacji, zobacz [widoków raportów narzędzi profilowania](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Następne kroki
[Debugowanie usług w chmurze](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Publikowanie w usłudze w chmurze platformy Azure z programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)
