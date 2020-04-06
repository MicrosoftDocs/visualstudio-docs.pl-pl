---
title: Rozwiązywanie problemów z DPI2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740108"
---
# <a name="address-dpi-issues"></a>Rozwiązywanie problemów z dpi
Coraz więcej urządzeń jest wysyłanych z ekranami o wysokiej rozdzielczości. Ekrany te mają zazwyczaj ponad 200 pikseli na cal (ppi). Praca z aplikacją na tych komputerach będzie wymagać skalowania zawartości w celu zaspokojenia potrzeb wyświetlania zawartości w normalnej odległości wyświetlania urządzenia. Od 2014 r. głównym celem dla wyświetlaczy o wysokiej gęstości są mobilne urządzenia komputerowe (tablety, laptopy i telefony).

System Windows 8.1 i nowsze zawierają kilka funkcji umożliwiających pracę tych maszyn z wyświetlaczami i środowiskami, w których urządzenie jest jednocześnie podłączone do wyświetlaczy o wysokiej i standardowej gęstości.

- System Windows umożliwia skalowanie zawartości do urządzenia za pomocą ustawienia "Ustawianie tekstu i innych elementów większych lub mniejszych" (dostępne od systemu Windows XP).

- System Windows 8.1 lub nowsze automatycznie skaluje zawartość dla większości aplikacji, aby była spójna po przesunięciu między wyświetlaczami o różnej gęstości pikseli. Gdy ekran główny ma dużą gęstość (skalowanie 200%), a ekran pomocniczy to gęstość standardowa (100%), system Windows automatycznie przeskaluje zawartość okna aplikacji w dół na ekranie pomocniczym (1 piksel wyświetlany dla każdego 4 pikseli renderowanych przez aplikację).

- System Windows domyślnie skalowanie w prawo dla gęstości pikseli i odległości wyświetlania dla wyświetlacza (Windows 7 i wyższe, OEM konfigurowalne).

- System Windows może automatycznie skalować zawartość do 250% na nowych urządzeniach, które przekraczają 280 ppi (stan systemu Windows 8.1 S14).

  System Windows ma sposób radzenia sobie ze skalowaniem interfejsu użytkownika, aby skorzystać ze zwiększonej liczby pikseli. Aplikacja optuje do tego systemu, deklarując się jako "system DPI świadomy." Aplikacje, które tego nie robią, są skalowane w górę przez system. Może to spowodować "rozmyte" środowisko użytkownika, w którym cała aplikacja jest równomiernie rozciągnięta pikselami. Przykład:

  ![Dpi Problemy Rozmyte](../extensibility/media/dpi-issues-fuzzy.png "Dpi Problemy Rozmyte")

  Visual Studio decyduje się na skalowanie DPI-aware i dlatego nie jest "zwirtualizowane".

  System Windows (i Visual Studio) wykorzystują kilka technologii interfejsu użytkownika, które mają różne sposoby radzenia sobie z czynnikami skalowania ustawionymi przez system. Przykład:

- WPF WPF mierzy formanty w sposób niezależny od urządzenia (jednostki, a nie piksele). Interfejs użytkownika WPF automatycznie skaluje się w górę dla bieżącej rozdzielczości DPI.

- Wszystkie rozmiary tekstu, niezależnie od struktury interfejsu użytkownika są wyrażone w punktach, a więc są traktowane przez system jako dpi niezależne. Tekst w Win32, WinForms i WPF już skalowane poprawnie po narysowaniu do urządzenia wyświetlającego.

- Okna dialogowe i okna Win32/WinForms umożliwiają włączenie układu, który umożliwia rozmiar tekstu (na przykład za pośrednictwem paneli siatki, przepływu i układu tabeli). Umożliwiają one unikanie zakodowanych lokalizacji pikseli, które nie są skalowane po zwiększeniu rozmiarów czcionek.

- Ikony dostarczane przez system lub zasoby oparte na metrykach systemu (na przykład SM_CXICON i SM_CXSMICON) są już skalowane w górę.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starsze interfejsy użytkownika oparte na win32 (GDI, GDI+) i winforms
Chociaż WPF jest już wysoki DPI-aware, wiele z naszych Win32/GDI kod oparty nie został pierwotnie napisany z uwzględnieniem świadomości DPI. System Windows dostarczył interfejsy API skalowania DPI. Poprawki problemów z win32 należy używać tych konsekwentnie w całym produkcie. Visual Studio dostarczył bibliotekę klas pomocnika, aby uniknąć powielania funkcji i zapewnienia spójności w całym produkcie.

## <a name="high-resolution-images"></a>Obrazy o wysokiej rozdzielczości
Ta sekcja jest przede wszystkim dla deweloperów rozszerzenie programu Visual Studio 2013. W programie Visual Studio 2015 użyj usługi obrazów wbudowanej w program Visual Studio. Może się również okazać, że trzeba obsługiwać/kierować wiele wersji programu Visual Studio i dlatego przy użyciu usługi obrazu w 2015 r. nie jest opcją, ponieważ nie istnieje w poprzednich wersjach. Ta sekcja jest również dla Ciebie wtedy.

## <a name="scaling-up-images-that-are-too-small"></a>Skalowanie obrazów, które są zbyt małe
Obrazy, które są zbyt małe mogą być skalowane w górę i renderowane na GDI i WPF przy użyciu niektórych typowych metod. Zarządzane klasy pomocnika DPI są dostępne dla wewnętrznych i zewnętrznych integratorów programu Visual Studio w celu adresowania ikon skalowania, bitmap, pasów obrazów i list obrazów. Natywne pomocniki oparte na win32 C/C++są dostępne do skalowania HICON, HBITMAP, HIMAGELIST i VsUI::GdiplusImage. Skalowanie mapy bitowej zazwyczaj wymaga tylko zmiany jednowierszowej po uwzględnieniu odwołania do biblioteki pomocnika. Przykład:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Skalowanie listy obrazów zależy od tego, czy lista obrazów została ukończona w czasie ładowania, czy jest dołączana w czasie wykonywania. Jeśli zostanie ukończona `LogicalToDeviceUnits()` w czasie ładowania, zadzwoń z imagelistą tak, jak mapa bitowa. Gdy kod musi załadować pojedynczą mapę bitową przed złożeniem listy obrazów, upewnij się, że skaluje rozmiar obrazu listy obrazów:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

W kodzie macierzystym wymiary można skalować podczas tworzenia listy obrazów w następujący sposób:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funkcje w bibliotece umożliwiają określenie algorytmu zmiany rozmiaru. Podczas skalowania obrazów, które mają być umieszczone na listach obrazów, należy określić kolor tła, który jest używany do przezroczystości, lub użyj skalowania NearestNeighbor (co spowoduje zniekształcenia na poziomie 125% i 150%).

Zapoznaj <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> się z dokumentacją dotyczącą usługi MSDN.

W poniższej tabeli przedstawiono przykłady skalowania obrazów przy odpowiednich współczynnikach skalowania DPI. Obrazy opisane w kolorze pomarańczowym oznaczają nasze najlepsze rozwiązania dotyczące programu Visual Studio 2013 (skalowanie DPI w 100%-200%):

![Skalowanie problemów z dpi](../extensibility/media/dpi-issues-scaling.png "Skalowanie problemów z dpi")

## <a name="layout-issues"></a>Problemy z układem
Typowych problemów z układem można uniknąć przede wszystkim przez utrzymywanie punktów w interfejsie użytkownika skalowane i względem siebie, a nie przy użyciu lokalizacji bezwzględnych (w szczególności w jednostkach pikseli). Przykład:

- Pozycje układu/tekstu muszą być dostosowywane w celu uwzględnienia skalowane obrazy.

- Kolumny w siatkach muszą mieć szerokości dostosowane do skalowany tekst.

- Zakodowane rozmiary lub odstęp między elementami również będą musiały zostać powiększone. Rozmiary oparte tylko na wymiarach tekstowych są zazwyczaj wyświetlane, ponieważ czcionki są automatycznie skalowane w górę.

  Funkcje pomocnika są <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dostępne w klasie, aby umożliwić skalowanie na osi X i Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkcje umożliwiają skalowanie na osi X/Y)

- int spacja = DpiHelper.LogicalToDeviceUnitsX (10);

- wysokość int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Istnieją przeciążenia Jednostek Logicznych DoWydziawiczy, aby umożliwić skalowanie obiektów, takich jak Rect, Point i Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Używanie biblioteki/klasy DPIHelper do skalowania obrazów i układu
Biblioteka pomocnicza DPI programu Visual Studio jest dostępna w formularzach natywnych i zarządzanych i może być używana poza powłoką programu Visual Studio przez inne aplikacje.

Aby użyć biblioteki, przejdź do [przykładów rozszerzalności programu Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) i sklonuj przykład wysokiej DPI_Images_Icons.

W plikach źródłowych dołącz *VsUIDpiHelper.h* i `VsUI::DpiHelper` wywołaj funkcje statyczne klasy:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Nie należy używać funkcji pomocnika w zmiennych statycznych na poziomie modułu lub klasy. Biblioteka używa również statyki do synchronizacji wątków i może wystąpić problemy z inicjowaniem zamówienia. Konwertuj te statykę na niestatyczne zmienne członkowskie lub zawiń je w funkcję (aby zostały skonstruowane przy pierwszym dostępie).

Aby uzyskać dostęp do funkcji pomocnika DPI z kodu zarządzanego, który będzie uruchamiany w środowisku programu Visual Studio:

- Projekt zużywający musi odwoływać się do najnowszej wersji powłoki MPF. Przykład:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Upewnij się, że projekt ma odwołania do **System.Windows.Forms**, **PresentationCore**i **PresentationUI**.

- W kodzie użyj obszaru nazw **Microsoft.VisualStudio.PlatformUI** i wywołaj funkcje statyczne klasy DpiHelper. Dla obsługiwanych typów (punkty, rozmiary, prostokąty i tak dalej), istnieją funkcje rozszerzenia, które zwracają nowe skalowane obiekty. Przykład:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Radzenie sobie z wpfwą obrazu WPF w powiększalnym interfejsie użytkownika
W WPF, mapy bitowe są zmieniane automatycznie przez WPF dla bieżącego poziomu powiększenia DPI przy użyciu wysokiej jakości algorytm dwusześciowy (domyślnie), który działa dobrze dla obrazów lub dużych zrzutów ekranu, ale jest nieodpowiedni dla ikon elementów menu, ponieważ wprowadza postrzegane rozmycie.

Zalecenia:

- W przypadku grafiki obrazów i <xref:System.Windows.Media.BitmapScalingMode> banerów logo można użyć domyślnego trybu zmiany rozmiaru.

- W przypadku elementów menu <xref:System.Windows.Media.BitmapScalingMode> i obrazów ikonograficznych należy je używać, gdy nie powoduje to innych artefaktów zniekształceń w celu wyeliminowania rozmyć (na 200% i 300%).

- W przypadku dużych poziomów powiększenia, które nie są wielokrotnościami 100% (na przykład 250% lub 350%), skalowanie obrazów ikonografii za pomocą dwusześciennych wyników w rozmytym, wypranym interfejsie użytkownika. Lepszy wynik uzyskuje się przez pierwsze skalowanie obrazu z NearestNeighbor do największej wielokrotności 100% (na przykład 200% lub 300%) i skalowanie z dwusześcienne stamtąd. Zobacz przypadek specjalny: wstępne skalowanie obrazów WPF dla dużych poziomów DPI, aby uzyskać więcej informacji.

  Klasa DpiHelper w obszarze nazw Microsoft.VisualStudio.PlatformUI <xref:System.Windows.Media.BitmapScalingMode> udostępnia element członkowski, który może być używany do wiązania. Umożliwi to powłoki programu Visual Studio do kontrolowania trybu skalowania mapy bitowej w całym produkcie jednolicie, w zależności od współczynnika skalowania DPI.

  Aby użyć go w języku XAML, dodaj:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Powłoka programu Visual Studio już ustawia tę właściwość w oknach najwyższego poziomu i oknach dialogowych. Interfejs użytkownika oparty na programie WPF uruchomiony w programie Visual Studio będzie już dziedziczyć go. Jeśli ustawienie nie propaguje do określonych fragmentów interfejsu użytkownika, można ustawić na głównym elemencie interfejsu użytkownika XAML/WPF. Miejsca, w których tak się dzieje, obejmują wyskakujące okienka, elementy z elementami z elementami rzemiernymi Win32 i okna projektanta, których zabraknie w procesie, takie jak Mieszanie.

Niektóre interfejsu użytkownika można skalować niezależnie od poziomu powiększenia dpi zestawu systemu, takich jak edytor tekstu programu Visual Studio i projektantów opartych na WPF (WPF Desktop i Windows Store). W takich przypadkach DpiHelper.BitmapScalingMode nie należy używać. Aby rozwiązać ten problem w edytorze, zespół IDE utworzył niestandardową właściwość zatytułowaną RenderOptions.BitmapScalingMode. Ustaw tę wartość właściwości na HighQuality lub NearestNeighbor w zależności od połączonego poziomu powiększenia systemu i interfejsu użytkownika.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Przypadek szczególny: wstępne skalowanie obrazów WPF dla dużych poziomów DPI
W przypadku bardzo dużych poziomów powiększenia, które nie są wielokrotnością 100% (na przykład 250%, 350% itd.), skalowanie obrazów ikonografii za pomocą dwusześciennych powoduje rozmyte, wyprane interfejs użytkownika. Wrażenie tych obrazów obok wyraźnego tekstu jest prawie podobne do iluzji optycznej. Obrazy wydają się być bliżej oka i nieostema w stosunku do tekstu. Wynik skalowania przy tym powiększonym rozmiarze można poprawić, najpierw skalując obraz z NearestNeighbor do największej wielokrotności 100% (na przykład 200% lub 300%) i skalowanie z dwusześciennym do reszty (dodatkowe 50%).

Poniżej przedstawiono przykład różnic w wynikach, gdzie pierwszy obraz jest skalowany za pomocą ulepszonego algorytmu podwójnego skalowania 100%->200%->250%, a drugi tylko z dwusześciennym 100% ->250%.

![Dpi problemy podwójne skalowanie przykład](../extensibility/media/dpi-issues-double-scaling-example.png "Dpi problemy podwójne skalowanie przykład")

Aby umożliwić interfejs użytkownika do korzystania z tego podwójnego skalowania, znaczników XAML do wyświetlania każdego elementu image będą musiały zostać zmodyfikowane. Poniższe przykłady pokazują, jak używać podwójnego skalowania w programie WPF w programie Visual Studio przy użyciu biblioteki DpiHelper i Shell.12/14.

Krok 1: Wstępnie skaluj obraz do 200%, 300% i tak dalej, używając NearestNeighbor.

Wstępnie skaluj obraz przy użyciu konwertera zastosowanego do powiązania lub rozszerzenia znaczników XAML. Przykład:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Jeśli obraz musi być również tematyce (większość, jeśli nie wszystkie, powinny), znaczników można użyć innego konwertera, który najpierw nie motywowania obrazu, a następnie wstępnego skalowania. Znaczników można użyć <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> albo <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>lub , w zależności od żądanego wyjścia konwersji.

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

Krok 2: Upewnij się, że ostateczny rozmiar jest poprawny dla bieżącej rozdzielczości DPI.

Ponieważ WPFWpf będzie skalować interfejsu użytkownika dla bieżącego DPI przy użyciu BitmapScalingMode właściwości ustawionej na UIElement, Image kontroli przy użyciu wstępnie skalowany obraz jako jego źródło będzie wyglądać dwa lub trzy razy większe niż powinno. Oto kilka sposobów przeciwdziałania temu efektowi:

- Jeśli znasz wymiar oryginalnego obrazu na 100%, możesz określić dokładny rozmiar formantu Obraz. Te rozmiary będą odzwierciedlać rozmiar interfejsu użytkownika przed zastosowaniem skalowania.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Jeśli rozmiar oryginalnego obrazu nie jest znany, LayoutTransform może służyć do skalowania w dół końcowego Image obiektu. Przykład:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Włączanie obsługi interfejsu HDPI w sieci WebOC
Domyślnie formanty WebOC (takie jak kontrolka WebBrowser w WPF lub interfejs IWebBrowser2) nie umożliwiają wykrywania i obsługi HDPI. Rezultatem będzie wbudowany formant z zawartością wyświetlania, która jest zbyt mała na wyświetlaczu o wysokiej rozdzielczości. Poniżej opisano sposób włączania obsługi wysokiej rozdzielczości DPI w określonym wystąpieniu weboc.

Implementowanie interfejsu IDocHostUIHandler (zobacz artykuł MSDN na [IDocHostUIHandler:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))

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

Opcjonalnie zaimplementuj interfejs ICustomDoc (zobacz artykuł MSDN na [ICustomDoc:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Skojarz klasę, która implementuje IDocHostUIHandler z dokumentem WebOC. Jeśli zaimplementowano interfejs ICustomDoc powyżej, a następnie tak szybko, jak właściwość dokumentu WebOC jest prawidłowa, przerzucać go do ICustomDoc i wywołać SetUIHandler metody, przekazując klasę, która implementuje IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Jeśli nie zaimplementowano interfejsu ICustomDoc, a następnie tak szybko, jak właściwość dokumentu WebOC jest prawidłowa, `SetClientSite` należy przerzucić go do IOleObject i wywołać metodę, przekazując w klasie, która implementuje IDocHostUIHandler. Ustaw flagę DOCHOSTUIFLAG_DPI_AWARE na DOCHOSTUIINFO przekazany `GetHostInfo` do wywołania metody:

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

Powinno to być wszystko, czego potrzebujesz, aby uzyskać kontrolę WebOC do obsługi HPDI.

## <a name="tips"></a>Porady

1. Jeśli właściwość dokumentu w formancie WebOC ulegnie zmianie, może być konieczne ponowne przyłączenie dokumentu za pomocą klasy IDocHostUIHandler.

2. Jeśli powyższe nie działa, istnieje znany problem z WebOC nie podnoszenia zmiany do flagi DPI. Najbardziej niezawodnym sposobem naprawienia tego problemu jest przełączenie zoomu optycznego WebOC, co oznacza dwa wywołania z dwiema różnymi wartościami dla procentu powiększenia. Ponadto jeśli to obejście jest wymagane, może być konieczne wykonanie go przy każdym wywołaniu nawigacji.

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
