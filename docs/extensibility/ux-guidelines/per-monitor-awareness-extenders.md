---
title: Rozpoznawanie — monitorowanie, obsługę rozszerzeń programu Visual Studio
titleSuffix: ''
description: Zapoznaj się z nową obsługę rozszerzeń na monitor rozpoznawanie dostępne w programie Visual Studio 2019 r.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: db30c3d74a7742daa3c9cf7225bc2a38062dc6e4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660700"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Rozpoznawanie — monitorowanie, obsługę rozszerzeń programu Visual Studio
Wersje przed Visual Studio 2019 r było ich kontekstami świadomości DPI równa świadomi, a nie wartość DPI aware (PMA) monitor systemu. Działające w systemie świadomości spowodowało wizualizację pogorszenie środowiska (np. rozmyty czcionki lub ikony) zawsze wtedy, gdy program Visual Studio było renderowanie na monitorach z różne skale lub zdalnego do maszyn za pomocą innego ekranu konfiguracji np. (inny Windows skalowanie).

Kontekst świadomości DPI programu Visual Studio 2019 r ustawiono jako PMA, gdy środowisko obsługuje tę funkcję, umożliwiając renderowania w zależności od konfiguracji wyświetlania, w którym jest hostowany program Visual Studio, a nie pojedynczego systemu zdefiniowanej konfiguracji. Ostatecznie tłumaczenie na zawsze rzeczowy interfejsu użytkownika dla obszarów, które obsługują tryb PMA.

Zapoznaj się [wysokiej rozdzielczości DPI aplikacji programowanie aplikacji klasycznych na Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) dokumentacji, aby uzyskać więcej informacji o warunkach i ogólnego scenariusza omówione w tym dokumencie.

## <a name="quickstart"></a>Szybki start
- Upewnij się, program Visual Studio jest uruchomiony w trybie PMA (zobacz **Włączanie PMA**)

- Zweryfikuj swoje działania rozszerzenia poprawnie zestawu typowych scenariuszy (zobacz **testowanie rozszerzenia problemów PMA**)

- Jeśli znajdziesz problemy, można użyć strategii zalecenia omówionych w tym dokumencie, aby zdiagnozować i rozwiązać te problemy. Należy także dodać nowe [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) pakiet NuGet do projektu, dostęp do wymaganych interfejsów API.

## <a name="enabling-pma"></a>Włączanie PMA
Aby włączyć PMA w programie Visual Studio, muszą zostać spełnione następujące wymagania:
1)  Windows 10 kwietnia 2018 r. aktualizacji (v1803 RS4) lub nowszy
2)  .NET framework 4.8 RTM lub nowszej
3)  Visual Studio 2019 r przy użyciu ["Optymalizuj renderowania na ekranach o różnych pikseli gęstości"](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) po włączeniu opcji

Po spełnieniu tych wymagań programu Visual Studio spowoduje automatyczne włączenie trybu PMA całym procesie.

> [!NOTE]
> Zawartość Windows Forms w programie VS (na przykład w przeglądarce właściwości) będzie obsługiwać PMA tylko wtedy, gdy program Visual Studio 2019 aktualizacji nr 1.

## <a name="testing-your-extensions-for-pma-issues"></a>Testowanie rozszerzeń PMA problemów

Program Visual Studio obsługuje oficjalnie struktur WPF, Windows Forms, Win32 i interfejsu użytkownika HTML/JS. Gdy program Visual Studio zostanie przełączone do trybu PMA, każdy stos interfejsu użytkownika, zachowuje się inaczej. W związku z tym niezależnie od tego, w ramach interfejsu użytkownika, zalecane jest, że przebieg testu jest przeprowadzana w celu upewnij się, że wszystkie interfejsu użytkownika jest zgodna z trybem PMA.

Zalecamy zweryfikowanie następujących typowych scenariuszach:

1. Zmiana współczynnik skali środowiska pojedynczy monitor, gdy aplikacja jest uruchomiona *
    - W tym scenariuszu ułatwia testowanie, czy interfejs użytkownika odpowiada na żądania dynamiczna zmiana rozdzielczości DPI Windows

2. Dokowanie/dokowania komputera przenośnego, gdzie dołączonych monitor jest skonfigurowany do podstawowej i dołączonych monitor został współczynnik skali innego niż komputera przenośnego, gdy aplikacja jest uruchomiona.
    - W tym scenariuszu ułatwia testowanie, czy interfejs użytkownika odpowiada na żądania wyświetlanie, zmiana rozdzielczości, a także obsługa dynamicznie Wyświetla dodawany lub usuwany

3. Istnienie wielu monitorów z różne skale i przenoszenie aplikacji między nimi.
    - W tym scenariuszu ułatwia testowanie, czy interfejs użytkownika odpowiada na żądania zmiany rozdzielczości ekranu
    
4. Remoting do komputera, gdy maszyn lokalnych i zdalnych ma różne skale podstawowego monitora.
    - W tym scenariuszu ułatwia testowanie, czy interfejs użytkownika odpowiada na żądania dynamiczna zmiana rozdzielczości DPI Windows

Dobry test wstępny dla tego, czy interfejs użytkownika może mieć problemy to, czy kod korzysta z usługi *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper*, *Microsoft.VisualStudio.PlatformUI.DpiHelper*, lub *VsUI::CDpiHelper* klasy. Te stare klasy DpiHelper obsługują tylko rozpoznawanie DPI systemu i zawsze nie będzie działać prawidłowo, jeśli proces jest PMA.

Typowe użycie tych DpiHelpers będzie wyglądać następująco:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

W poprzednim przykładzie prostokąt reprezentujący logiczne granice okna jest konwertowana na jednostki urządzenia tak, aby go mogą być przekazywane do metody natywnej MonitorFromPoint, która oczekuje współrzędnych urządzenia w celu zwróci wskaźnik dokładne monitorowanie.

### <a name="classes-of-issues"></a>Klasy problemów
Po włączeniu trybu PMA dla programu Visual Studio interfejsu użytkownika można replikować problemy na kilka typowych sposobów. Większość, jeśli nie wszystkie z tych problemów może się zdarzyć w jednym z obsługiwanych platform interfejsu użytkownika programu Visual Studio. Ponadto te problemy również zdarzyć, gdy element interfejsu użytkownika znajduje się on w trybie mieszanym DPI skalowanie scenariuszy (zobacz Windows [dokumentacji](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Aby dowiedzieć się więcej). 

#### <a name="win32-window-creation"></a>Tworzenie okien Win32
Podczas tworzenia systemu windows przy użyciu CreateWindow() lub CreateWindowEx(), Wspólny wzorzec jest utworzenie okna na współrzędnych (0,0) (górnego/lewego rogu ekranu głównego), przenieś go do ostatecznego miejsca. Jednak w ten sposób może spowodować, że okna, aby wyzwolić DPI zmienić wiadomości lub zdarzenie, które można także ponownie wyzwolić inne komunikaty interfejsu użytkownika lub zdarzenia, a ostatecznie spowodować niepożądane zachowanie lub renderowania.

#### <a name="wpf-element-placement"></a>Położenie elementu WPF
Podczas przenoszenia elementów WPF za pomocą starego Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, współrzędne w lewym górnym rogu może nie można obliczyć poprawnie zawsze wtedy, gdy elementy znajdują się na DPI innych niż podstawowe.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializacja rozmiarów elementu interfejsu użytkownika lub położenia
Po przywróceniu interfejsu użytkownika rozmiaru lub położenia (jeśli są zapisywane jako jednostki urządzenia) w innym kontekście DPI niż co był przechowywany w, zostanie umieszczony i wielkości niepoprawnie. Dzieje się tak, ponieważ jednostki urządzenia mają relację z używaniem DPI.

#### <a name="incorrect-scaling"></a>Niepoprawne skalowania
Elementy interfejsu użytkownika tworzone na podstawowym DPI skalują się poprawnie, jednak po przeniesieniu do wyświetlania przy użyciu różnych wartości DPI, nie ponowne skalowanie, a w związku z tym, jego zawartość kończy się on za duży lub za mały.

#### <a name="incorrect-bounding"></a>Niepoprawne obwiedni
Podobnie do skalowania problemu elementy interfejsu użytkownika obliczy ich granice prawidłowo w swoim kontekście z podstawowego DPI, jednak po przeniesieniu do DPI innego niż podstawowy, ich nie będzie obliczania nowych granic poprawnie. W efekcie okna zawartości kończy się zbyt małej lub zbyt duży w porównaniu do hostowania interfejsu użytkownika, co skutkuje pustego miejsca lub wycinka.

#### <a name="drag--drop"></a>Przeciąganie i upuszczanie
Zawsze, gdy w scenariuszach DPI trybu mieszanego (np. różne elementy interfejsu użytkownika renderowania w różnych trybach świadomości DPI), przeciągnij i upuść współrzędne może być miscalculated, co w położeniu końcowym listy znajdą się nieprawidłowe.

#### <a name="out-of-process-ui"></a>Interfejs użytkownika spoza procesu
Niektóre interfejsu użytkownika zostanie utworzony poza procesem i w przypadku tworzenia proces zewnętrzny w trybie świadomości DPI innego niż program Visual Studio, może prowadzić do dowolnego z poprzednich problemy z renderowaniem.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Kontrolek formularzy Windows Forms, obrazów lub niepoprawnie renderowany układów
Nie wszystkie treści Windows Forms obsługują tryb PMA. W rezultacie mogą pojawić się renderowanie problem z układów niepoprawne lub skalowania. Rozwiązania, w tym przypadku jest jawnie renderowanie zawartości Windows Forms w DpiAwarenessContext "System Aware" (dotyczą [wymuszanie formant do określonego DpiAwarenessContext](#forcing-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Kontrolek formularzy Windows Forms lub windows, które nie są wyświetlane
Jedną z głównych przyczyn tego problemu jest próby Zmień obiekt nadrzędny dla formantu lub okno z jednego DpiAwarenessContext do okna z różnych DpiAwarenessContext deweloperów.

Poniższe ilustracje pokazują bieżącą **domyślne** ograniczeń systemu operacyjnego Windows w elementy nadrzędne systemu windows:

![Zrzut ekranu przedstawiający zachowanie poprawny element nadrzędny](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

> [!Note]
> To zachowanie można zmienić, określając zachowanie hostingu wątku (zobacz [DpiHostinBehaviour](https://docs.microsoft.com/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

W rezultacie Jeśli ustawisz relacji nadrzędny podrzędny między trybami nieobsługiwane, zakończy się niepowodzeniem i kontroli lub okna nie może być renderowana zgodnie z oczekiwaniami.

### <a name="diagnosing-issues"></a>Diagnozowanie problemów
Istnieje wiele czynników, które należy wziąć pod uwagę przy identyfikowaniu problemów związanych z PMA: 

1. Czy interfejs użytkownika lub interfejsu API oczekiwać logicznych lub wartości urządzenia.
    - WPF UI i interfejsów API zazwyczaj używają wartości logiczne (ale nie zawsze)
    - Interfejs użytkownika systemu Win32 i interfejsów API zwykle użyć wartości urządzenia

2. Których wartości pochodzą?
    - Jeśli odbieranie wartości z innego interfejsu użytkownika lub interfejsów API, czy jest przekazywanie urządzenia lub wartości logicznych.
    - Jeśli odbieranie wartości z wielu źródeł, wszystkie one Użyj/oczekiwać te same typy wartości lub konwersji, trzeba być mieszane i dopasowywane?

3. Są stałe interfejsu użytkownika w użyciu i jakie są one w?

4. Wątek jest w odpowiednim kontekście DPI dla wartości otrzymuje?
    - Zmiany mieszane hostowania DPI ogólnie należy umieścić w odpowiednim kontekście ścieżki kodu, jednak pracy poza przepływ pętli lub zdarzenie główne komunikatów może być wykonywany w nieprawidłowym kontekście DPI.

5. Czy wartości między granic kontekstowych DPI?
    - Przeciągnięcie i upuszczenie jest typowych sytuacji, w którym współrzędne mogą przechodzić kontekstów DPI. Okno próbuje postępują właściwie, ale w niektórych przypadkach hosta interfejsu użytkownika może być konieczne spełniała konwersji zapewnienie dopasowania granic kontekstowych.

### <a name="pma-nuget-package"></a>Pakiet PMA NuGet
Nowe biblioteki DpiAwarness znajduje się na [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) pakietu NuGet.

### <a name="recommended-tools"></a>Zalecane narzędzia
Następujące narzędzia można debugować problemy związane z PMA na niektóre z różnych stosów interfejsu użytkownika, obsługiwane przez program Visual Studio.

#### <a name="snoop"></a>Snoop
Rozpoznanie jest XAML narzędzie debugowania, który ma dodatkowe funkcje, które nie mają wbudowane narzędzia Visual Studio XAML. Ponadto przed śledzeniem nie trzeba aktywnie debugowania programu Visual Studio, aby można było wyświetlić i dostosować jego WPF UI. Dwa główne sposoby rozpoznanie może być przydatne do diagnozowania problemów PMA jest sprawdzania poprawności współrzędne logiczne umieszczania lub granice rozmiar i sprawdzania poprawności interfejsu użytkownika ma odpowiednie DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Narzędzia Visual Studio, XAML
Podobnie jak przed śledzeniem narzędzia XAML w programie Visual Studio może pomóc w diagnozowaniu problemów PMA. Po znalezieniu prawdopodobnie Przyczyna nadmiernego możesz ustawić punkty przerwania i użyj okna dynamiczne drzewo wizualne, jak również w oknach debugowania, aby sprawdzić granice interfejsu użytkownika i bieżącego DPI.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie rozwiązywania problemów PMA
### <a name="replacing-dpihelper-calls"></a>Zastępowanie DpiHelper wywołania
W większości przypadków Rozwiązywanie problemów z interfejsem użytkownika w trybie PMA wrzała w dół do zastępowania wywołań w kodzie zarządzanym starego *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* i *Microsoft.VisualStudio.PlatformUI.DpiHelper*klasy przy użyciu wywołania do nowego *Microsoft.VisualStudio.Utilities.DpiAwareness* Klasa pomocy. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Dla kodu natywnego, wiąże się zastępowanie wywołania do starego *VsUI::CDpiHelper* klasy przy użyciu wywołania do nowego *VsUI::CDpiAwareness* klasy. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Nowe klasy DpiAwareness i CDpiAwareness oferują tej samej jednostce pomocników konwersji zgodnie z klasy DpiHelper, ale nie wymagają dodatkowego parametru wejściowego: element interfejsu użytkownika do użycia jako odwołanie dla operacji konwersji. Ważne jest, aby należy pamiętać, że pomocników skalowania obrazu nie istnieją w nowych pomocników DpiAwareness/CDpiAwareness i w razie potrzeby [ImageService](https://docs.microsoft.com/visualstudio/extensibility/image-service-and-catalog?view=vs-2019) powinny być używane zamiast tego.

Klasa zarządzana DpiAwareness oferuje pomocników wizualizacji WPF, kontrolek Windows Forms i Win32 parametrów hWnd i HMONITORs (zarówno w formie IntPtrs), podczas natywnych CDpiAwareness oferty HWND i HMONITOR pomocnicy klasy.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Okna dialogowe w formularzach Windows, windows lub kontrolki wyświetlane w niewłaściwej DpiAwarenessContext
Nawet po pomyślnym element nadrzędny systemu windows przy użyciu różnych DpiAwarenessContexts (ze względu na zachowanie domyślne Windows), użytkownicy mogą nadal otrzymywać, skalowanie problemy jako systemu windows przy użyciu różnych skali DpiAwarenessContexts inaczej. W wyniku użytkownicy mogą Zobacz/rozmyty wyrównania tekstu lub obrazów kwestie dotyczące interfejsu użytkownika.

Rozwiązanie to można ustawić poprawny zakres DpiAwarenessContext dla wszystkich okien i formantów w aplikacji.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Okna dialogowe najwyższego poziomu w trybie mieszanym (TLMM)
Tworzenie okien najwyższego poziomu, takie jak modalne okna dialogowe, koniecznie upewnij się, że wątek jest w poprawnym stanie przed okna (i jego uchwyt) tworzona. Wątek można umieścić w świadomości systemu przez przy użyciu Pomocnika CDpiScope w trybie macierzystym, lub pomocnika DpiAwareness.EnterDpiScope w zarządzanych. (TLMM powinien być zazwyczaj używany na innych WPF okna dialogowe/windows).

### <a name="child-level-mixed-mode-clmm"></a>Tryb mieszany poziom podrzędny (CLMM)
Domyślnie okien podrzędnych otrzymują bieżącego wątku DPI świadomości kontekstu Jeśli utworzony bez klasy nadrzędnej lub program nadrzędnego DPI świadomości kontekstu utworzone za pomocą elementu nadrzędnego. Aby utworzyć element podrzędny w innym kontekście świadomości DPI niż jego obiekt nadrzędny, Wątek można umieścić w żądanej kontekstu świadomości DPI. Następnie element podrzędny można tworzyć bez klasy nadrzędnej i ręcznie pokrewnym do okna nadrzędnego.

#### <a name="clmm-issues"></a>Problemy z CLMM
Większość pracy obliczeń interfejsu użytkownika, wykonywanej jako część głównej komunikatów łańcucha pętli lub zdarzeń powinny być uruchomione w odpowiednim kontekście świadomości DPI. Jednak jeśli współrzędnych lub obliczenia rozmiarów są wykonywane poza te przepływy pracy w głównym (np. podczas wykonywania zadania czas bezczynności lub wyłączone przez wątek interfejsu użytkownika, bieżącego kontekstu świadomości DPI mogą być niepoprawne, prowadzące do przemieszczenie interfejsu użytkownika lub źle rozmiaru problemów. Umieszczenie wątku w poprawnym stanie dla interfejsu użytkownika pracy zwykle rozwiąże problem.
 
#### <a name="opting-out-of-clmm"></a>Rezygnacja z CLMM
Jeśli okno narzędzia WPF nie jest przeprowadzana migracja do zapewnienia pełnej obsługi PMA, należy zrezygnować z CLMM. Aby to zrobić, nowy interfejs musi zostać wdrożone: IVsDpiAware.

C#:
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:
```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Dla języków zarządzanych, najlepszym miejscem, aby zaimplementować ten interfejs jest w tej samej klasy, która pochodzi od klasy *Microsoft.VisualStudio.Shell.ToolWindowPane*. Aby uzyskać C++, najlepszym miejscem, aby zaimplementować ten interfejs jest w tej samej klasy, która implementuje *IVsWindowPane* z vsshell.h.

Wartość zwracana przez właściwość trybu w interfejsie jest __VSDPIMODE (i Rzutowanie na uint w zarządzanych):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Oznacza okna narzędzi musi obsługiwać rozdzielczości 96 DPI, Windows będzie obsługiwać skalowanie go dla wszystkich innych rozdzielczościami. Wynikowe zawartości jest nieco rozmyty.
- Oznacza, że system okna narzędzi musi obsługiwać DPI dla podstawowego wyświetlanie rozdzielczości DPI. Wszelkie wyświetlanie za pomocą dopasowywania DPI wygląd rzeczowy, ale to wartość DPI różni się lub zmienia się podczas sesji, Windows będzie obsługiwać skalowanie i będzie on nieco rozmyty.
- PerMonitor oznacza, że okno narzędzia musi obsługiwać wszystkie rozdzielczościami na wszystkich ekranach i zawsze, gdy zmieni się to wartość DPI.

> [!NOTE]
> Visual Studio obsługuje tylko rozpoznawanie PerMonitorV2, więc wartość wyliczenia PerMonitor przekłada się na wartość Windows DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="forcing-a-control-into-a-specific-dpiawarenesscontext"></a>Wymuszanie formant do określonego DpiAwarenessContext
Starszy interfejs użytkownika, który nie został zaktualizowany do obsługi trybu PMA nadal może być konieczne wyglądało pracę, podczas gdy program Visual Studio jest uruchomiony w trybie PMA. Jednego takiego poprawkę obejmuje upewnienie się, że interfejs użytkownika jest tworzona w prawo DpiAwarenessContext. Aby wymusić interfejs użytkownika do konkretnej DpiAwarenessContext, można wprowadzić zakres rozdzielczości DPI następującym kodem:

C#:
```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

C++:
```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Wymuszanie DpiAwarenessContext działa tylko na - WPF UI i najwyższego poziomu wyświetlanymi w oknach dialogowych programu WPF. Podczas tworzenia interfejsu użytkownika aplikacji WPF, która jest hostowana wewnątrz okna narzędzi lub projektantów, zaraz po jego zawartość jest wstawiany do drzewa WPF UI, konwertowane do bieżącego procesu DpiAwarenessContext.

## <a name="known-issues"></a>Znane problemy
### <a name="windows-forms"></a>Windows Forms

Zoptymalizowane pod kątem nowych scenariuszy w trybie mieszanym, Windows Forms zmienić sposób tworzenia kontrolek i systemu windows zawsze wtedy, gdy ich nadrzędnego nie została jawnie ustawiona. Wcześniej kontrolek bez użycia jawny element nadrzędny używany wewnętrzny "parkowania okno" jako tymczasowe nadrzędnej do kontroli lub okna tworzona. 

Przed .NET 4.8 podczas jednego "parkowania okna" pobierające jego DpiAwarenessContext z bieżącego kontekstu świadomości DPI wątku w czasie tworzenia okna. Żadnego formantu, bez elementów nadrzędnych dziedziczy ten sam DpiAwarenessContext parkowania okna, gdy uchwyt formantu zostanie utworzona i będzie pokrewnym do elementu nadrzędnego final lub oczekiwanym przez dewelopera aplikacji. To spowoduje, że błędy na podstawie czasu Jeśli "Parkowania okno" miała wyższy DpiAwarenessContext niż okno nadrzędne końcowego.

Począwszy od .NET 4.8 jest teraz "Parkowania okna" dla każdego DpiAwarenessContext, które zostanie został osiągnięty. Główna różnica polega na tym, że DpiAwarenessContext formantu są buforowane, gdy formant zostanie utworzony, nie w momencie tworzenia dojścia. Oznacza to, się ogólnym zachowaniom zakończenia jest taka sama, ale można włączyć przeznaczenie problem na podstawie czasu do spójnego problem. Daje ona również Deweloper aplikacji bardziej przewidywalne działania do pisania kodu interfejsu użytkownika i określania zakresu poprawnie.
