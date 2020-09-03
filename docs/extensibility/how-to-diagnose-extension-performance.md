---
title: 'Instrukcje: diagnozowanie wydajności rozszerzeń | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905909"
---
# <a name="measuring-extension-impact-in-startup"></a>Pomiar wpływu rozszerzenia w trakcie uruchamiania

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Skupienie się na wydajności rozszerzeń w programie Visual Studio 2017

W oparciu o opinie klientów jeden z obszarów koncentracji dla wersji programu Visual Studio 2017 został rozruchowy i ma wydajność ładowania rozwiązań. Jako zespół platformy Visual Studio pracujemy nad ulepszeniem wydajności uruchamiania i ładowania rozwiązań. Ogólnie rzecz biorąc, nasze Pomiary sugerują rozszerzenia zainstalowane mogą również mieć znaczny wpływ na te scenariusze.

Aby pomóc użytkownikom zrozumieć ten wpływ, dodaliśmy nową funkcję w programie Visual Studio w celu powiadomienia użytkowników o wolnych rozszerzeniach. Czasami program Visual Studio wykrywa nowe rozszerzenie, które spowalnia ładowanie lub uruchamianie rozwiązań. Gdy zostanie wykryte spowolnienie, użytkownicy zobaczą powiadomienie w środowisku IDE wskazującym nowe okno dialogowe "Zarządzanie wydajnością programu Visual Studio". To okno dialogowe może być również zawsze dostępne w menu Pomoc, aby przeglądać poprzednio wykryte rozszerzenia.

![Zarządzanie wydajnością programu Visual Studio](media/manage-performance.png)

Ten dokument ma na celu ułatwienie deweloperom rozszerzeń przez opisywanie sposobu, w jaki jest obliczany wpływ na rozszerzenie. W tym dokumencie opisano również sposób, w jaki wpływ rozszerzenia może być analizowany lokalnie. Lokalne analizowanie wpływu rozszerzenia określi, czy rozszerzenie może być widoczne jako rozszerzenie wpływające na wydajność.

> [!NOTE]
> Ten dokument koncentruje się na wpływie rozszerzeń podczas uruchamiania i ładowania rozwiązań. Rozszerzenia wpływają również na wydajność programu Visual Studio, gdy powodują, że interfejs użytkownika przestanie odpowiadać. Aby uzyskać więcej informacji na ten temat, zobacz [How to: diagnozowanie opóźnień interfejsu użytkownika spowodowanych przez rozszerzenia](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Jak rozszerzenia mogą mieć wpływ na uruchamianie

Jednym z najczęstszych sposobów przedłużania wydajności uruchamiania jest wybranie opcji automatyczne ładowanie jednego z znanych kontekstów interfejsu użytkownika, takich jak NoSolutionExists lub ShellInitialized. Te konteksty interfejsu użytkownika są aktywowane podczas uruchamiania. Wszystkie pakiety, które zawierają `ProvideAutoLoad` atrybut w ich definicji z tymi kontekstami, zostaną załadowane i zainicjowane w tym czasie.

Gdy mierzy wpływ rozszerzenia, firma Microsoft koncentruje się głównie na czasie spędzonym przez te rozszerzenia, które mają być ładowane w powyższych kontekstach. Mierzone czasy powinny obejmować, ale nie być ograniczone do:

* Ładowanie zestawów rozszerzeń dla pakietów synchronicznych
* Czas spędzony w konstruktorze klasy pakietu dla pakietów synchronicznych
* Czas poświęcony na zainicjowanie pakietu (lub SetSite) dla pakietów synchronicznych
* W przypadku pakietów asynchronicznych powyższe operacje są uruchamiane w wątku w tle.  W związku z tym operacje są wykluczone z monitorowania.
* Czas spędzony na wszystkich asynchronicznych zadaniach zaplanowanych podczas inicjowania pakietu do uruchomienia w wątku głównym
* Czas spędzony na obsłudze zdarzeń, w tym w ramach aktywacji kontekstu zainicjowanej przez powłokę lub zmiany stanu stanie zombie powłoki
* Począwszy od programu Visual Studio 2017 Update 3, rozpocznie się również monitorowanie czasu oczekiwania na wywołania bezczynne przed zainicjowaniem powłoki. Długotrwałe operacje w obsłudze bezczynności powodują również nieodpowiadające im środowisko IDE i przyczyniają się do postrzegania czasu uruchamiania przez użytkownika.

Dodaliśmy wiele funkcji, zaczynając od programu Visual Studio 2015. Te funkcje ułatwiają usunięcie potrzebnych pakietów do autoładowania. Funkcje te również opóźnią konieczność ładowania pakietów do bardziej szczegółowych przypadków. Te przypadki zawierają przykłady, w których użytkownicy byłyby bardziej konkretnym zastosowaniem rozszerzenia lub zmniejszyć wpływ rozszerzenia podczas automatycznego ładowania.

Więcej informacji o tych funkcjach można znaleźć w następujących dokumentach:

[Konteksty interfejsu użytkownika oparte na regułach](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): bogatszy aparat oparty na regułach, który umożliwia tworzenie kontekstów niestandardowych na podstawie typów projektu, jego wersji i atrybutów. Kontekstów niestandardowych można użyć do załadowania pakietu w określonych scenariuszach. Te konkretne scenariusze obejmują obecność projektu z określoną możliwością zamiast uruchamiania. Niestandardowe konteksty umożliwiają również [widoczność poleceń, które mają być powiązane z kontekstem niestandardowym](visibilityconstraints-element.md) na podstawie składników projektu lub innych dostępnych warunków. Ta funkcja eliminuje konieczność załadowania pakietu w celu zarejestrowania programu obsługi zapytań stanu polecenia.

[Obsługa pakietów asynchronicznych](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Nowa klasa bazowa AsyncPackage w programie Visual Studio 2015 zezwala na ładowanie pakietów programu Visual Studio w tle asynchronicznie, jeśli zażądano obciążenia pakietu przez atrybut autoload lub asynchronicznej kwerendy usługi. To ładowanie w tle umożliwia reagowanie środowiska IDE. IDE reaguje nawet w trakcie inicjowania rozszerzenia w tle i krytycznych scenariuszy, takich jak uruchamianie i ładowanie rozwiązań nie ma wpływu na to.

[Usługi asynchroniczne](how-to-provide-an-asynchronous-visual-studio-service.md): z obsługą pakietów asynchronicznych Dodaliśmy również obsługę zapytań usług asynchronicznych i możliwość rejestrowania usług asynchronicznych. Dokładniej pracujemy nad konwertowaniem podstawowych usług Visual Studio, aby obsługiwały asynchroniczne zapytania, dzięki czemu większość pracy w zapytaniach asynchronicznych występuje w wątkach w tle. SComponentModel (host programu Visual Studio MEF) to jedna z głównych usług, która obsługuje teraz asynchroniczne zapytania, aby rozszerzenia obsługiwały asynchroniczne ładowanie w całości.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Ograniczanie wpływu rozszerzeń ładowanych przez funkcję

Jeśli pakiet nadal musi być automatycznie ładowany podczas uruchamiania, ważne jest, aby zminimalizować nakład pracy wykonywany podczas inicjowania pakietu. Minimalizacja działania inicjowania pakietu zmniejsza szansę uruchomienia rozszerzenia.

Niektóre przykłady, które mogą spowodować, że inicjowanie pakietu jest kosztowne:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Użycie synchronicznego ładowania pakietów zamiast asynchronicznego ładowania pakietów

Ponieważ pakiety synchroniczne są domyślnie ładowane w wątku głównym, zachęcamy właścicieli rozszerzeń, którzy mają ładowane pakiety, aby korzystały z klasy bazowej pakietu asynchronicznego zamiast tego wcześniej. Zmiana automatycznie załadowanego pakietu, aby obsługiwał asynchroniczne ładowanie, ułatwi również rozwiązanie innych problemów poniżej.

### <a name="synchronous-filenetwork-io-requests"></a>Synchroniczne żądania we/wy pliku/sieci

Najlepszym rozwiązaniem jest unikanie dowolnego synchronicznego żądania we/wy pliku lub sieci w wątku głównym. Ich wpływ będzie zależeć od stanu komputera i może być blokowany przez długie okresy w niektórych przypadkach.

Przy użyciu asynchronicznego ładowania pakietów i asynchronicznych interfejsów API we/wy należy upewnić się, że inicjalizacja pakietu nie blokuje wątku głównego w takich przypadkach. Użytkownicy mogą również nadal korzystać z programu Visual Studio, podczas gdy żądania we/wy są wykonywane w tle.

### <a name="early-initialization-of-services-components"></a>Wczesne inicjowanie usług, składników

Jednym z typowych wzorców w inicjalizacji pakietu jest zainicjowanie usług używanych przez lub dostarczonych przez ten pakiet w pakiecie `constructor` lub `initialize` metodzie. Dzięki temu usługi są gotowe do użycia, ale można również dodać niepotrzebne koszty do ładowania pakietów, jeśli te usługi nie są używane natychmiast. Zamiast tego usługi powinny być inicjowane na żądanie w celu zminimalizowania pracy wykonywanej w ramach inicjalizacji pakietu.

W przypadku usług globalnych udostępnianych przez pakiet można użyć `AddService` metod, które przyjmują funkcję, aby opóźnieniem zainicjować usługę tylko wtedy, gdy jest wymagana przez składnik. W przypadku usług używanych w pakiecie można użyć polecenie z opóźnieniem \<T> lub AsyncLazy, \<T> Aby upewnić się, że usługi są inicjowane/wykonywane z użyciem zapytania przy pierwszym użyciu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Mierzenie wpływu autoładowanych rozszerzeń przy użyciu dziennika aktywności

Począwszy od programu Visual Studio 2017 Update 3, dziennik aktywności programu Visual Studio będzie teraz zawierał wpisy dotyczące wydajności pakietów podczas uruchamiania i ładowania rozwiązania. Aby wyświetlić te pomiary, należy otworzyć program Visual Studio z przełącznikiem/log i otworzyć plik *ActivityLog.xml* .

W dzienniku aktywności wpisy będą znajdować się w obszarze "Zarządzanie wydajnością programu Visual Studio" i będzie wyglądać podobnie do poniższego przykładu:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Ten przykład pokazuje, że pakiet o identyfikatorze GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" spędził 2008 MS podczas uruchamiania programu Visual Studio. Należy pamiętać, że program Visual Studio traktuje koszt najwyższego poziomu jako numer podstawowy podczas obliczania wpływu pakietu, który byłby widoczny dla użytkowników oszczędności po wyłączeniu rozszerzenia dla tego pakietu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Mierzenie wpływu autoładowanych rozszerzeń przy użyciu narzędzia PerfView

Chociaż Analiza kodu może pomóc identyfikować ścieżki kodu, które mogą spowalniać inicjalizację pakietu, można również użyć śledzenia przy użyciu aplikacji, takich jak narzędzia PerfView, aby zrozumieć wpływ ładowania pakietów w programie Visual Studio.

Narzędzia PerfView to narzędzie do śledzenia całego systemu. To narzędzie pomoże zrozumieć aktywne ścieżki w aplikacji z powodu użycia procesora CPU lub blokowania wywołań systemowych. Poniżej znajduje się krótki przykład analizowania przykładowego rozszerzenia za pomocą narzędzia PerfView dostępnego w [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Przykładowy kod:**

Ten przykład jest oparty na poniższym przykładowym kodzie, który jest przeznaczony do wyświetlania niektórych typowych przyczyn opóźnienia:

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

**Rejestrowanie śledzenia przy użyciu narzędzia PerfView:**

Po skonfigurowaniu środowiska programu Visual Studio z zainstalowanym rozszerzeniem można zarejestrować śledzenie uruchamiania, otwierając Narzędzia PerfView i otwierając okno dialogowe **zbierania** z menu **zbieranie** .

![menu zbierające narzędzia PerfView](media/perfview-collect-menu.png)

Opcje domyślne udostępniają stosy wywołań dla użycia procesora CPU, ale ponieważ chcemy również mieć czas blokowania, należy również włączyć stosy **czasu wątków** . Gdy ustawienia są gotowe, możesz kliknąć pozycję **Rozpocznij zbieranie** , a następnie otworzyć program Visual Studio po rozpoczęciu rejestrowania.

Przed zatrzymaniem kolekcjonowania chcesz upewnić się, że program Visual Studio jest w pełni zainicjowany, okno główne jest całkowicie widoczne i jeśli rozszerzenie zawiera elementy interfejsu użytkownika, które są automatycznie wyświetlane, są one również widoczne. Po całkowitym załadowaniu programu Visual Studio i zainicjowaniu rozszerzenia można zatrzymać nagrywanie, aby analizować śledzenie.

**Analizowanie śledzenia za pomocą narzędzia PerfView:**

Po zakończeniu nagrywania narzędzia PerfView automatycznie otworzy opcje śledzenia i rozwijania.

Na potrzeby tego przykładu głównie interesuje się widok **stosy czasu wątku** , który można znaleźć w obszarze **Grupa zaawansowana**. Ten widok pokazuje łączny czas spędzony na wątku przez metodę, w tym czas procesora CPU i czas blokowania, takie jak dysk operacji we/wy lub oczekiwanie na dojścia.

 ![stosy czasu wątku](media/perfview-thread-time-stacks.png)

 Podczas otwierania widoku **stosów czasu wątku** należy wybrać proces **devenv** , aby rozpocząć analizę.

Narzędzia PerfView zawiera szczegółowe wskazówki dotyczące odczytywania stosów czasu wątków w ramach własnego menu Pomoc w celu uzyskania bardziej szczegółowej analizy. Na potrzeby tego przykładu chcemy odfiltrować ten widok tylko w przypadku, gdy stosy mają nazwę modułu pakietów, i wątek startowy.

1. Ustaw **GroupPats** na pusty tekst, aby usunąć wszystkie grupowanie dodane domyślnie.
2. Ustaw **IncPats** do uwzględnienia części nazwy zestawu i wątku uruchomieniowego oprócz istniejącego filtru procesów. W takim przypadku powinna być **devenv; Wątek startowy; MakeVsSlowExtension**.

Teraz widok będzie zawierać tylko koszt skojarzony z zestawami związanymi z rozszerzeniem. W tym widoku dowolny czas wymieniony w kolumnie **Inc (włącznie)** wątku startowego jest powiązany z naszym filtrowanym rozszerzeniem i ma wpływ na uruchamianie.

Na przykład powyżej niektórych interesujących stosów wywołań byłyby:

1. We/wy przy użyciu `System.IO` klasy: choć koszt włącznie z tymi ramkami może nie być zbyt kosztowny w śledzeniu, są one potencjalną przyczyną problemu, ponieważ szybkość operacji we/wy pliku zależy od maszyny do komputera.

   ![ramki we/wy systemu](media/perfview-system-io-frames.png)

2. Blokowanie wywołań czekających na inne asynchroniczne operacje: w tym przypadku czas włączny reprezentuje czas, przez który główny wątek jest blokowany po zakończeniu pracy asynchronicznej.

   ![Blokowanie ramek wywołań](media/perfview-blocking-call-frames.png)

Jednym z innych widoków śledzenia, które będą przydatne do określenia wpływu, będzie **stosy ładowania obrazu**. Można zastosować te same filtry, które zostały zastosowane w odniesieniu do **stosów czasu wątku** , i sprawdzić wszystkie zestawy ładowane ze względu na kod wykonywany przez pakiet, który został załadowany.

Ważne jest, aby zminimalizować liczbę załadowanych zestawów wewnątrz procedury inicjowania pakietu, ponieważ każdy dodatkowy zestaw będzie obejmował dodatkowe we/wy dysku, co może znacznie spowolnić uruchamianie na wolniejszych komputerach.

## <a name="summary"></a>Podsumowanie

Uruchomienie programu Visual Studio było jednym z obszarów, w których ciągle otrzymujesz opinię. Nasze cele podane wcześniej są przeznaczone dla wszystkich użytkowników, którzy mają spójne środowisko uruchamiania niezależnie od składników i rozszerzeń, które zostały zainstalowane. Chcemy współpracować z właścicielami rozszerzeń, aby pomóc im w osiągnięciu tego celu. Powyższe wskazówki powinny być przydatne w zrozumieniu rozszerzeń wpływających na uruchomienie i unikając konieczności samoładowania lub załadowania go asynchronicznie w celu zminimalizowania wpływu na wydajność użytkowników.
