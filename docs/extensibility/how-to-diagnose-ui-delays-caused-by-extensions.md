---
title: Diagnozowanie opóźnień interfejsu użytkownika w programie Visual Studio | Microsoft Docs
description: Program Visual Studio powiadamia o tym, czy opóźnienia interfejsu użytkownika mogą być spowodowane przez rozszerzenie. Dowiedz się, jak zdiagnozować zawartość kodu rozszerzenia, powodując opóźnienia interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jmartens
ms.workload: multiple
ms.openlocfilehash: 508fdd44a1c73f66d88317b7ec304e810f5f12e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890802"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Instrukcje: diagnozowanie opóźnień w interfejsie użytkownika powodowanych przez rozszerzenia

Gdy interfejs użytkownika przestanie odpowiadać, program Visual Studio sprawdzi stos wywołań wątku interfejsu użytkownika, rozpoczynając od liścia i pracując nad bazą. Jeśli program Visual Studio określi, że ramka stosu wywołań należy do modułu, który jest częścią zainstalowanego i włączonego rozszerzenia, pokazuje powiadomienie.

![Powiadomienie dotyczące opóźnień interfejsu użytkownika (nieodpowiadania)](media/ui-delay-notification-in-vs.png)

Powiadomienie informuje użytkownika o tym, że opóźnienie interfejsu użytkownika (czyli czas braku odpowiedzi w interfejsie użytkownika) mogło być wynikiem kodu z rozszerzenia. Udostępnia także użytkownikowi opcje umożliwiające wyłączenie rozszerzenia lub przyszłe powiadomienia dla tego rozszerzenia.

W tym dokumencie opisano, jak można zdiagnozować, co w kodzie rozszerzenia powoduje, że powiadomienia o opóźnieniu interfejsu użytkownika.

> [!NOTE]
> Nie używaj eksperymentalnego wystąpienia programu Visual Studio, aby zdiagnozować opóźnienia interfejsu użytkownika. Niektóre części analizy stosu wywołań wymagane przez funkcję powiadomień opóźnienia interfejsu użytkownika są wyłączone podczas korzystania z wystąpienia eksperymentalnego, co oznacza, że powiadomienia o opóźnieniu interfejsu użytkownika mogą nie być wyświetlane.

Przegląd procesu diagnostycznego jest następujący:
1. Zidentyfikuj scenariusz wyzwalacza.
2. Uruchom ponownie program VS z rejestrowaniem aktywności.
3. Uruchom śledzenie ETW.
4. Wyzwól powiadomienie, aby pojawiło się ponownie.
5. Zatrzymaj śledzenie ETW.
6. Przejrzyj dziennik aktywności, aby uzyskać identyfikator opóźnienia.
7. Analizowanie śledzenia ETW przy użyciu identyfikatora opóźnienia z kroku 6.

W poniższych sekcjach opisano te kroki bardziej szczegółowo.

## <a name="identify-the-trigger-scenario"></a>Identyfikowanie scenariusza wyzwalacza

Aby zdiagnozować opóźnienie interfejsu użytkownika, należy najpierw określić, co (sekwencja akcji) powoduje, że program Visual Studio wyświetli powiadomienie. Jest to możliwe, aby móc wyzwolić powiadomienie później z włączonym logowaniem.

## <a name="restart-vs-with-activity-logging-on"></a>Uruchom ponownie program VS z rejestrowaniem aktywności

Program Visual Studio może generować "Dziennik aktywności", który zapewnia informacje pomocne podczas debugowania problemu. Aby włączyć rejestrowanie aktywności w programie Visual Studio, Otwórz program Visual Studio z `/log` opcją wiersza polecenia. Po uruchomieniu programu Visual Studio Dziennik aktywności jest przechowywany w następującej lokalizacji:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Aby dowiedzieć się więcej o tym, jak można znaleźć identyfikator wystąpienia programu VS, zobacz [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](../install/tools-for-managing-visual-studio-instances.md). Ten dziennik aktywności zostanie użyty później, aby uzyskać więcej informacji na temat opóźnień interfejsu użytkownika i powiązanych powiadomień.

## <a name="starting-etw-tracing"></a>Uruchamianie śledzenia ETW

Za pomocą [Narzędzia PerfView](https://github.com/Microsoft/perfview/) można zbierać dane śledzenia ETW. Narzędzia PerfView zapewnia łatwy w użyciu interfejs do zbierania śledzenia ETW i analizowania go. Użyj następującego polecenia, aby zebrać ślad:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Umożliwia to dostawcy "Microsoft-VisualStudio", który jest dostawcą używanym przez program Visual Studio do zdarzeń związanych z powiadomieniami o opóźnieniu interfejsu użytkownika. Określa także słowo kluczowe dla dostawcy jądra, którego narzędzia PerfView może użyć do wygenerowania widoku **stosów czasu wątku** .

## <a name="trigger-the-notification-to-appear-again"></a>Wyzwól powiadomienie, aby pojawiło się ponownie

Po rozpoczęciu zbierania śladów przez narzędzia PerfView można użyć sekwencji akcji wyzwalacza (z kroku 1), aby powiadomienie pojawiało się ponownie. Po wyświetleniu powiadomienia można zatrzymać zbieranie danych śledzenia dla narzędzia PerfView, aby przetwarzać i generować wyjściowy plik śledzenia.

## <a name="stop-etw-tracing"></a>Zatrzymaj śledzenie ETW

Aby zatrzymać zbieranie śladów, po prostu Użyj przycisku **Zatrzymaj zbieranie** w oknie narzędzia PerfView. Po zatrzymaniu zbierania danych śledzenia program narzędzia PerfView automatycznie przetworzy zdarzenia ETW i wygeneruje wyjściowy plik śledzenia.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Badanie dziennika aktywności w celu uzyskania identyfikatora opóźnienia

Jak wspomniano wcześniej, można znaleźć dziennik aktywności w *%APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml*. Za każdym razem, gdy program Visual Studio wykrywa opóźnienie interfejsu użytkownika rozszerzenia, zapisuje węzeł do dziennika aktywności ze `UIDelayNotifications` źródłem. Ten węzeł zawiera cztery informacje o opóźnieniu interfejsu użytkownika:

- Identyfikator opóźnienia interfejsu użytkownika, numer sekwencyjny, który jednoznacznie identyfikuje opóźnienie interfejsu użytkownika w sesji programu VS
- Identyfikator sesji, który jednoznacznie identyfikuje sesję programu Visual Studio od początku do zamknięcia
- Niezależnie od tego, czy pokazywane jest powiadomienie dotyczące opóźnień interfejsu użytkownika
- Rozszerzenie, które prawdopodobnie spowodowało opóźnienie interfejsu użytkownika

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Nie wszystkie opóźnienia interfejsu użytkownika powodują powiadomienie. W związku z tym należy zawsze sprawdzać **pokazane powiadomienia?** wartość, aby prawidłowo identyfikować odpowiednie opóźnienie interfejsu użytkownika.

Po znalezieniu prawidłowego opóźnienia interfejsu użytkownika w dzienniku aktywności Zapisz identyfikator opóźnienia interfejsu użytkownika określony w węźle. Użyj identyfikatora, aby wyszukać odpowiednie zdarzenie ETW w następnym kroku.

## <a name="analyze-the-etw-trace"></a>Analizowanie śledzenia ETW

Następnie otwórz plik śledzenia. Można to zrobić przy użyciu tego samego wystąpienia narzędzia PerfView lub przez uruchomienie nowego wystąpienia i ustawienie bieżącej ścieżki folderu w lewym górnym rogu okna do lokalizacji pliku śledzenia.

![Ustawianie ścieżki folderu w narzędzia PerfView](media/perfview-set-path.png)

Następnie wybierz plik śledzenia w okienku po lewej stronie i otwórz go, wybierając pozycję **Otwórz** w menu kontekstowym lub prawym przyciskiem myszy.

> [!NOTE]
> Domyślnie narzędzia PerfView wyprowadza archiwum zip. Po otwarciu *trace.zip* automatycznie dekompresuje archiwum i otwiera śledzenie. Możesz to pominąć, usuwając zaznaczenie pola **zip** podczas zbierania śladu. Jeśli jednak planujesz transfer i używanie śladów na różnych komputerach, zdecydowanie zalecamy, aby nie sprawdzać pola **zip** . Bez tej opcji wymagane plików PDB dla zestawów NGen nie towarzyszy śledzeniu i w rezultacie symbole z zestawów NGen nie zostaną rozwiązane na maszynie docelowej. (Zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) , aby uzyskać więcej informacji na temat plików PDB dla zestawów NGen).

Przetworzenie i otwieranie śledzenia przez narzędzia PerfView może potrwać kilka minut. Po otwarciu śledzenia zostanie wyświetlona lista różnych "widoków".

![Widok podsumowania śledzenia narzędzia PerfView](media/perfview-summary-view-events-selected.png)

Najpierw będziemy używać widoku **zdarzeń** , aby uzyskać zakres czasu opóźnienia interfejsu użytkownika:

1. Otwórz widok **zdarzenia** , zaznaczając `Events` węzeł w obszarze ślad i wybierając pozycję **Otwórz** w menu kontekstowym lub prawym przyciskiem myszy.
2. Wybierz pozycję " `Microsoft-VisualStudio/ExtensionUIUnresponsiveness` " w lewym okienku.
3. Naciśnij klawisz ENTER

Wybór zostanie zastosowany, a wszystkie `ExtensionUIUnresponsiveness` zdarzenia są wyświetlane w okienku po prawej stronie.

![Wybieranie zdarzeń w widoku zdarzeń](media/perfview-event-selection.png)

Każdy wiersz w prawym okienku odnosi się do opóźnienia interfejsu użytkownika. Zdarzenie zawiera wartość "Delay ID", która powinna być zgodna z IDENTYFIKATORem opóźnienia w dzienniku aktywności z kroku 6. Ponieważ `ExtensionUIUnresponsiveness` jest uruchamiany na końcu opóźnienia interfejsu użytkownika, sygnatura czasowa zdarzenia (w przybliżeniu) oznacza godzinę zakończenia opóźnienia interfejsu użytkownika. Zdarzenie zawiera również czas trwania opóźnienia. Aby uzyskać sygnaturę czasową uruchomienia opóźnienia interfejsu użytkownika, można odjąć czas trwania od sygnatury czasowej końca.

![Obliczanie czasu opóźnienia interfejsu użytkownika](media/ui-delay-time-range.png)

Na przykład na poprzednim zrzucie ekranu sygnatura czasowa zdarzenia to 12 125,679, a czas opóźnienia wynosi 6 143,085 (MS). Tak więc,
* Opóźnienie zaczyna się od 12 125,679-6 143,085 = 5 982,594.
* Zakres czasu opóźnienia interfejsu użytkownika to 5 982,594 do 12 125,679.

Po określeniu zakresu czasu można zamknąć widok **zdarzenia** i otworzyć widok **stosy czasu wątku (z działaniami StartStop)** . Ten widok jest szczególnie przydatny, ponieważ często rozszerzenia blokujące wątek interfejsu użytkownika są tylko oczekujące na inne wątki lub operacje we/wy. W związku z tym widok **stosu procesora CPU** , który jest opcjami do wykonania w większości przypadków, może nie przechwycić czasu, przez który wątek zablokuje, ponieważ nie używa procesora CPU w tym czasie. **Stosy czasu wątku** rozwiązują ten problem, prawidłowo pokazując zablokowany czas.

![Węzeł Stacks (z działaniami StartStop) w widoku podsumowania narzędzia PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Podczas otwierania widoku **stosów czasu wątku** wybierz proces **devenv** , aby rozpocząć analizę.

![Widok stosów czasu wątku dla analizy opóźnień interfejsu użytkownika](media/ui-delay-thread-time-stacks.png)

W widoku **stosy czasu wątku** w lewym górnym rogu strony możesz ustawić zakres czasu na wartości, które są obliczane w poprzednim kroku, a następnie naciśnij klawisz **Enter** , aby stosy zostały dostosowane do tego zakresu czasu.

> [!NOTE]
> Określanie wątku jest wątkiem interfejsu użytkownika (uruchamiania) można nielogiczna, jeśli zbieranie śladów zostało rozpoczęte po otwarciu programu Visual Studio. Jednak pierwsze elementy na stosie wątku interfejsu użytkownika (Startup) najprawdopodobniej są zawsze w systemie operacyjnym (*ntdll.dll* i *kernel32.dll*) `devenv!?` , a następnie, a następnie `msenv!?` . Ta sekwencja może pomóc w identyfikacji wątku interfejsu użytkownika.

 ![Identyfikowanie wątku startowego](media/ui-delay-startup-thread.png)

Możesz również dodatkowo filtrować ten widok, dołączając tylko stosy zawierające moduły z pakietu.

* Ustaw **GroupPats** na pusty tekst, aby usunąć wszystkie grupowanie dodane domyślnie.
* Ustaw **IncPats** , aby uwzględnić część nazwy zestawu oprócz istniejącego filtru procesów. W takim przypadku powinna być **devenv; UIDelayR2**.

![Ustawianie GroupPath i IncPath w widoku stosów czasu wątku](media/perfview-tts-group-path-inc-path.png)

Narzędzia PerfView zawiera szczegółowe wskazówki w menu **Pomoc** , których można użyć do identyfikowania wąskich gardeł wydajności w kodzie. Ponadto poniższe linki zawierają więcej informacji na temat sposobu korzystania z interfejsów API tworzenia wątków programu Visual Studio w celu optymalizacji kodu:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Możesz również użyć nowych analizatorów statycznych programu Visual Studio dla rozszerzeń (pakiet NuGet [tutaj](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), które zapewniają wskazówki dotyczące najlepszych rozwiązań dotyczących pisania wydajnych rozszerzeń. Zobacz listę [analizatorów zestawu SDK vs](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) i [analizatorów wątków](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Jeśli nie możesz rozwiązać odpowiedzi z powodu zależności, na które nie masz kontroli (na przykład jeśli Twoje rozszerzenie ma wywoływać synchroniczne usługi VS w wątku interfejsu użytkownika), chcielibyśmy wiedzieć o tym. Jeśli jesteś członkiem naszego programu partnerskiego Visual Studio, możesz skontaktować się z nami, przesyłając żądanie pomocy technicznej dla deweloperów. W przeciwnym razie użyj narzędzia "Zgłoś problem", aby przesłać swoją opinię i dołączyć do `"Extension UI Delay Notifications"` tytułu. Zapoznaj się również z szczegółowym opisem analizy.
