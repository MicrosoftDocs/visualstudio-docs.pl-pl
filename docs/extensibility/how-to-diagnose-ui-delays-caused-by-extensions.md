---
title: Rozszerzenia interfejsu użytkownika diagnozowanie opóźnień w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: c4852e3c760f2974620f0a6c641a540b92d19bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957445"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Instrukcje: Diagnozowanie opóźnień w interfejsie użytkownika powodowanych przez rozszerzenia

Gdy interfejs użytkownika przestanie odpowiadać, Visual Studio sprawdza, czy stos wywołań wątku interfejsu użytkownika, począwszy od typu liść i pracą z nimi na podstawie. Jeśli program Visual Studio okaże się, że ramka stosu wywołań należy do modułu, który jest częścią rozszerzenia zainstalowane i włączone, wyświetlane jest powiadomienie.

![Opóźnienie reakcji interfejsu użytkownika (sek) powiadomień](media/ui-delay-notification-in-vs.png)

Powiadomienia informuje użytkownika, że opóźnienie reakcji interfejsu użytkownika (oznacza to problem z brakiem odpowiedzi w interfejsie użytkownika) mogły być wynikiem kodu z rozszerzeniem. Zapewnia również użytkowników z opcjami, aby wyłączyć rozszerzenie lub kolejnych powiadomień dotyczących tego rozszerzenia.

W tym dokumencie opisano, jak diagnozować, co w kodzie rozszerzenia powoduje powiadomienia dotyczące opóźnienia interfejsu użytkownika. 

> [!NOTE]
> Nie należy używać wystąpienie eksperymentalne programu Visual Studio do diagnozowania występują opóźnienia interfejsu użytkownika. Niektóre części analiz stos wywołań, wymaganych w celu powiadomienia dotyczące opóźnienia interfejsu użytkownika są wyłączone, gdy jest używane wystąpienie eksperymentalne, co oznacza, że powiadomienia dotyczące opóźnienia interfejsu użytkownika mogą nie być wyświetlane.

Omówienie procesu diagnostycznych jest następująca:
1. Identyfikowanie scenariusza wyzwalacza.
2. Za pomocą działania logowania, należy ponownie uruchomić program VS.
3. Uruchom śledzenie zdarzeń systemu Windows.
4. Wyzwalanie powiadomienie, aby ponownie wyświetlone.
5. Zatrzymaj śledzenie.
6. Sprawdź dziennik aktywności, aby uzyskać identyfikator opóźnienia.
7. Analizuj śledzenie zdarzeń systemu Windows przy użyciu Identyfikatora opóźnienia w kroku 6.

W poniższych sekcjach opiszemy kroki opisane w bardziej szczegółowo.

## <a name="identify-the-trigger-scenario"></a>Identyfikowanie scenariusza wyzwalacza

Aby zdiagnozować opóźnienie reakcji interfejsu użytkownika, należy najpierw zidentyfikować jakie (sekwencję akcji) powoduje, że Visual Studio wyświetlić powiadomienie. Jest to w celu uzyskania, aby było możliwe jego wyzwalać powiadomienie później za pomocą funkcji rejestrowania włączona.

## <a name="restart-vs-with-activity-logging-on"></a>Uruchom ponownie program VS za pomocą działania logowania

Program Visual Studio można wygenerować "Dziennik aktywności" który informacje pomocne przy debugowaniu problemu. Aby włączyć funkcję rejestrowania w programie Visual Studio aktywności, uruchom program Visual Studio za pomocą `/log` opcji wiersza polecenia. Po uruchomieniu programu Visual Studio, w dzienniku aktywności są przechowywane w następującej lokalizacji:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Aby dowiedzieć się więcej na temat sposobu można znaleźć usługi VS identyfikator wystąpienia, zobacz [narzędzia do wykrywania i Zarządzanie wystąpieniami programu Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Firma Microsoft użyje tego dziennika aktywności później Aby dowiedzieć się więcej informacji na temat występują opóźnienia interfejsu użytkownika i związanych z nią powiadomień.

## <a name="starting-etw-tracing"></a>Począwszy od śledzenia zdarzeń systemu Windows

Możesz użyć [narzędzia PerfView](https://github.com/Microsoft/perfview/) zbierać ETW śledzenia. Narzędzia PerfView zapewnia łatwy w użyciu interfejs zarówno zbieranie, śledzenie zdarzeń systemu Windows oraz je analizować. Aby zbierać dane śledzenia, należy użyć następującego polecenia:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Dzięki temu dostawcy "Microsoft VisualStudio", który jest dostawcą, używanych przez program Visual Studio dla zdarzeń związanych z powiadomienia dotyczące opóźnienia interfejsu użytkownika. Określa również słowo kluczowe dostawcy jądra, który można użyć narzędzia PerfView, aby wygenerować **wątku stosów czasu** widoku.

## <a name="trigger-the-notification-to-appear-again"></a>Powiadomienie, aby ponownie wyzwalacz

Po rozpoczęciu zbierania śladu narzędzia PerfView umożliwia sekwencję akcji wyzwalacza (z kroku 1), powiadomienia pojawiają się ponownie. Gdy zostanie wyświetlone powiadomienie, można zatrzymać śledzenia kolekcji dla narzędzia PerfView do przetwarzania i wygenerowanie pliku danych wyjściowych śledzenia.

## <a name="stop-etw-tracing"></a>Zatrzymaj śledzenie

Aby zatrzymać zbieranie śledzenia, po prostu użyć **Zatrzymaj Kolekcjonowanie** przycisk w oknie narzędzia PerfView. Po zatrzymaniu zbierania śladu narzędzia PerfView będzie automatycznie przetwarzać zdarzenia ETW i generuje dane wyjściowe pliku śledzenia.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Sprawdź dziennik aktywności, aby uzyskać identyfikator opóźnienia

Jak wspomniano wcześniej, można znaleźć dziennika aktywności w *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.XML*. Za każdym razem, gdy program Visual Studio wykryje rozszerzenie opóźnienie reakcji interfejsu użytkownika, zapisuje węzła do dziennika aktywności przy użyciu `UIDelayNotifications` jako źródło. Ten węzeł zawiera cztery fragmentów informacji dotyczących opóźnienie reakcji interfejsu użytkownika:

- Identyfikator opóźnienia interfejsu użytkownika, a kolejny numer, który unikatowo identyfikuje opóźnienie reakcji interfejsu użytkownika w sesji programu VS
- Identyfikator sesji, który unikatowo identyfikuje sesję programu Visual Studio od początku, aby zamknąć
- Określa, czy powiadomienia wyświetleniem opóźnienia interfejsu użytkownika
- Rozszerzenie, które prawdopodobnie spowodowało opóźnienie reakcji interfejsu użytkownika

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
> Nie wszystkie występują opóźnienia interfejsu użytkownika powoduje powiadomienie. W związku z tym, należy zawsze sprawdzić **powiadomień wyświetlane?** wartość, aby prawidłowo identyfikować odpowiednie opóźnienie reakcji interfejsu użytkownika.

Po znalezieniu poprawne opóźnienie reakcji interfejsu użytkownika w dzienniku aktywności Zanotuj identyfikator opóźnienia interfejsu użytkownika, określona w węźle. Identyfikator użyjemy do wyszukania odpowiadające zdarzenie ETW w następnym kroku.

## <a name="analyze-the-etw-trace"></a>Analizowanie śledzenie zdarzeń systemu Windows

Następnie otwórz plik śledzenia. Można to zrobić przy użyciu tego samego wystąpienia narzędzia PerfView lub uruchamia nowe wystąpienie i ustawiając bieżącą ścieżkę folderu w górnym lewym rogu okna do lokalizacji pliku śledzenia.

![Ustawienie w ścieżce folderu w Perfview](media/perfview-set-path.png)

Następnie wybierz plik śledzenia w okienku po lewej stronie i otwórz go, wybierając **Otwórz** w menu kliknij prawym przyciskiem myszy lub kontekstu.

> [!NOTE]
> Domyślnie narzędzia PerfView generuje archiwum Zip. Po otwarciu *trace.zip*, automatycznie dekompresuje archiwum i otwiera śledzenia. Możesz to pominąć, usuwając zaznaczenie pola **Zip** pola podczas zbierania śladu. Jednak jeśli planowane jest transferu i używanie śledzenia na różnych komputerach, zdecydowanie zalecamy względem usuwając zaznaczenie pola wyboru **Zip** pole. Bez tej opcji wymagane pliki PDB dla zestawów Ngen nie będzie towarzyszyć śledzenia i dlatego symbole z Ngen zestawów, nie będą rozpoznawane na komputerze docelowym. (Zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) Aby uzyskać więcej informacji na temat plików PDB dla zestawów Ngen.) 

Może potrwać kilka minut, zanim programu PerfView do przetwarzania i Otwórz śledzenie. Po otwarciu śledzenia listę różnych "widoków" pojawiają się w nim.

![Widok podsumowania ślad narzędzia PerfView](media/perfview-summary-view-events-selected.png)

Firma Microsoft w pierwszej kolejności używają **zdarzenia** widok, aby uzyskać przedział czasu opóźnienie reakcji interfejsu użytkownika:

1. Otwórz **zdarzenia** widoku, wybierając `Events` węźle śledzenia i wybierając pozycję **Otwórz** w menu kliknij prawym przyciskiem myszy lub kontekstu.
2. Wybierz pozycję "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" w okienku po lewej stronie.
3. Naciśnij klawisz Enter

Zaznaczenie jest stosowana i wszystkich `ExtensionUIUnresponsiveness` zdarzenia są wyświetlane w okienku po prawej stronie.

![Wybierając zdarzenia w widoku zdarzeń](media/perfview-event-selection.png)

Każdy wiersz w okienku po prawej stronie odnosi się do opóźnienia interfejsu użytkownika. Zdarzenie zawiera wartość "Opóźnienie ID elementu", który powinien być zgodny z Identyfikatorem opóźnienia w dzienniku aktywności w kroku 6. Ponieważ `ExtensionUIUnresponsiveness` jest wywoływane na końcu opóźnienie reakcji interfejsu użytkownika, sygnatura czasowa zdarzenia (w przybliżeniu) znaki czas zakończenia opóźnienie reakcji interfejsu użytkownika. Zdarzenie zawiera także czas trwania zwłoki. Firma Microsoft jest przypisany typ czasu trwania z końcowa sygnatura czasowa w celu uzyskania sygnatury czasowej podczas uruchamiania opóźnienie reakcji interfejsu użytkownika.

![Obliczanie opóźnienia interfejsu użytkownika w zakres czasu](media/ui-delay-time-range.png)

Na poprzednim zrzucie ekranu na przykład sygnatura czasowa zdarzenia jest 12,125.679 i czas trwania opóźnienia jest 6,143.085 (ms). Tak więc,
* Opóźnienie rozpoczęcia jest 12,125.679 6,143.085 = 5,982.594.
* Zakres czasu opóźnienia interfejsu użytkownika jest 5,982.594 do 12,125.679.

Gdy będziemy już mieć zakres czasu, możemy zamknąć poza **zdarzenia** Wyświetl i Otwórz **stosy wątków czasu (z działaniami StartStop)** widoku. Ten widok jest szczególnie przydatne, ponieważ często tych rozszerzeń, które blokują wątek interfejsu użytkownika nie tylko oczekuje na innych wątków lub operacji I/O-powiązane z. W efekcie **stosu Procesora** widoku, który jest idealną opcję w większości przypadków, nie mogą przechwytywać czasu wątku korzystało z blokowaniem, ponieważ w tym czasie nie używa procesora CPU. **Wątku stosów czasu** rozwiązuje ten problem, prawidłowo czas wyświetlania zablokowanych.

![Węzeł stosów czasu (z działaniami StartStop) wątku w widoku podsumowania narzędzia PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Podczas otwierania **wątku stosów czasu** wyświetlić, wybierz **devenv** procesu można rozpocząć analizy.

![Widok stosów czasu dla analiza opóźnienia interfejsu użytkownika wątku](media/ui-delay-thread-time-stacks.png)

W **wątku stosów czasu** wyświetlić, w górnym lewym rogu strony, można ustawić przedział czasu do wartości, firma Microsoft obliczona w poprzednim kroku, a następnie naciśnij klawisz **Enter** tak stosy są dostosowywane do tego zakresu czasu.

> [!NOTE]
> Określanie, który wątek będzie interfejs użytkownika wątku (startowych) może być nielogiczna, jeśli zbierania śladu jest uruchomione, gdy program Visual Studio jest już otwarty. Jednak pierwszych elementów na stosie wątku interfejsu użytkownika (startowych) są najbardziej prawdopodobną zawsze bibliotek DLL systemu operacyjnego (*ntdll.dll* i *kernel32.dll*) następuje `devenv!?` i następnie `msenv!?` . Ta sekwencja może być pomocny w zidentyfikowaniu wątku interfejsu użytkownika.

 ![Identyfikowanie uruchamiania wątku](media/ui-delay-startup-thread.png)

W tym widoku można również filtrować według tylko tym stosów, które zawierają moduły z pakietu.

* Ustaw **GroupPats** na pusty tekst, aby usunąć wszelkie grupowanie dodawany domyślnie.
* Ustaw **IncPats** obejmujący część Twoja nazwa zestawu, oprócz istniejącego filtru procesu. W tym przypadku powinien być **devenv; UIDelayR2**.

![Ustawianie GroupPath i IncPath w widoku wątków stosów czasu](media/perfview-tts-group-path-inc-path.png)

Narzędzia PerfView zawiera szczegółowe wskazówki, w obszarze **pomocy** menu, który służy do identyfikowania wąskich gardeł wydajności w kodzie. Ponadto poniższe linki zawierają dodatkowe informacje na temat Korzystanie z programu Visual Studio wątkowości interfejsy API w celu optymalizacji kodu:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Umożliwia także nowe analizatory statyczne programu Visual Studio dla rozszerzeń (pakiet NuGet [tutaj](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), który wytyczne dotyczące najlepszych rozwiązań do tworzenia rozszerzenia wydajne. Wyświetlenie listy [analizatory zestawu SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) i [wątkowości analizatory](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Jeśli nie możesz rozwiązać problem z brakiem odpowiedzi z powodu zależności nie masz kontrolę nad (na przykład, jeśli ma rozszerzenie do wywołania synchroniczne usług VS w wątku interfejsu użytkownika), chcemy o tym wiedzieć. Jeśli jesteś członkiem programu naszych partnerów programu Visual Studio, użytkownik może się z nami, przesyłając żądanie pomocy technicznej developer. W przeciwnym razie użyj narzędzia "Zgłoś Problem" Prześlij opinię i dołączenie `"Extension UI Delay Notifications"` w tytule. Uwzględnij również szczegółowy opis analizy.
