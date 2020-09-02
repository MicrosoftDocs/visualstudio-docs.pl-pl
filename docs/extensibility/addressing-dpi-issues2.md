---
title: Adresowanie Issues2 DPI | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740108"
---
# <a name="address-dpi-issues"></a>Problemy dotyczące DPI adresów
Rosnąca liczba urządzeń jest wysyłana z ekranami o wysokiej rozdzielczości. Ekrany te zwykle mają ponad 200 pikseli na cal (ppi). Praca z aplikacją na tych komputerach będzie wymagała skalowania zawartości w górę w celu spełnienia potrzeb związanych z wyświetlaniem zawartości przy normalnej odległości do wyświetlania na urządzeniu. Począwszy od 2014, podstawowy element docelowy dla ekranów o wysokiej gęstości jest urządzeniami przenośnymi z obsługą urządzeń przenośnych (tabletów, laptopów clamshell i telefonów).

Windows 8.1 i więcej zawiera kilka funkcji umożliwiających tym maszynom współdziałanie z ekranami i środowiskami, w których maszyna jest dołączona jednocześnie do wyświetlaczy o wysokiej gęstości i gęstości.

- System Windows może umożliwić skalowanie zawartości na urządzeniu przy użyciu ustawienia "Wprowadź tekst i inne elementy większe lub mniejsze" (dostępne od systemu Windows XP).

- Funkcja Windows 8.1 i wyższa automatycznie skaluje zawartość dla większości aplikacji, która będzie spójna podczas przenoszenia między ekranami o różnej gęstości pikseli. Gdy podstawowy wyświetlacz ma wysoką gęstość (200% skalowania), a wyświetlacz pomocniczy jest gęstością standardową (100%), system Windows automatycznie skaluje zawartość okna aplikacji na ekranie pomocniczym (1 piksel wyświetlany dla każdego 4 pikseli renderowanego przez aplikację).

- System Windows będzie domyślnie miał prawo do skalowania gęstości pikseli i wyświetlania odległości ekranu (system Windows 7 i nowsze wersje OEM — konfigurowalne).

- System Windows może automatycznie skalować zawartość do 250% na nowych urządzeniach, które przekraczają 280 PPI (w Windows 8.1 S14).

  System Windows umożliwia przeznaczenie skalowania interfejsu użytkownika w celu wykorzystania większej liczby pikseli. Aplikacja zdecyduje się w tym systemie poprzez zadeklarując samo "systemowej rozdzielczości DPI". Aplikacje, które nie wykonują tej czynności, są skalowane przez system. Może to spowodować "rozmyte" środowisko użytkownika, w którym cała aplikacja jest jednolicie rozciągana o piksele. Na przykład:

  ![Rozmyte problemy dotyczące DPI](../extensibility/media/dpi-issues-fuzzy.png "Rozmyte problemy dotyczące DPI")

  Program Visual Studio umożliwia skalowanie w rozdzielczości DPI i w związku z tym nie jest "zwirtualizowany".

  Systemy Windows (i Visual Studio) wykorzystują kilka technologii interfejsu użytkownika, które mają różne sposoby postępowania z czynnikami skalowania ustawionymi przez system. Na przykład:

- WPF mierzy kontrolki w sposób niezależny od urządzenia (jednostki, nie piksele). Interfejs użytkownika WPF automatycznie skaluje się w górę dla bieżącej wartości DPI.

- Wszystkie rozmiary tekstu niezależnie od struktury interfejsu użytkownika są wyrażane w punktach i dlatego są traktowane przez system jako niezależne od rozdzielczości DPI. Tekst w Win32, WinForms i WPF jest już prawidłowo skalowany po narysowaniu na urządzeniu wyświetlającym.

- Okna dialogowe Win32/WinForms i Windows mają na celu włączenie układu, który zmienia rozmiar tekstu (na przykład za pośrednictwem paneli siatki, przepływu i układu tabeli). Umożliwiają one uniknięcie sztywno zakodowanych lokalizacji pikseli, które nie są skalowane po zwiększeniu rozmiaru czcionki.

- Ikony udostępniane przez system lub zasoby oparte na metrykach systemu (na przykład SM_CXICON i SM_CXSMICON) są już skalowane.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starszy interfejs użytkownika systemu Win32 (GDI, GDI+) i WinForms
Podczas gdy WPF jest już wysoce oparty na rozdzielczości DPI, większość kodu opartego na systemie Win32/GDI nie została pierwotnie zapisywana z uwzględnieniem świadomości DPI. System Windows udostępnia interfejsy API skalowania DPI. Poprawki do problemów z systemem Win32 powinny być stosowane konsekwentnie w całym produkcie. Program Visual Studio dostarczył bibliotekę klas pomocnika, aby uniknąć duplikowania funkcjonalności i zapewnienia spójności w produkcie.

## <a name="high-resolution-images"></a>Obrazy o wysokiej rozdzielczości
Ta sekcja dotyczy głównie deweloperów, którzy rozszerzają Visual Studio 2013. W przypadku programu Visual Studio 2015 Użyj usługi Image Service, która jest wbudowana w program Visual Studio. Możesz również sprawdzić, czy jest wymagana obsługa/docelowa wiele wersji programu Visual Studio, w związku z czym korzystanie z usługi Image Service w 2015 nie jest możliwe, ponieważ nie istnieje w poprzednich wersjach. Ta sekcja jest również dla Ciebie.

## <a name="scaling-up-images-that-are-too-small"></a>Skalowanie obrazów w górę zbyt małe
Obrazy, które są zbyt małe, mogą być skalowane i renderowane w interfejsach GDI i WPF przy użyciu niektórych typowych metod. Zarządzane klasy pomocnika DPI są dostępne dla wewnętrznych i zewnętrznych integratorów programu Visual Studio w celu rozróżnienia ikon skalowania, map bitowych, imagestrips i ImageList. Natywne pomocniki C/C + + usługi oparte na Win32 są dostępne do skalowania HICON, HBITMAP, HIMAGELIST i VsUI:: GdiplusImage. Skalowanie mapy bitowej zazwyczaj wymaga jednowierszowej zmiany po dołączeniu odwołania do biblioteki pomocnika. Na przykład:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Skalowanie listy ImageList zależy od tego, czy lista ImageList została zakończona w czasie ładowania, czy też jest dołączana w czasie wykonywania. Jeśli zakończysz w czasie ładowania, wywołaj `LogicalToDeviceUnits()` element ImageList jako mapę bitową. Gdy kod wymaga załadowania pojedynczej mapy bitowej przed złożeniem listy ImageList, pamiętaj o skalowaniu rozmiaru obrazu listy ImageList:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

W kodzie natywnym wymiary mogą być skalowane podczas tworzenia listy ImageList w następujący sposób:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funkcje w bibliotece umożliwiają określanie algorytmu zmiany rozmiarów. Podczas skalowania obrazów do umieszczenia w elementach ImageList upewnij się, że określono kolor tła, który jest używany do przezroczystości, lub użyj skalowania NearestNeighbor (co spowoduje zniekształcenia o 125% i 150%).

Zapoznaj się z <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dokumentacją w witrynie MSDN.

W poniższej tabeli przedstawiono przykłady sposobu skalowania obrazów w odpowiednich czynnikach skalowania DPI. Obrazy opisane w kolorze pomarańczowym oznaczają nasze najlepsze rozwiązanie w zakresie Visual Studio 2013 (skalowanie DPI o 100% 200%):

![Skalowanie problemów z DPI](../extensibility/media/dpi-issues-scaling.png "Skalowanie problemów z DPI")

## <a name="layout-issues"></a>Problemy z układem
Typowe problemy z układem można uniknąć przede wszystkim przez utrzymywanie punktów w interfejsie użytkownika, a nie przy użyciu lokalizacji bezwzględnych (w odniesieniu do jednostek pikseli). Na przykład:

- Położenie układu/tekstu musi być dostosowane do konta w przypadku obrazów skalowanych w górę.

- Kolumny w siatkach muszą mieć szerokość dopasowaną do skalowanego tekstu.

- Stałe kodowane rozmiary lub miejsca między elementami należy również skalować w górę. Rozmiary, które są oparte tylko na wymiarach tekstowych, są zwykle bardziej precyzyjne, ponieważ czcionki są skalowane automatycznie.

  Funkcje pomocnika są dostępne w <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> klasie, aby umożliwić skalowanie na osi X i Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkcje umożliwiają skalowanie na osi X/Y)

- spacja int = DpiHelper. LogicalToDeviceUnitsX (10);

- int Height = VsUI::D piHelper:: LogicalToDeviceUnitsY (5);

  Istnieją przeciążenia LogicalToDeviceUnits, aby umożliwić skalowanie obiektów, takich jak Rect, punkt i rozmiar.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Używanie biblioteki/klasy DPIHelper do skalowania obrazów i układu
Biblioteka pomocnika DPI programu Visual Studio jest dostępna w natywnych i zarządzanych formularzach i może być używana poza powłoką programu Visual Studio przez inne aplikacje.

Aby skorzystać z biblioteki, przejdź do [przykładów rozszerzalności programu Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) i Sklonuj przykład o wysokiej DPI_Images_Icons.

W polu pliki źródłowe Dołącz *VsUIDpiHelper. h* i Wywołaj statyczne funkcje `VsUI::DpiHelper` klasy:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Nie należy używać funkcji pomocnika w zmiennych statycznych na poziomie modułu lub klasy. Biblioteka używa także statycznych do synchronizacji wątków i może działać w przypadku problemów z inicjacją. Konwertuj te elementy statyczne na niestatyczne zmienne składowe lub Zapakuj je do funkcji (tak, aby były zbudowane przy pierwszym dostępie).

Aby uzyskać dostęp do funkcji pomocnika DPI z kodu zarządzanego, który będzie uruchamiany w środowisku programu Visual Studio:

- Projekt zużywający musi odwoływać się do najnowszej wersji powłoki shell MPF. Na przykład:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Upewnij się, że projekt zawiera odwołania do **System. Windows. Forms**, **'presentationcore**i **PresentationUI**.

- W kodzie, użyj przestrzeni nazw **Microsoft. VisualStudio. PlatformUI** i Wywołaj funkcje statyczne klasy DpiHelper. W przypadku obsługiwanych typów (punktów, rozmiarów, prostokątów itd.) dostępne są funkcje rozszerzenia, które zwracają nowe obiekty skalowane. Na przykład:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Obsługa obrazów WPF rozmycia w interfejsie użytkownika z powiększeniami
W programie WPF mapy bitowe są zmieniane automatycznie przez WPF dla bieżącego poziomu powiększenia DPI przy użyciu algorytmu wielosześciennego o wysokiej jakości (domyślnie), który dobrze sprawdza się w przypadku obrazów lub dużych zrzutów ekranu, ale jest nieodpowiedni dla ikon elementów menu, ponieważ wprowadza postrzegane rozmycia.

Mając

- W przypadku kompozycji obrazu logo i transparentów można <xref:System.Windows.Media.BitmapScalingMode> użyć domyślnego trybu zmiany rozmiarów.

- W przypadku elementów menu i obrazów iconography <xref:System.Windows.Media.BitmapScalingMode> należy użyć, gdy nie powoduje inne artefakty zniekształcenia, aby wyeliminować rozmycia (na 200% i 300%).

- W przypadku dużych poziomów powiększenia nie wielokrotności 100% (na przykład 250% lub 350%) skalowanie obrazów iconography z wynikami dwusześciennych w postaci rozmytego, wyskakującego interfejsu użytkownika. Lepszy wynik jest uzyskiwany przez pierwsze skalowanie obrazu z NearestNeighbor do największej wielokrotności 100% (na przykład 200% lub 300%) i skalowanie z tego miejsca. Zobacz przypadek specjalny: skalowanie obrazów WPF dla dużych poziomów DPI w celu uzyskania dodatkowych informacji.

  Klasa DpiHelper w przestrzeni nazw Microsoft. VisualStudio. PlatformUI zawiera element członkowski <xref:System.Windows.Media.BitmapScalingMode> , który może służyć do wiązania. Umożliwi to programowi Visual Studio Shell kontrolowanie trybu skalowania bitmapowego w całym produkcie, w zależności od współczynnika skalowania DPI.

  Aby używać go w języku XAML, Dodaj:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Powłoka programu Visual Studio już ustawia tę właściwość na oknach i oknach najwyższego poziomu. Interfejs użytkownika oparty na platformie WPF działający w programie Visual Studio będzie już dziedziczyć. Jeśli to ustawienie nie zostanie propagowane do określonych elementów interfejsu użytkownika, można je ustawić dla elementu głównego interfejsu użytkownika XAML/WPF. Miejsce, w którym się dzieje, obejmuje wyskakujące okienka, elementy z elementami nadrzędnymi Win32 i okna projektanta, które działają poza procesem, takie jak Blend.

Niektóre elementy interfejsu użytkownika można skalować niezależnie od poziomu powiększenia DPI ustawionego przez system, takiego jak edytor tekstu programu Visual Studio i projektantów opartych na platformie WPF (aplikacje klasyczne i Windows Store). W takich przypadkach nie należy używać DpiHelper. BitmapScalingMode. Aby rozwiązać ten problem w edytorze, zespół IDE utworzył właściwość niestandardową zatytułowaną RenderOptions. BitmapScalingMode. Ustaw tę wartość właściwości na HighQuality lub NearestNeighbor w zależności od połączonego poziomu powiększenia systemu i interfejsu użytkownika.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Przypadek specjalny: skalowanie obrazów WPF dla dużych poziomów DPI
Dla bardzo dużych poziomów powiększenia, które nie są wielokrotnością 100% (na przykład 250%, 350% itd.), skalowanie obrazów iconography z efektem dwusześciennym w postaci rozmytego i wyskakującego interfejsu użytkownika. Wrażenie tego obrazu obok wyraźnego tekstu jest niemal podobne jak w przypadku iluzji optycznej. Obrazy wyglądają tak, aby wyglądały bliżej oczu i nie skupić się w odniesieniu do tekstu. Wynik skalowania dla tego powiększonego rozmiaru można ulepszyć, naciskając najpierw skalowanie obrazu z NearestNeighbor do największej wielokrotności 100% (na przykład 200% lub 300%) i skalowanie z dwusześciennym do reszty (dodatkowy 50%).

Poniżej przedstawiono przykład różnic między wynikami, gdzie pierwszy obraz jest skalowany przy użyciu ulepszonego algorytmu podwójnego skalowania 100%->200%->250%, a drugi po prostu przy użyciu funkcji wielosześciennych 100%->250%.

![Przykład skalowania podwójnego rozdzielczości DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Przykład skalowania podwójnego rozdzielczości DPI")

Aby umożliwić interfejsowi użytkownika korzystanie z tego podwójnego skalowania, należy zmodyfikować znaczniki XAML do wyświetlania każdego elementu obrazu. W poniższych przykładach pokazano, jak używać podwójnego skalowania w WPF w programie Visual Studio przy użyciu biblioteki DpiHelper i powłoki. 12/14.

Krok 1. skalowanie obrazu do 200%, 300% i tak dalej przy użyciu NearestNeighbor.

Przeskaluj obraz do obrazu przy użyciu konwertera zastosowanego w powiązaniu lub z rozszerzeniem języka XAML. Na przykład:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Jeśli obraz również musi być motywem (większość, jeśli nie wszystkie, powinien), znacznik może użyć innego konwertera, który najpierw wykonuje motyw obrazu, a następnie wstępnie skalowanie. Znaczniki mogą używać <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> lub, w <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> zależności od żądanych danych wyjściowych konwersji.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Krok 2. upewnienie się, że rozmiar końcowy jest prawidłowy dla bieżącej wartości DPI.

Ponieważ WPF przeskaluje interfejs użytkownika dla bieżącej wartości DPI przy użyciu właściwości BitmapScalingMode ustawionej w UIElement, kontrolka obrazu korzystająca z obrazu ze zdjęciem ze skalowaniem będzie wyglądać na dwa lub trzy razy większe niż powinna. Poniżej przedstawiono kilka sposobów na przelicznik tego efektu:

- Jeśli znasz wymiar oryginalnego obrazu w 100%, możesz określić dokładny rozmiar kontrolki obraz. Rozmiary te odzwierciedlają rozmiar interfejsu użytkownika przed zastosowaniem skalowania.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Jeśli rozmiar oryginalnego obrazu nie jest znany, LayoutTransform może służyć do skalowania w dół obiektu obrazu końcowego. Na przykład:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Włączanie obsługi HDPI w WebOC
Domyślnie formanty WebOC (takie jak formant WebBrowser w WPF lub interfejs IWebBrowser2) nie umożliwiają wykrywania HDPI i obsługi. Wynik będzie osadzoną kontrolką z zawartością wyświetlaną, która jest zbyt mała na ekranie o wysokiej rozdzielczości. Poniżej opisano sposób włączania obsługi wysokiej rozdzielczości DPI w konkretnym wystąpieniu WebOC sieci Web.

Zaimplementuj interfejs IDocHostUIHandler (Zobacz artykuł MSDN w witrynie [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

Opcjonalnie Zaimplementuj interfejs ICustomDoc (Zobacz artykuł MSDN w witrynie [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Skojarz klasę implementującą IDocHostUIHandler z dokumentem WebOC. W przypadku zaimplementowania interfejsu ICustomDoc powyżej, gdy tylko Właściwość dokumentu WebOC jest prawidłowa, należy rzutować ją na ICustomDoc i wywołać metodę SetUIHandler, przekazując klasę implementującą IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Jeśli interfejs ICustomDoc nie został zaimplementowany, a dopiero wtedy, gdy właściwość dokumentu WebOC jest prawidłowa, należy ją rzutować na IOleObject i wywołać `SetClientSite` metodę, przekazując w klasie, która implementuje IDocHostUIHandler. Ustaw flagę DOCHOSTUIFLAG_DPI_AWARE na DOCHOSTUIINFO przekazaną do `GetHostInfo` wywołania metody:

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

Powinno to być wszystko, co należy zrobić, aby formant WebOC obsługiwał HPDI.

## <a name="tips"></a>Porady

1. Jeśli właściwość dokumentu w kontrolce WebOC ulegnie zmianie, może być konieczne ponowne skojarzenie dokumentu z klasą IDocHostUIHandler.

2. Jeśli powyższe nie działa, występuje znany problem z WebOC nie można pobrać zmiany flagi DPI. Najbardziej niezawodnym sposobem rozwiązania tego problemu jest przełączenie optycznego powiększenia WebOC, co oznacza, że dwa wywołania mają dwie różne wartości dla procentu powiększenia. Ponadto, jeśli to obejście jest wymagane, może być konieczne jego wykonanie na każdym wywołaniu nawigacji.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
