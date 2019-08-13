---
title: Obsługa zapewniania świadomości dla rozszerzeń programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej o nowej obsłudze rozszerzeń dla poszczególnych monitorów dostępnych w programie Visual Studio 2019.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 2686248a087650f6170b72c8ef9b3a77e2ba275c
ms.sourcegitcommit: 6f3cf7a1bfc81a61f9a603461a1c34fd2221f100
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957352"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Obsługa zapewniania świadomości dla rozszerzeń programu Visual Studio

Wersje starsze niż program Visual Studio 2019 mają kontekst rozpoznawania DPI ustawiony dla systemu, a nie dla monitora (PMA). Działanie w systemie rozpoznawania systemu spowodowało spadek wydajności wizualizacji (np. czcionki rozmyte lub ikony), gdy program Visual Studio ma renderować różne monitory z różnymi czynnikami skalowania lub zdalnie na maszynach z różnymi konfiguracjami wyświetlania (np. różne Skalowanie systemu Windows).

Kontekst rozpoznawania DPI programu Visual Studio 2019 jest ustawiany jako PMA, gdy obsługuje to środowisko, co pozwala programowi Visual Studio na renderowanie zgodnie z konfiguracją ekranu, w którym jest hostowana, a nie z jedną konfiguracją zdefiniowaną w systemie. Ostatecznie tłumaczenie na zawsze wyrazisty interfejs użytkownika dla obszarów powierzchni, które obsługują tryb PMA.

Więcej informacji na temat terminów i ogólnego scenariusza omówionego w tym dokumencie znajduje się w dokumentacji [systemu Windows o wysokiej rozdzielczości DPI](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) .

## <a name="quickstart"></a>Szybki start

- Upewnij się, że program Visual Studio jest uruchomiony w trybie PMA (patrz **Włączanie PMA**)

- Sprawdzanie poprawności rozszerzenia działa prawidłowo w ramach zestawu typowych scenariuszy (zobacz **Testowanie rozszerzeń w przypadku problemów z PMA**)

- Jeśli znajdziesz problemy, możesz użyć strategii/zaleceń omówionych w tym dokumencie, aby zdiagnozować i rozwiązać te problemy. Należy również dodać nowy pakiet NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) do projektu w celu uzyskania dostępu do wymaganych interfejsów API.

## <a name="enable-pma"></a>Włącz PMA

Aby włączyć PMA w programie Visual Studio, należy spełnić następujące wymagania:

- Aktualizacja systemu Windows 10 z kwietnia 2018 (v1803, RS4) lub nowsza
- .NET Framework 4,8 RTM lub nowszy
- Program Visual Studio 2019 z włączoną opcją ["Optymalizuj renderowanie ekranów z inną gęstością pikseli"](../../ide/reference/general-environment-options-dialog-box.md)

Po spełnieniu tych wymagań program Visual Studio automatycznie włącza tryb PMA w całym procesie.

> [!NOTE]
> Windows Forms content in Visual Studio (na przykład Browser Property) obsługuje PMA tylko wtedy, gdy masz program Visual Studio 2019 w wersji 16,1 lub nowszej.

## <a name="test-your-extensions-for-pma-issues"></a>Testowanie rozszerzeń pod kątem problemów z PMA

Program Visual Studio oficjalnie obsługuje struktury interfejsu użytkownika WPF, Windows Forms, Win32 i HTML/JS. Gdy program Visual Studio jest włączony w trybie PMA, każdy stos interfejsu użytkownika działa inaczej. W związku z tym niezależnie od struktury interfejsu użytkownika zaleca się wykonanie przebiegu testowego, aby upewnić się, że wszystkie elementy interfejsu użytkownika są zgodne z trybem PMA.

Zalecane jest zweryfikowanie następujących typowych scenariuszy:

- Zmiana współczynnika skalowania pojedynczego środowiska monitorowania, gdy aplikacja jest uruchomiona.

  Ten scenariusz pomaga sprawdzić, czy interfejs użytkownika odpowiada na dynamiczną zmianę systemu Windows.

- Dokowanie/oddokowanie komputera przenośnego, na którym jest ustawiony podłączony monitor, a podłączony monitor ma różny współczynnik skalowania niż laptop, gdy aplikacja jest uruchomiona.

  W tym scenariuszu można sprawdzić, czy interfejs użytkownika odpowiada na zmiany rozdzielczości DPI, a także czy jest dynamicznie dodawany lub usuwany.

- Posiadanie wielu monitorów o różnych współczynnikach skalowania i przeniesienie aplikacji między nimi.

  Ten scenariusz pomaga testować, że ten interfejs użytkownika odpowiada na zmianę wyświetlacza DPI
    
- Komunikacja zdalna z maszyną, gdy maszyna lokalna i zdalna mają różne czynniki skalowania do monitora podstawowego.

  Ten scenariusz pomaga sprawdzić, czy interfejs użytkownika odpowiada na dynamiczną zmianę systemu Windows.

Dobry test wstępny dla tego, czy interfejs użytkownika może mieć problemy, to czy kod wykorzystuje klasy *Microsoft. VisualStudio. Utilities. dpi. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper*lub *VsUI:: CDpiHelper* . Te stare klasy DpiHelper obsługują rozpoznawanie DPI systemu i nie zawsze działają prawidłowo, gdy proces jest PMA.

Typowy sposób użycia tych DpiHelpers będzie wyglądać następująco:

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

W poprzednim przykładzie prostokąt reprezentujący granice logiczne okna jest konwertowany na jednostki urządzeń, dzięki czemu można go przesłać do metody natywnej MonitorFromPoint, która oczekuje współrzędnych urządzenia, aby przywrócić dokładny wskaźnik monitora.

### <a name="classes-of-issues"></a>Klasy problemów
Gdy tryb PMA jest włączony dla programu Visual Studio, interfejs użytkownika może replikować problemy na kilka typowych sposobów. Większość (jeśli nie wszystkie) te problemy mogą wystąpić w dowolnych obsługiwanych strukturach interfejsu użytkownika programu Visual Studio. Ponadto te problemy mogą występować, gdy element interfejsu użytkownika jest hostowany w scenariuszach skalowania DPI w trybie mieszanym (zapoznaj się z [dokumentacją](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) systemu Windows, aby dowiedzieć się więcej). 

#### <a name="win32-window-creation"></a>Tworzenie okna Win32
Podczas tworzenia systemu Windows przy użyciu elementu elementu CreateWindowEx () lub () wspólny wzorzec polega na utworzeniu okna według współrzędnych (0, 0) (górny/lewy róg ekranu głównego), a następnie przenieść go do ostatecznego położenia. Jednak może to spowodować, że okno wyzwala komunikat o zmienionym lub zdarzeniu DPI, które może ponownie wyzwolić inne komunikaty lub zdarzenia interfejsu użytkownika, a ostatecznie prowadzić do niepożądanego zachowania lub renderowania.

#### <a name="wpf-element-placement"></a>Położenie elementu WPF
W przypadku przesuwania elementów WPF przy użyciu starych współrzędnych Microsoft. VisualStudio. Utilities. dpi. DpiHelper, współrzędne Top-Left mogą nie być obliczane prawidłowo, gdy elementy znajdują się w niepodstawowej rozdzielczości DPI.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializacja rozmiarów elementów interfejsu użytkownika lub pozycji
Po przywróceniu rozmiaru lub pozycji interfejsu użytkownika (jeśli zapisano jako jednostki urządzenia) w innym kontekście DPI niż to, w którym został on zapisany, zostanie on ustawiony nieprawidłowo. Dzieje się tak, ponieważ jednostki urządzeń mają niezależną relację DPI.

#### <a name="incorrect-scaling"></a>Nieprawidłowe skalowanie
Elementy interfejsu użytkownika utworzone na podstawowej DPI są skalowane prawidłowo, jednak podczas przenoszenia do wyświetlania z inną rozdzielczością DPI nie są one zmieniane, a ich zawartość jest za duża lub za mała.

#### <a name="incorrect-bounding"></a>Nieprawidłowe ograniczenie
Podobnie jak w przypadku problemu z skalowaniem elementy interfejsu użytkownika odpowiednio obliczają swoje powiązania w podstawowym kontekście DPI, ale w przypadku przeniesienia do niepodstawowej wartości DPI nie obliczają poprawnie nowych granic. W związku z tym okno zawartości jest zbyt małe lub zbyt duże w porównaniu z interfejsem użytkownika hostingu, co powoduje puste miejsce lub przycinanie.

#### <a name="drag--drop"></a>Przeciągnij & upuść
Za każdym razem, gdy działa w trybie mieszanym (na przykład inne elementy interfejsu użytkownika Renderuj w różnych trybach rozpoznawania DPI), współrzędnych przeciągania i upuszczania może być błędnie obliczony, co powoduje nieprawidłowe zakończenie ostatecznej pozycji upuszczania.

#### <a name="out-of-process-ui"></a>Nieprzetwarzany interfejs użytkownika
Niektóre elementy interfejsu użytkownika zostały utworzone poza procesem, a jeśli proces tworzenia zewnętrznego ma inny tryb rozpoznawania DPI niż program Visual Studio, może to spowodować, że wszystkie poprzednie problemy z renderowaniem.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms kontrolki, obrazy lub układy renderowane niepoprawnie
Nie wszystkie Windows Forms Content obsługują tryb PMA. W związku z tym może wystąpić problem z renderowaniem z nieprawidłowymi układami lub skalowaniem. Możliwe rozwiązanie w tym przypadku jest jawnie renderowane Windows Forms zawartości w DpiAwarenessContext "system aware" (Zobacz, aby wymusić [kontrolę w określonym DpiAwarenessContext](#force-a-control-into-a-specific-dpiawarenesscontext)).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Kontrolki Windows Forms lub okna niewyświetlane
Jednym z głównych przyczyn tego problemu są deweloperzy próbujący zmienić nadrzędny formant lub okno z jednym DpiAwarenessContextem do okna z innym DpiAwarenessContextem.

Na poniższych ilustracjach przedstawiono bieżące **domyślne** ograniczenia systemu operacyjnego Windows w oknach nadrzędnych:

![Zrzut ekranu przedstawiający poprawność działania nadrzędnego](media/PMA-parenting-behavior.PNG)

> [!Note]
> Możesz zmienić to zachowanie, ustawiając zachowanie hostingu wątku (zobacz [Wyliczenie Dpi_Hosting_Behavior](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

W związku z tym, jeśli ustawisz relację nadrzędny-podrzędny między nieobsługiwanymi trybami, zakończy się niepowodzeniem, a kontrolka lub okno może nie być renderowane zgodnie z oczekiwaniami.

### <a name="diagnose-issues"></a>Diagnozuj problemy

Istnieje wiele czynników, które należy wziąć pod uwagę podczas identyfikowania problemów związanych z PMA: 

- Czy interfejs użytkownika lub interfejs API oczekuje wartości logicznych lub urządzeń?
    - Interfejs użytkownika i interfejsy API WPF zazwyczaj używają wartości logicznych (ale nie zawsze).
    - Interfejs użytkownika Win32 i interfejsy API zwykle korzystają z wartości urządzeń

- Gdzie są wartości z?
    - W przypadku odebrania wartości z innego interfejsu użytkownika lub interfejsu API program przepuszcza urządzenie lub wartości logiczne.
    - Czy w przypadku otrzymywania wartości z wielu źródeł należy używać tych samych typów wartości, czy też przeprowadzić konwersję i dopasować je?

- Czy są używane stałe interfejsu użytkownika i do jakich formularzy?

- Czy wątek w prawidłowym kontekście DPI dla wartości, które otrzymuje?

  Zmiany mające na celu włączenie obsługi mieszanych DPI powinny zwykle umieszczać ścieżki kodu w odpowiednim kontekście, jednak działają poza główną pętlą komunikatów lub przepływem zdarzeń mogą być wykonywane w nieprawidłowym kontekście DPI.

- Czy wartości w granicach kontekstu są krzyżowe?

  Przeciąganie & upuszczania to typowa sytuacja, w której współrzędne mogą przekroczyć konteksty DPI. Okno próbuje wykonać odpowiednie działania, ale w niektórych przypadkach może być konieczne wykonanie konwersji przez interfejs użytkownika hosta w celu zapewnienia zgodności z granicami kontekstu.

### <a name="pma-nuget-package"></a>Pakiet NuGet PMA
Nowe biblioteki DpiAwarness można znaleźć w pakiecie NuGet [Microsoft. VisualStudio. DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) .

### <a name="recommended-tools"></a>Zalecane narzędzia
Poniższe narzędzia mogą pomóc debugować problemy związane z PMAą na różnych stosach interfejsu użytkownika obsługiwanych przez program Visual Studio.

#### <a name="snoop"></a>Słuchiwani
Podsłuchiwanie to narzędzie debugowania XAML, które ma dodatkowe funkcje, które nie mają wbudowanych narzędzi języka XAML programu Visual Studio. Ponadto nasłuchiwanie nie musi aktywnie debugować programu Visual Studio, aby można było wyświetlać i dostrajać swój interfejs użytkownika WPF. Te dwa podstawowe sposoby, które mogą być przydatne do diagnozowania problemów z PMAem, to sprawdzanie współrzędnych logicznego położenia lub granic rozmiaru, a w celu sprawdzenia, czy interfejs użytkownika ma odpowiednią wartość DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Narzędzia XAML programu Visual Studio
Podobnie jak w przypadku wysłuchiwania, narzędzia XAML w programie Visual Studio mogą pomóc zdiagnozować problemy z PMA. Po znalezieniu prawdopodobnie przyczyna można ustawić punkty przerwania i użyć aktywnego okna drzewa wizualnego, a także okien debugowania, aby sprawdzić granice interfejsu użytkownika i bieżącą wartość DPI.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie rozwiązywania problemów z PMA

### <a name="replace-dpihelper-calls"></a>Zastąp wywołania DpiHelper

W większości przypadków Rozwiązywanie problemów z interfejsem użytkownika w trybie PMA powoduje zagotowanie wywołań w kodzie zarządzanym do starej klasy *Microsoft. VisualStudio. Utilities. dpi. DpiHelper* i *Microsoft. VisualStudio. PlatformUI. DpiHelper* , z wywołaniami do nowego  *Microsoft. VisualStudio. Utilities. DpiAwareness* — Klasa pomocnika. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

W przypadku kodu natywnego będzie to wymagało zamiany wywołań do starej klasy *VsUI:: CDpiHelper* z wywołaniami nowej klasy *VsUI:: CDpiAwareness* . 

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

Nowe klasy DpiAwareness i CDpiAwareness oferują te same pomocników konwersji jednostek jak klasy DpiHelper, ale wymagają dodatkowego parametru wejściowego: elementu interfejsu użytkownika, który ma być używany jako odwołanie do operacji konwersji. Należy pamiętać, że pomocników skalowania obrazu nie ma w nowych pomocnikach DpiAwareness/CDpiAwareness i w razie potrzeby [ImageService](../image-service-and-catalog.md) powinien zostać użyty.

Zarządzana Klasa DpiAwareness oferuje pomocników dla wizualizacji WPF, formantów Windows Forms i elementów HWND Win32 oraz HMONITORs (zarówno w postaci elementów IntPtr), natomiast natywna Klasa CDpiAwareness oferuje niey i HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Okna dialogowe Windows Forms, okna lub kontrolki wyświetlane w niewłaściwym DpiAwarenessContext
Nawet po pomyślnym utworzeniu nadrzędnego systemu Windows przy użyciu różnych DpiAwarenessContexts (z powodu domyślnego zachowania systemu Windows) użytkownicy mogą nadal zobaczyć problemy ze skalowaniem jako Windows z różnymi skalowaniami DpiAwarenessContexts w różny sposób. W związku z tym użytkownicy mogą zobaczyć wyrównania/rozmycie tekstu lub problemów z obrazami w interfejsie użytkownika.

Rozwiązaniem jest ustawienie prawidłowego zakresu DpiAwarenessContext dla wszystkich okien i kontrolek w aplikacji.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Okna dialogowe trybu mieszanego (TLMM) najwyższego poziomu
Podczas tworzenia okien najwyższego poziomu, takich jak modalne okna dialogowe, należy upewnić się, że wątek jest w prawidłowym stanie przed utworzeniem okna (i jego dojściem). Wątek może być wprowadzany do świadomości systemu przy użyciu pomocnika CDpiScope w trybie macierzystym lub pomocnika DpiAwareness. EnterDpiScope w obszarze zarządzanym. (TLMM powinny być zwykle używane w oknach dialogowych, które nie są oparte na platformie WPF/Windows).

### <a name="child-level-mixed-mode-clmm"></a>Tryb mieszany na poziomie podrzędnym (CLMM)
Domyślnie okna podrzędne otrzymują bieżący kontekst świadomości DPI wątku, jeśli został utworzony bez elementu nadrzędnego lub kontekstu rozpoznawania wartości DPI dla elementu nadrzędnego podczas tworzenia z elementem nadrzędnym. Aby utworzyć element podrzędny o innym kontekście rozpoznawania DPI niż jego obiekt nadrzędny, wątek można umieścić w żądanym kontekście rozpoznawania DPI. Następnie element podrzędny można utworzyć bez obiektu nadrzędnego i ręcznie ponownie nadrzędny w oknie nadrzędnym.

#### <a name="clmm-issues"></a>CLMM problemy
Większość zadań obliczeniowych interfejsu użytkownika, które są wykonywane w ramach głównej pętli obsługi komunikatów lub łańcucha zdarzeń, powinna być już uruchomiona w prawym kontekście rozpoznawania wartości DPI. Jednakże, jeśli obliczenia współrzędnych lub rozmiarów są wykonywane poza tymi głównymi przepływami pracy (na przykład w czasie wykonywania zadania bezczynności lub poza wątkiem interfejsu użytkownika, bieżący kontekst rozpoznawania DPI może być nieprawidłowy, ponieważ problemy z nieprawidłowym rozmieszczeniem interfejsu użytkownika lub błędne zmiany rozmiarów). Umieszczenie wątku w poprawnym stanie dla interfejsu użytkownika zwykle rozwiązuje problem.
 
#### <a name="opt-out-of-clmm"></a>Zrezygnuj z CLMM
Jeśli przeprowadzono migrację okna narzędzi innego niż WPF do pełnej obsługi PMA, konieczne będzie rezygnacja z CLMM. Aby to zrobić, należy zaimplementować nowy interfejs: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

W przypadku języków zarządzanych najlepszym miejscem do wdrożenia tego interfejsu jest ta sama klasa, która pochodzi od *Microsoft. VisualStudio. Shell. elementu toolwindowpane*. W C++przypadku, najlepszym miejscem do wdrożenia tego interfejsu jest w tej samej klasie, która implementuje *interfejsu IVsWindowPane* z vsshell. h.

Wartość zwrócona przez Właściwość Mode w interfejsie to element __VSDPIMODE (i rzutowany do elementu uint w zarządzanych):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Nieświadome oznacza, że okno narzędzi musi obsługiwać 96 DPI, system Windows obsłuży skalowanie go dla wszystkich innych rozdzielczościami. Dzięki czemu zawartość jest nieco zamazana.
- System oznacza, że okno narzędzi musi obsłużyć wartość DPI na potrzeby podstawowego wyświetlacza DPI. Każdy ekran o pasującej rozdzielczości DPI będzie wyglądał wyraźniejszy, ale jeśli wartość DPI jest inna lub zmienia się w trakcie sesji, system Windows obsłuży skalowanie i będzie nieznacznie zamazany.
- PerMonitor oznacza, że okno narzędzi musi obsługiwać wszystkie rozdzielczościami na wszystkich ekranach i za każdym razem, gdy zmienia się wartość DPI.

> [!NOTE]
> Program Visual Studio obsługuje tylko świadomość PerMonitorV2, więc wartość wyliczenia PerMonitor jest tłumaczona na wartość DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 w systemie Windows.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Wymuś kontrolę w określonym DpiAwarenessContext

Starszy interfejs użytkownika, który nie jest aktualizowany do obsługi trybu PMA, może nadal potrzebować drobnych dostosowań do pracy, gdy program Visual Studio jest uruchomiony w trybie PMA. Takie rozwiązanie obejmuje upewnienie się, że interfejs użytkownika jest tworzony w prawym DpiAwarenessContext. Aby wymusić, że interfejs użytkownika należy do określonego DpiAwarenessContext, możesz wprowadzić zakres DPI przy użyciu następującego kodu:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> Wymuszanie DpiAwarenessContext działa tylko w interfejsie użytkownika innym niż WPF i w oknach dialogowych WPF najwyższego poziomu. Podczas tworzenia interfejsu użytkownika WPF, który ma być hostowany w oknach narzędzi lub projektantach, gdy tylko zawartość zostanie wstawiona do drzewa interfejsu użytkownika WPF, zostanie przekonwertowana na bieżący proces DpiAwarenessContext.

## <a name="known-issues"></a>Znane problemy

### <a name="windows-forms"></a>Windows Forms

Aby zoptymalizować w przypadku nowych scenariuszy w trybie mieszanym, Windows Forms zmienić sposób tworzenia formantów i okien, gdy ich element nadrzędny nie został jawnie ustawiony. Wcześniej kontrolki bez jawnego elementu nadrzędnego używały wewnętrznego "okna parkingowego" jako tymczasowego elementu nadrzędnego dla tworzonego formantu lub okna. 

Przed rozpoczęciem pracy z platformą .NET 4,8 istniało jedno "okno parkingowe", które pobiera jego DpiAwarenessContext z bieżącego kontekstu świadomości DPI wątku podczas tworzenia okna. Wszystkie nienadrzędne kontrolki dziedziczą ten sam DpiAwarenessContext, co okno przeparkowania, gdy zostanie utworzone uchwyt kontrolki i zostanie on zastąpiony do końcowego/oczekiwanego elementu nadrzędnego przez dewelopera aplikacji. Może to spowodować błędy oparte na czasie, jeśli "okno parkingowe" miało wyższy DpiAwarenessContext niż końcowe okno nadrzędne.

Począwszy od programu .NET 4,8, istnieje teraz "okno parkingowe" dla wszystkich DpiAwarenessContext, które zostały napotkane. Druga główna różnica polega na tym, że DpiAwarenessContext używany dla formantu jest buforowany podczas tworzenia kontrolki, a nie podczas tworzenia dojścia. Oznacza to, że całkowite zachowanie końcowe jest takie samo, ale może to zmienić, co jest problemem w celu zapewnienia spójnego problemu. Zapewnia również deweloperom aplikacji bardziej deterministyczne zachowanie podczas pisania kodu interfejsu użytkownika i poprawnego określania zakresu.
