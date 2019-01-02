---
title: 'Instrukcje: Diagnozowanie wydajności rozszerzenia | Dokumentacja firmy Microsoft'
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: fd51728f5e57af1017cb4b280f9ffc9d1c50df98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943424"
---
# <a name="measuring-extension-impact-in-startup"></a>Mierzenie wpływu rozszerzenie przy uruchamianiu

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Skup się na wydajności rozszerzenia programu Visual Studio 2017

Na podstawie opinii klientów, jeden obszarach zainteresowań dla wersji programu Visual Studio 2017 został wydajność ładowania uruchamiania i rozwiązania. Zespół platformy Visual Studio Dokładamy wszelkich starań dotyczące poprawy wydajności obciążenia uruchamiania i rozwiązania. Ogólnie rzecz biorąc nasze pomiarów sugerują, zainstalowanych rozszerzeń również może mieć znaczący wpływ na tych scenariuszy.

Aby ułatwić użytkownikom poznania zakresu przedstawionego wypływu, dodaliśmy nową funkcję w programie Visual Studio w celu powiadomienia użytkowników o powolne rozszerzenia. Czasami program Visual Studio wykryje nowe rozszerzenie, które spowalnia ładowanie rozwiązania lub uruchamiania. Po wykryciu spowalniają działanie, użytkownicy będą widzieć powiadomień w środowisku IDE, wskazując je do nowego okna dialogowego "Zarządzanie wydajnością programu Visual Studio". Menu Pomoc, aby przejść do wcześniej wykrytych rozszerzenia również są zawsze możliwy to okno dialogowe.

![Zarządzanie wydajnością programu Visual Studio](media/manage-performance.png)

Ten dokument ma na celu pomoc deweloperom rozszerzenie poprzez opisanie, jak jest obliczana wpływ rozszerzenia. W tym dokumencie opisano również, jak wpływ rozszerzenia można analizować lokalnie. Lokalnie analizowanie wpływu rozszerzenia określi, jeśli rozszerzenie może być wyświetlany jako wydajności, wpływ na rozszerzenia.

> [!NOTE]
> Ten dokument koncentruje się na temat wpływu rozszerzeń na rozwiązanie i uruchamiania obciążenia. Rozszerzenia również wpływ na wydajność programu Visual Studio podczas spowodują interfejsu użytkownika przestanie odpowiadać. Aby uzyskać więcej informacji na ten temat, zobacz [jak: Diagnozowanie interfejsu użytkownika powodowanych przez rozszerzenia opóźnienia](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Wpływ uruchamiania rozszerzenia

Jednym z najbardziej typowych sposobów do rozszerzenia, które mają wpływ na wydajność uruchamiania jest wybierając ładowane automatycznie w poszczególnych kontekstach interfejsu użytkownika znanych uruchamiania, takich jak NoSolutionExists lub ShellInitialized. Tych kontekstach interfejsu użytkownika, aktywować podczas uruchamiania. Wszystkie pakiety, które obejmują `ProvideAutoLoad` atrybutu w ich definicji z tych kontekstach zostanie załadowany i zainicjowany w danym momencie.

Gdy firma Microsoft szacować wpływ tych rozszerzeń, przede wszystkim skupimy się na czas spędzony przez te rozszerzenia, które chce automatycznie obciążenia w kontekstach powyżej. Mierzony czas będzie obejmują, ale nie ogranicza się do:

* Ładowanie zestawów rozszerzeń dla pakietów synchroniczne
* Czas w konstruktorze klasy pakietu dla pakietów synchroniczne
* Czas w metodzie zainicjowanie (lub setsite —) pakietu pakietów synchroniczne
* Asynchroniczne pakietów powyżej operacje są uruchamiane w wątku w tle.  Jako takie operacje są wykluczone z monitorowania.
* Czas potrzebny do dowolnego zadanie asynchroniczne planowane podczas inicjowania pakiet do uruchomienia w głównym wątku
* Czas spędzony w procedurze obsługi zdarzeń, specjalnie powłoki zainicjować kontekstu aktywacji lub zmiana stanu zombie powłoki
* Począwszy od programu Visual Studio 2017 Update 3, firma Microsoft będzie również uruchomić monitorowania czas poświęcony w bezczynności połączenia przed powłoki jest zainicjowany. Długie operacji w obsłudze bezczynności również powodować IDE nie odpowiada i przyczynić się do czasu uruchamiania postrzegany przez użytkownika.

Dodaliśmy wiele funkcji, począwszy od programu Visual Studio 2015. Te funkcje ułatwiają z konieczności pakietów ładowane automatycznie. Funkcje Odłóż również potrzebę pakietów do załadowania do bardziej szczegółowych przypadków. Te przypadki obejmują przykłady, których użytkownicy będą bardziej określone za pomocą rozszerzenia lub ograniczenia wpływu rozszerzeń, podczas ładowania automatycznie.

Więcej informacji o tych funkcjach można znaleźć w następujących dokumentach:

[Konteksty interfejsu użytkownika opartego na regułach](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): Bardziej rozbudowane aparat oparty na regułach zbudowane wokół kontekstów interfejsu użytkownika umożliwia tworzenie kontekstów niestandardowego na podstawie typów projektów, odmian i atrybuty. Konteksty niestandardowego może służyć do ładowania pakietu podczas bardziej specyficznych scenariuszy. Określone scenariusze obejmują obecności projekt z konkretną funkcją, zamiast uruchamiania. Konteksty niestandardowych również zezwolić [polecenia widoczność ograniczeni do kontekstowego](visibilityconstraints-element.md) na podstawie składników projektów lub innych dostępnych warunków. Ta funkcja eliminuje potrzebę załadowanie pakietu, aby zarejestrować procedurę obsługi poleceń stan zapytania.

[Obsługa asynchronicznego pakietu](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Nowe klasy bazowej AsyncPackage w programie Visual Studio 2015 umożliwia pakietów programu Visual Studio mają zostać załadowane w tle asynchronicznie jeśli ładowanie pakiet żądanej atrybutu obciążenia automatycznie lub zapytania asynchroniczne usługi. To ładowanie tła umożliwia IDE na bieżąco dynamiczny. Środowisko IDE jest elastyczny, nawet wtedy, gdy rozszerzenie zostanie zainicjowana w tle i nie ma wpływu na scenariuszy o kluczowym znaczeniu, takie jak uruchamianie i rozwiązanie obciążenia.

[Asynchronicznych usług](how-to-provide-an-asynchronous-visual-studio-service.md): Dzięki obsłudze asynchronicznego pakietu dodaliśmy są również obsługę zapytań usług asynchronicznie i możliwość rejestrowania asynchronicznych usług. Co ważniejsze pracujemy nad konwertowanie podstawowych usług Visual Studio do obsługi asynchronicznej kwerendy, tak aby większość pracy w zapytaniu async odbywa się w wątków w tle. SComponentModel (Visual Studio MEF host) jest jednym z głównych usług, które obsługuje teraz zapytania asynchronicznego umożliwia rozszerzeń do obsługi asynchroniczne ładowanie całkowicie.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Zmniejszenie wpływu automatycznie załadować rozszerzeń

Jeśli pakiet jest nadal wymagana automatycznie ładowane podczas uruchamiania, jest ważne, aby zminimalizować prace wykonane podczas inicjowania pakietu. Minimalizacja pracy inicjowania pakietu zmniejsza ryzyko wystąpienia rozszerzenia wpływ na uruchamianie.

Kilka przykładów, które może spowodować, że pakiet inicjowania są kosztowne są:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Użyj pakietu synchroniczne obciążenia zamiast obciążenia asynchronicznego pakietu

Ponieważ synchroniczne pakiety są ładowane w wątku głównym, domyślnie, firma Microsoft zachęca właścicieli rozszerzenia, których ma automatycznie załadować pakietów do użycia zamiast tego, jak wspomniano wcześniej klasy bazowej asynchronicznego pakietu. Zmiana automatycznie załadować pakiet programu obsługuje asynchroniczne ładowanie również ułatwi rozwiązać poniższe problemy.

### <a name="synchronous-filenetwork-io-requests"></a>Żądania We/Wy pliku synchroniczne/sieć

W idealnym każdego synchroniczne żądania We/Wy pliku lub sieci należy unikać w wątku głównym. Ich wpływ będzie zależeć od stan komputera i może zablokować przez długi czas, w niektórych przypadkach.

Za pomocą pakietu asynchroniczne ładowanie i asynchronicznych operacji We/Wy interfejsów API upewnij się, że Inicjalizacja tego pakietu nie blokuje wątek główny w takich przypadkach. Użytkownicy mogą również nadal wchodzić w interakcje z programem Visual Studio, podczas gdy żądań We/Wy odbywa się w tle.

### <a name="early-initialization-of-services-components"></a>Wczesne inicjowania usług i składników

Jednym z typowych wzorców podczas inicjowania pakietu jest zainicjować usług używanych przez lub udostępniane przez ten pakiet w pakiecie `constructor` lub `initialize` metody. Dzięki temu usługi są gotowe do użycia, jego można również dodać niepotrzebnych kosztów pakietów ładowania tych usług nie są używane bezpośrednio. Zamiast tego tych usług powinna zostać zainicjowana na żądanie, aby zminimalizować prace wykonane w pakiet inicjowania.

W przypadku usług globalnych dostarczonej przez pakiet, można użyć `AddService` metod, dla których funkcja opóźnieniem zainicjować usługi tylko wtedy, gdy jest on wymagany przez składnik. Obejmujący usługi używane w pakiecie, można użyć leniwy<T> lub AsyncLazy<T> aby upewnić się, że usługi są inicjowane/badane przy pierwszym użyciu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Mierzenie wpływu automatycznie załadować rozszerzeń przy użyciu dziennika aktywności

Począwszy od programu Visual Studio 2017 Update 3, dziennika aktywności w programie Visual Studio będzie zawierają teraz wpisy dla pakietów wpływ na wydajność podczas uruchamiania i rozwiązanie ładowania. Aby można było wyświetlić te pomiary, musisz uruchomić program Visual Studio z przełącznikiem/log, a następnie otwórz *plik ActivityLog.xml* pliku.

W dzienniku aktywności wpisy będzie wymieniony w obszarze "Zarządzanie wydajnością programu Visual Studio" źródła i będzie wyglądać następująco:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Ten przykład pokazuje, że pakiet o identyfikatorze GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" poświęcony 2008 ms w przypadku uruchamiania programu Visual Studio. Należy pamiętać, że Visual Studio uwzględnia koszt najwyższego poziomu jako podstawowy numer, podczas obliczania wpływ pakietu, ponieważ byłoby się, że użytkownicy oszczędności widzą podczas ich wyłączyć rozszerzenie dla tego pakietu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mierzenie wpływu automatycznie załadować rozszerzeń przy użyciu narzędzia PerfView

Podczas analizy kodu może być pomocny w zidentyfikowaniu ścieżki kodu, które może spowolnić inicjowania pakiet, możesz użyć śledzenia przy użyciu aplikacji, takich jak narzędzia PerfView, aby zrozumieć wpływ obciążenia pakietu w uruchamiania programu Visual Studio.

Narzędzia PerfView jest narzędziem do śledzenia całego systemu. To narzędzie pomoże zrozumienia działania ścieżek krytycznych w aplikacji z powodu użycia procesora CPU lub blokuje wywołania systemowe. Poniżej przedstawiono prosty przykład na analizowaniu Przykładowe rozszerzenie za pomocą narzędzia PerfView dostępne pod adresem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Przykładowy kod:**

Ten przykład jest oparty na przykład niektóre typowe przyczyny opóźnienie zamierzone, Zapisz poniżej kodu, który został zaprojektowany do wyświetlenia:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Rejestrowanie śledzenia za pomocą narzędzia PerfView:**

Po skonfigurowaniu środowiska programu Visual Studio za pomocą rozszerzenia zainstalowane można zarejestrować śledzenia uruchamiania, otwierając narzędzia PerfView i otwierania **zbieranie** okna dialogowego **zbieranie** menu.

![zbieranie menu Narzędzia perfview](media/perfview-collect-menu.png)

Domyślne opcje zapewni stosy wywołań do użycia procesora CPU, ale ponieważ jesteśmy zainteresowani także czasu blokowania, należy również włączyć **czasu wątku** stosów. Gdy gotowe ustawienia możesz kliknąć **Rozpocznij zbieranie** i uruchom program Visual Studio po uruchomieniu rejestrowania.

Przed zatrzymaniem zbierania należy upewnić się, program Visual Studio jest w pełni zainicjowany, okno główne jest całkowicie widoczna i jeśli rozszerzenie zawiera wszystkie elementy interfejsu użytkownika, które automatycznie pokazują, również są widoczne. Po całkowitym załadowaniu programu Visual Studio i rozszerzenia jest inicjowany, można zatrzymać rejestrowania można analizować śledzenia.

**Analizowanie danych śledzenia przy użyciu narzędzia PerfView:**

Po zakończeniu nagrywania narzędzia PerfView automatycznie otworzyć śledzenia i opcje $expand.

Na potrzeby tego przykładu, jesteśmy szczególnie zainteresowani **wątku stosów czasu** widoku, który można znaleźć w obszarze **grupę zaawansowane**. Widok ten wyświetli łączny czas spędzony na wątku za pomocą metody, w tym czas procesora CPU i czas blokowania, takich jak We/Wy dysku lub Oczekiwanie na uchwyty.

 ![stosy czasu wątków](media/perfview-thread-time-stacks.png)

 Podczas otwierania **wątku stosów czasu** wyświetlić, należy wybrać **devenv** procesu można rozpocząć analizy.

Narzędzia PerfView zawiera szczegółowe wskazówki dotyczące sposobu odczytywania wątku stosów czasu w ramach własnej menu Pomoc, aby uzyskać bardziej szczegółową analizę. Do celów tego przykładu chcemy filtrować dalsze ten widok, tylko tym stosów z wątkiem naszych pakietów w module nazwy i uruchamiania.

1. Ustaw **GroupPats** na pusty tekst, aby usunąć wszelkie grupowanie dodawany domyślnie.
2. Ustaw **IncPats** obejmujący część nazwy zestawu i uruchamiania wątku oprócz istniejącego filtru procesu. W tym przypadku powinien być **devenv; Uruchamianie wątku; MakeVsSlowExtension**.

Teraz w widoku będzie wyświetlana tylko koszt, który jest skojarzony z zestawów powiązanych do rozszerzenia. W tym widoku, ilekroć się na liście **Inc (całkowity koszt)** kolumny uruchamiania wątku jest powiązany z naszego rozszerzenia filtrowane i będzie mieć wpływ na uruchamianie.

W przykładzie powyżej niektóre ciekawe wywołania będą stosów:

1. We/Wy przy użyciu `System.IO` klasy: Całkowity koszt te klatki nie może być zbyt drogie w śledzeniu, są potencjalną przyczyną problemu, ponieważ szybkość operacji We/Wy pliku będą się różnić od maszyny.

   ![system We/Wy ramki](media/perfview-system-io-frames.png)

2. Blokowanie oczekiwanie na inne zadanie asynchroniczne wywołania: W tym przypadku całkowity czas reprezentuje czas, w których główny wątek jest zablokowany na ukończenie zadań asynchronicznych.

   ![blokowanie ramek wywołania](media/perfview-blocking-call-frames.png)

Jedną z innymi widokami w śledzenia, które mogą być przydatne do określenia wpływu będzie **stosy ładowania obrazów**. Można zastosować tych samych filtrów, jakie mają zastosowanie do **wątku stosów czasu** służy do wyświetlania i Dowiedz się, wszystkie zestawy, ładowane z powodu kod wykonywany przez pakiet załadowane automatycznie.

Jest ważne, aby zminimalizować liczbę załadowanych zestawów wewnątrz procedury inicjowania pakietu, zgodnie z każdego dodatkowego zestawu pociąga za sobą we/wy dodatkowy dysk, który może spowolnić uruchamiania znacznie na maszynach wolniej.

## <a name="summary"></a>Podsumowanie

Uruchamianie programu Visual Studio został jednego z obszarów, które firma Microsoft stale uzyskiwanie opinii na temat. Naszym celem, jak wspomniano wcześniej, jest dla wszystkich użytkowników do uruchomienia spójne środowisko niezależnie od tego, czy składniki i rozszerzeń, które na nich zainstalować. Prosimy o poświęcenie do pracy z właścicielami rozszerzenia, aby pomóc im pomóc nam osiągnąć ten cel. Wskazówki dotyczące powyższych powinny być pomocne w zrozumienie wpływu rozszerzeń na uruchamianie i albo uniknięcie konieczności auto obciążenia lub załadować je asynchronicznie, aby zminimalizować wpływ na wydajność pracy użytkownika.
