---
title: Per-Monitor awareness support for Visual Studio extenders (Obsługa świadomości Visual Studio dla rozszerzenia)
titleSuffix: ''
description: Dowiedz się więcej na temat nowej obsługi rozszerzenia na monitor-awareness dostępnej w Visual Studio 2019 r.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902049"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Per-Monitor awareness support for Visual Studio extenders (Obsługa świadomości Visual Studio dla rozszerzenia)

Wersje wcześniejsze niż Visual Studio 2019 miały swój kontekst świadomości DPI ustawiony na system, a nie na monitor z wartością DPI (DPI Aware, PMA). Działanie w świadomości systemu powoduje obniżenie jakości wizualnej (np. rozmyte czcionki lub ikony), gdy program Visual Studio musiał renderować na monitorach o różnych współczynnikach skali lub zdalnie na komputerach z różnymi konfiguracjami wyświetlania (np. różne skalowanie systemu Windows).

Kontekst świadomości DPI programu Visual Studio 2019 jest ustawiany jako PMA, gdy środowisko go obsługuje, dzięki czemu program Visual Studio może być renderowany zgodnie z konfiguracją ekranu, na którym jest hostowany, a nie z jedną konfiguracją zdefiniowaną przez system. Ostatecznie tłumaczone na zawsze zbędny interfejs użytkownika dla obszarów powierzchni, które obsługują tryb PMA.

Zapoznaj się z [dokumentacją High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Tworzenie aplikacji klasycznych o wysokiej rozdzielczości w systemie Windows), aby uzyskać więcej informacji o warunkach i ogólnym scenariuszu, które zostały uwzględnione w tym dokumencie.

## <a name="quickstart"></a>Szybki start

- Upewnij się Visual Studio że program działa w trybie PMA (zobacz **Włączanie pma)**

- Sprawdź, czy rozszerzenie działa prawidłowo w ramach zestawu typowych scenariuszy (zobacz **Testowanie rozszerzeń w przypadku problemów z pma)**

- Jeśli znajdziesz problemy, możesz użyć strategii/zaleceń omówionych w tym dokumencie, aby zdiagnozować i rozwiązać te problemy. Należy również dodać nowy pakiet NuGet [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) do projektu, aby uzyskać dostęp do wymaganych interfejsów API.

## <a name="enable-pma"></a>Włączanie pma

Aby włączyć funkcję PMA Visual Studio, należy spełnić następujące wymagania:

- Aktualizacja systemu Windows 10 z kwietnia 2018 (wersja 1803, RS4) lub nowszy
- .NET Framework wersji 4.8 RTM lub większej
- Visual Studio 2019 r. z włączoną [opcją "Optymalizacja](../../ide/reference/general-environment-options-dialog-box.md) renderowania dla ekranów z różnymi gęstościami pikseli"

Gdy te wymagania zostaną spełnione, Visual Studio automatycznie włącza tryb PMA w całym procesie.

> [!NOTE]
> Windows Forms w programie Visual Studio (na przykład Przeglądarka właściwości) obsługuje funkcję PMA tylko wtedy, Visual Studio 2019 w wersji 16.1 lub nowszej.

## <a name="test-your-extensions-for-pma-issues"></a>Testowanie rozszerzeń pod przypadku problemów z pma

Visual Studio oficjalnie obsługuje platformy interfejsu użytkownika WPF, Windows Forms, Win32 i HTML/JS. Gdy Visual Studio tryb PMA, każdy stos interfejsu użytkownika zachowuje się inaczej. W związku z tym, niezależnie od struktury interfejsu użytkownika, zaleca się, aby przeprowadzić test przebiegu, aby upewnić się, że cały interfejs użytkownika jest zgodny z trybem PMA.

Zalecane jest zweryfikowanie następujących typowych scenariuszy:

- Zmiana współczynnika skali w środowisku pojedynczego monitora, gdy aplikacja jest uruchomiona.

  Ten scenariusz ułatwia przetestowanie, czy interfejs użytkownika odpowiada na dynamiczną zmianę dpi systemu Windows.

- Dokowanie/oddokowanie komputera przenośnego, na którym podłączony monitor jest ustawiony na podstawowy, a dołączony monitor ma inny współczynnik skali niż laptop, gdy aplikacja jest uruchomiona.

  Ten scenariusz ułatwia przetestowanie, czy interfejs użytkownika odpowiada na zmianę dpi wyświetlania, a także obsługę wyświetlania dynamicznie dodawanych lub usuwanych.

- Posiadanie wielu monitorów o różnych współczynnikach skali i przeniesienie aplikacji między nimi.

  Ten scenariusz pomaga przetestować, czy interfejs użytkownika odpowiada na zmianę dpi wyświetlania
    
- Komunikacja zdalna z maszyną, gdy maszyny lokalne i zdalne mają różne współczynniki skali dla monitora podstawowego.

  Ten scenariusz ułatwia przetestowanie, czy interfejs użytkownika odpowiada na dynamiczną zmianę dpi systemu Windows.

Dobrym wstępnym testem na to, czy interfejs użytkownika może mieć problemy, jest to, czy kod korzysta z klas *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper,* *Microsoft.VisualStudio.PlatformUI.DpiHelper,* *czy VsUI::CDpiHelper.* Te stare klasy DpiHelper obsługują tylko świadomość DPI systemu i nie zawsze będą działać poprawnie, gdy proces jest PMA.

Typowe zastosowanie tych dpiHelpers będzie wyglądać tak:

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

W poprzednim przykładzie prostokąt reprezentujący logiczne granice okna jest konwertowany na jednostki urządzenia, tak aby można je było przekazano do metody natywnej MonitorFromPoint, która oczekuje współrzędnych urządzenia w celu zwrócenia dokładnego wskaźnika monitora.

### <a name="classes-of-issues"></a>Klasy problemów
Gdy tryb PMA jest włączony dla Visual Studio, interfejs użytkownika może replikować problemy na kilka typowych sposobów. Większość, jeśli nie wszystkie, tych problemów może wystąpić w dowolnej Visual Studio obsługiwanych platformach interfejsu użytkownika. Ponadto te problemy mogą również wystąpić, gdy element interfejsu użytkownika jest hostowany w scenariuszach skalowania DPI w trybie mieszanym (zobacz dokumentację systemu [Windows,](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) aby dowiedzieć się więcej). 

#### <a name="win32-window-creation"></a>Tworzenie okna Win32
Podczas tworzenia okien za pomocą funkcji CreateWindow() lub CreateWindowEx() powszechnym wzorcem jest utworzenie okna o współrzędnych (0,0) (lewy górny róg ekranu podstawowego), a następnie przeniesienie go do jego ostatniej pozycji. Może to jednak spowodować wyzwolenie przez okno zmienionego komunikatu lub zdarzenia DPI, które może ponownie wyzwolić inne komunikaty lub zdarzenia interfejsu użytkownika, a ostatecznie doprowadzić do niepożądanego zachowania lub renderowania.

#### <a name="wpf-element-placement"></a>Umieszczanie elementów WPF
Podczas przenoszenia elementów WPF przy użyciu starego obiektu Microsoft.VisualStudio.Utilities.Dpi.DpiHelper współrzędne lewego górnego rogu mogą nie być obliczane prawidłowo za każdym razem, gdy elementy znajdują się w nie primary DPI.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Serializacja rozmiarów lub pozycji elementów interfejsu użytkownika
Po przywróceniu rozmiaru lub położenia interfejsu użytkownika (jeśli zostały zapisane jako jednostki urządzenia) w innym kontekście DPI niż to, w którym został on zapisany, zostanie on umieszczony i będzie miał niepoprawny rozmiar. Dzieje się tak, ponieważ jednostki urządzenia mają naturalną relację DPI.

#### <a name="incorrect-scaling"></a>Nieprawidłowe skalowanie
Elementy interfejsu użytkownika utworzone w podstawowej rozdzielczości DPI będą poprawnie skalowane, jednak gdy zostaną przeniesione do ekranu z inną wartością DPI, nie zostaną przeskalowane, a ich zawartość będzie zbyt duża lub zbyt mała.

#### <a name="incorrect-bounding"></a>Nieprawidłowe wiązanie
Podobnie jak w przypadku problemu ze skalowaniem, elementy interfejsu użytkownika poprawnie obliczają swoje granice w podstawowym kontekście DPI, jednak po przenoszonym do nie primary DPI nowe granice nie będą poprawnie obliczać nowych granic. W związku z tym okno zawartości jest zbyt małe lub zbyt duże w porównaniu z hostującym interfejsem użytkownika, co powoduje puste miejsce lub przycinanie.

#### <a name="drag--drop"></a>Przeciąganie & upuszczania
Zawsze, gdy wewnątrz scenariuszy DPI w trybie mieszanym (na przykład różne elementy interfejsu użytkownika są renderowane w różnych trybach świadomości DPI), współrzędne przeciągania i upuszczania mogą być błędnie obliczanie, co w rezultacie kończy się niepoprawną pozycją upuszczania.

#### <a name="out-of-process-ui"></a>Interfejs użytkownika poza procesem
Część interfejsu użytkownika jest tworzona poza procesem, a jeśli proces tworzenia zewnętrznego jest w innym trybie świadomości DPI niż Visual Studio, może to wprowadzić dowolny z poprzednich problemów z renderowaniem.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms kontrolki, obrazy lub układy są renderowane niepoprawnie
Nie cała zawartość Windows Forms obsługuje tryb PMA. W związku z tym może wystąpić problem z renderowaniem w przypadku nieprawidłowych układów lub skalowania. W takim przypadku możliwym rozwiązaniem jest jawne renderowanie zawartości Windows Forms "System Aware" DpiAwarenessContext (zobacz Wymuś kontrolkę do określonej [wartości DpiAwarenessContext).](#force-a-control-into-a-specific-dpiawarenesscontext)

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms lub okna nie są wyświetlane
Jedną z głównych przyczyn tego problemu jest to, że deweloperzy próbują ponownie przechwycić kontrolkę lub okno z jednym elementem DpiAwarenessContext do okna z innym elementem DpiAwarenessContext.

Na poniższych ilustracjach przedstawiono bieżące **domyślne ograniczenia** systemu operacyjnego Windows w oknach nadrzędnych:

![Zrzut ekranu przedstawiający poprawne zachowanie elementu nadrzędnego](media/PMA-parenting-behavior.PNG)

> [!Note]
> To zachowanie można zmienić, ustawiając zachowanie hostingu wątków (zobacz [wyliczenie Dpi_Hosting_Behavior](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)).

W związku z tym ustawienie relacji nadrzędny-podrzędny między nieobsługiwanymi trybami zakończy się niepowodzeniem, a kontrolka lub okno może nie być renderowane zgodnie z oczekiwaniami.

### <a name="diagnose-issues"></a>Diagnozowanie problemów

Istnieje wiele czynników, które należy wziąć pod uwagę podczas identyfikowania problemów związanych z pma: 

- Czy interfejs użytkownika lub interfejs API oczekuje wartości logicznych lub wartości urządzenia?
    - Interfejs użytkownika i interfejsy API WPF zwykle używają wartości logicznych (ale nie zawsze)
    - Interfejs użytkownika i interfejsy API Win32 zwykle używają wartości urządzenia

- Skąd pochodzą wartości?
    - W przypadku odbierania wartości z innego interfejsu użytkownika lub interfejsu API jest to przekazywanie wartości urządzenia lub logicznych.
    - Jeśli otrzymujesz wartości z wielu źródeł, czy wszystkie one używają/oczekują tych samych typów wartości, czy konwersje muszą być mieszane i dopasowane?

- Czy stałe interfejsu użytkownika są w użyciu i w jakiej postaci się znajdują?

- Czy wątek jest w poprawnym kontekście DPI dla wartości, które otrzymuje?

  Zmiany umożliwiające hostowanie mieszane DPI powinny zwykle umieszczać ścieżki kodu w odpowiednim kontekście, jednak praca wykonywana poza główną pętlą komunikatów lub przepływem zdarzeń może zostać wykonana w niewłaściwym kontekście DPI.

- Czy wartości przecinają granice kontekstu DPI?

  Przeciąganie & jest powszechną sytuacją, w której współrzędne mogą krzyżować konteksty DPI. Okno próbuje wykonać odpowiednie działania, ale w niektórych przypadkach interfejs użytkownika hosta może wymagać pracy konwersji w celu zapewnienia pasujących granic kontekstu.

### <a name="pma-nuget-package"></a>Pakiet NuGet PMA
Nowe biblioteki DpiAwarness można znaleźć w pakiecie NuGet [Microsoft.VisualStudio.DpiAwareness.](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/)

### <a name="recommended-tools"></a>Zalecane narzędzia
Poniższe narzędzia mogą pomóc w debugowaniu problemów związanych z pma dla niektórych różnych stosów interfejsu użytkownika obsługiwanych przez Visual Studio.

#### <a name="snoop"></a>Snoop
Snoop to narzędzie debugowania XAML, które ma pewne dodatkowe funkcje, których nie mają wbudowane Visual Studio JĘZYKA XAML. Ponadto Snoop nie musi aktywnie debugować interfejsu Visual Studio, aby móc wyświetlać i dostroić interfejs użytkownika WPF. Dwa główne sposoby, w jakie Snoop może być przydatny do diagnozowania problemów z PMA, to sprawdzania współrzędnych położenia logicznego lub granic rozmiaru, a do sprawdzania, czy interfejs użytkownika ma właściwą wartość DPI.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio narzędzi XAML
Podobnie jak snoop, narzędzia XAML w programie Visual Studio mogą pomóc zdiagnozować problemy z pma. Po odnalezioniu prawdopodobnego winy można ustawić punkty przerwania i użyć okna dynamicznego drzewa wizualnego, a także okien debugowania, aby sprawdzić granice interfejsu użytkownika i bieżącą wartość DPI.

## <a name="strategies-for-fixing-pma-issues"></a>Strategie rozwiązywania problemów z pma

### <a name="replace-dpihelper-calls"></a>Zastępowanie wywołań DpiHelper

W większości przypadków rozwiązywanie problemów z interfejsem użytkownika w trybie PMA sprowadza się do zastępowania wywołań w kodzie zarządzanym starym klasom *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* i *Microsoft.VisualStudio.PlatformUI.DpiHelper* wywołaniami nowej klasy pomocnika *Microsoft.VisualStudio.Utilities.DpiAwareness.* 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

W przypadku kodu natywnego wiąże się to z zastąpieniem wywołań starej klasy *VsUI::CDpiHelper* wywołaniami nowej klasy *VsUI::CDpiAwareness.* 

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

Nowe klasy DpiAwareness i CDpiAwareness oferują te same pomocniki konwersji jednostek co klasy DpiHelper, ale wymagają dodatkowego parametru wejściowego: elementu interfejsu użytkownika, który ma być odwołaniem do operacji konwersji. Należy pamiętać, że pomocnicy skalowania obrazów nie istnieją w nowych pomocnikach DpiAwareness/CDpiAwareness. W razie potrzeby należy zamiast tego użyć obiektu [ImageService.](../image-service-and-catalog.md)

Zarządzana klasa DpiAwareness oferuje pomocników dla wizualizacji WPF, kontrolek Windows Forms oraz identyfikatorów HWND Win32 i HMONRS (obie w postaci intPtrs), podczas gdy natywna klasa CDpiAwareness oferuje pomocników HWND i HMONITOR.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Windows Forms oknach dialogowych, oknach lub kontrolkach wyświetlanych w niewłaściwym pliku DpiAwarenessContext
Nawet po pomyślnym wytyczeniu okien z różnymi obiektami DpiAwarenessContexts (z powodu domyślnego zachowania systemu Windows) użytkownicy mogą nadal widzieć problemy ze skalowaniem, ponieważ okna z różnymi wartościami DpiAwarenessContexts są skalowane w różny sposób. W związku z tym użytkownicy mogą zobaczyć problemy z wyrównaniem/rozmytym tekstem lub obrazem w interfejsie użytkownika.

Rozwiązaniem jest ustawienie poprawnego zakresu DpiAwarenessContext dla wszystkich okien i kontrolek w aplikacji.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Okna dialogowe trybu mieszanego najwyższego poziomu (TLMM)
Podczas tworzenia okien najwyższego poziomu, takich jak modalne okna dialogowe, należy upewnić się, że wątek jest w prawidłowym stanie przed utworzeniem okna (i jego uchwytu). Wątek można umieścić w świadomości systemu przy użyciu pomocnika CDpiScope w natywnym lub pomocnika DpiAwareness.EnterDpiScope w zarządzanym. (TLMM zwykle należy używać w oknach dialogowych/oknach innych niż WPF).

### <a name="child-level-mixed-mode-clmm"></a>Tryb mieszany na poziomie podrzędnym (CLMM)
Domyślnie okna podrzędne odbierają bieżący kontekst świadomości DPI wątku, jeśli został utworzony bez elementu nadrzędnego, lub kontekst świadomości DPI elementu nadrzędnego w przypadku utworzenia za pomocą elementu nadrzędnego. Aby utworzyć element podrzędny z innym kontekstem świadomości DPI niż jego element nadrzędny, wątek można umieścić w żądanym kontekście świadomości DPI. Następnie element podrzędny można utworzyć bez elementu nadrzędnego i ręcznie ponownie przetworzyć z oknem nadrzędnym.

#### <a name="clmm-issues"></a>Problemy z clmm
Większość obliczeń interfejsu użytkownika, które są częścią głównej pętli obsługi komunikatów lub łańcucha zdarzeń, powinna być już uruchomiona w odpowiednim kontekście świadomości DPI. Jeśli jednak obliczenia współrzędnych lub rozmiarów są wykonywane poza głównymi przepływami pracy (na przykład podczas zadania w czasie bezczynności lub poza wątkiem interfejsu użytkownika, bieżący kontekst świadomości DPI może być nieprawidłowy, co prowadzi do problemów z nieprawidłowym miejscem interfejsu użytkownika lub błędnym ustawieniem rozmiaru). Umieszczenie wątku w prawidłowym stanie dla pracy interfejsu użytkownika zwykle rozwiązuje problem.
 
#### <a name="opt-out-of-clmm"></a>Rezygnacja z clmm
Jeśli okno narzędzi inne niż WPF jest migrowane w celu pełnej obsługi pma, należy zrezygnować z clmm. W tym celu należy zaimplementować nowy interfejs: IVsDpiAware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
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

W przypadku języków zarządzanych najlepszym miejscem do zaimplementowania tego interfejsu jest klasa pochodząca od klasy *Microsoft.VisualStudio.Shell.ToolWindowPane.* W przypadku języka C++ najlepszym miejscem do zaimplementowania tego interfejsu jest ta sama klasa, która implementuje interfejs *IVsWindowPane* z vsshell.h.

Wartość zwracana przez właściwość Mode interfejsu jest __VSDPIMODE (i rzutowana na uint w zarządzanym):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Nieświadome oznacza, że okno narzędzia musi obsługiwać rozdzielczość 96 DPI, a system Windows będzie obsługiwać skalowanie dla wszystkich innych interfejsów DPI. W wyniku zawartość jest nieco rozmyte.
- System oznacza, że okno narzędzia musi obsługiwać dpi dla podstawowego wyświetlania DPI. Wszystkie ekrany z pasującą wartością DPI będą wyglądały na rozmyte, ale jeśli wartość DPI będzie inna lub zmieni się podczas sesji, system Windows obsłuży skalowanie i będzie nieco rozmyte.
- PerMonitor oznacza, że okno narzędzia musi obsługiwać wszystkie dpi na wszystkich ekranach i przy każdej zmianie dpi.

> [!NOTE]
> Visual Studio obsługuje tylko świadomość PerMonitorV2, więc wartość wyliczania PerMonitor przekłada się na wartość systemu Windows DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Wymuś kontrolkę do określonej wartości DpiAwarenessContext

Starszy interfejs użytkownika, który nie jest aktualizowany w celu obsługi trybu PMA, może nadal wymagać drobnych dostrojeń, aby działał Visual Studio w trybie PMA. Jedna z takich poprawek obejmuje upewnienie się, że interfejs użytkownika jest tworzony w prawej stronie dpiAwarenessContext. Aby wymusić na interfejsie użytkownika określony element DpiAwarenessContext, możesz wprowadzić zakres DPI przy użyciu następującego kodu:

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
> Wymuś wartość DpiAwarenessContext tylko w oknach dialogowych interfejsu użytkownika innych niż WPF i WPF najwyższego poziomu. Podczas tworzenia interfejsu użytkownika WPF, który ma być hostowany wewnątrz okien narzędzi lub projektantów, natychmiast po wstawieniu zawartości do drzewa interfejsu użytkownika WPF jest ona konwertowana na bieżący proces DpiAwarenessContext.

## <a name="known-issues"></a>Znane problemy

### <a name="windows-forms"></a>Windows Forms

Aby zoptymalizować pod kątem nowych scenariuszy w trybie mieszanym, Windows Forms sposób tworzenia kontrolek i okien, gdy ich elementy nadrzędne nie zostały jawnie ustawione. Wcześniej kontrolki bez jawnego elementu nadrzędnego używały wewnętrznego "okna z oknaMiadło" jako tymczasowego elementu nadrzędnego dla tworzonej kontrolki lub okna. 

W systemach wcześniejszych niż .NET 4.8 był dostępny pojedynczy obiekt "Okno z cyfergą", który pobiera jego obiekt DpiAwarenessContext z kontekstu świadomości DPI bieżącego wątku w czasie tworzenia okna. Każda kontrolka bez elementu nadrzędnego dziedziczy tę samą wartość DpiAwarenessContext, co okno Okna z okienkiem Okna z oknaMiedzy, gdy zostanie utworzone dojście kontrolki, i zostanie ponownie przejmowana do końcowego/oczekiwanego elementu nadrzędnego przez dewelopera aplikacji. Może to spowodować błędy oparte na chronometrażu, jeśli wartość "Okna z oknami okien okiennych" jest większa niż w końcowym oknie nadrzędnym.

W programie .NET 4.8 jest teraz dostępne "okno z cyferfertą" dla każdego napotkanego obiektu DpiAwarenessContext. Inną główną różnicą jest to, że wartość DpiAwarenessContext używana dla kontrolki jest buforowana podczas tworzenia kontrolki, a nie podczas tworzenia dojścia. Oznacza to, że ogólne zachowanie końcowe jest takie samo, ale może przekształcić to, co było kiedyś problemem opartym na chronometrażu, w spójny problem. Zapewnia to również deweloperowi aplikacji bardziej deterministyczne zachowanie podczas pisania kodu interfejsu użytkownika i poprawnego określania zakresu.
