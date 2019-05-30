---
title: Adresowanie Problemy2 DPI | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2b440ff34a5c1f2c60b8874ba56266b636afde3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352262"
---
# <a name="address-dpi-issues"></a>Wartość DPI rozwiązywania problemów
Zwiększa liczbę urządzeń, które jest dostarczany z ekranami "o wysokiej rozdzielczości". Te ekrany, zwykle dokonują ponad 200 pikseli na cal (ppi). Korzystanie z aplikacji na tych komputerów będzie wymagać zawartości można skalować w do potrzeb wyświetlania zawartości w odległości normalnego widoku dla urządzenia. 2014 roku podstawowy cel wyświetlaczy o wysokiej gęstości są mobilni, urządzenia (tablety, laptopy clamshell i telefonów).

Windows 8.1 lub nowszy zawiera kilka funkcji, aby włączyć te maszyny pracować z Wyświetla i środowiska, w której komputer jest podłączony do obu o wysokiej gęstości i gęstość standardowa wyświetla się w tym samym czasie.

- Windows można umożliwiają Skaluj zawartość do urządzenia przy użyciu "Przechowuj tekst i inne elementy większy lub mniejszy" ustawienie (dostępny od Windows XP).

- Windows 8.1 lub nowszy jest automatycznie skalowany w zawartości w przypadku większości aplikacji były zgodne po przeniesieniu między wyświetla różne gęstości pikseli. Gdy ekran główny jest wysoka gęstość (200% skalowanie) i wyświetlanie dodatkowych jest gęstość standardowa (100%), Windows automatycznie skalowane wraz ze zawartość okna aplikacji w dół na ekranie dodatkowej (1 piksel wyświetlane dla każdego 4 pikseli renderowany przez Aplikacja).

- Windows jest domyślnie po prawej stronie skalowanie gęstość pikseli i wyświetlanie odległości ekranu (Windows 7 lub nowszy, można skonfigurować OEM).

- Windows może automatycznie skalować zawartość w górę do 250% na nowych urządzeniach, które przekraczają 280 ppi (począwszy od S14 Windows 8.1).

  Windows ma sposób postępowania z skalowanie w górę interfejsu użytkownika z zalet zwiększonej pikseli liczby. Aplikacja powoduje do tego systemu przez zadeklarowanie sam "systemu DPI aware". Aplikacje, które nie rób tego są skalowane w górę przez system. Może to spowodować, że środowisko użytkownika "rozmytego", gdzie całej aplikacji jest równomiernie rozciągnięte pikseli. Na przykład:

  ![DPI wystawia rozmyte](../extensibility/media/dpi-issues-fuzzy.png "DPI wystawia rozmytego")

  Program Visual Studio powoduje zasubskrybowanie trwa skalowanie obsługujących DPI i w związku z tym nie jest "zwirtualizowany."

  Windows (i programu Visual Studio) korzystać z kilku technologii interfejsu użytkownika, które mają różne sposoby radzenia sobie ze skalowaniem czynniki ustawiony przez system. Na przykład:

- WPF środki kontroli w sposób niezależny od urządzenia (jednostki, nie pikseli). WPF UI jest skalowana automatycznie w miarę potrzeby bieżącej DPI.

- Wszystkich rozmiarów tekstu, niezależnie od tego, w ramach interfejsu użytkownika są wyrażone w punktach i dlatego są traktowane przez system jako niezależne od rozdzielczości DPI. Tekst w Win32, WinForms, WPF już skalowanie w górę poprawnie podczas rysowania do urządzenia.

- Win32/WinForms okien dialogowych windows się włączenie układ, który zmienia rozmiar tekstu (na przykład za pomocą siatki, flow i panele układów tabeli). Włącz te, unikając lokalizacje ustaloną pikseli, które nie są skalowane przy zwiększa się rozmiary czcionek.

- Ikony udostępnianej przez system lub zasobów w oparciu metryki systemu (na przykład SM_CXICON i SM_CXSMICON) są już skalowany w górę.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starsze Win32 (GDI, GDI +) i interfejsu użytkownika opartego na WinForms
WPF już jest wysoka obsługującą ustawienia DPI, większość naszego kodu oparte na Win32/interfejsu GDI nie przewodnik pierwotnie został napisany z świadomości DPI na uwadze. Windows oferuje Skalowanie DPI z interfejsów API. Problemów z Win32 należy używać tych spójnego w ramach produktu. Program Visual Studio udostępnia pomocnika biblioteki klas, aby uniknąć duplikowania funkcjonalność i zapewnienie spójności w ramach produktu.

## <a name="high-resolution-images"></a>Obrazów w wysokiej rozdzielczości
Ta sekcja dotyczy przede wszystkim deweloperom rozszerzenie programu Visual Studio 2013. Dla programu Visual Studio 2015 za pomocą usługi obrazu, która jest wbudowana w program Visual Studio. Można również znaleźć czy musisz docelowa obsługę wielu wersji programu Visual Studio i w związku z tym korzystanie z usługi obrazu w 2015 r. nie jest opcją, ponieważ nie istnieje w poprzednich wersjach. W tej sekcji jest również dla Ciebie.

## <a name="scaling-up-images-that-are-too-small"></a>Skalowanie w górę obrazy, które są zbyt małe
Obrazy, które są zbyt małe, można przeskalować w górę i renderowania GDI i WPF za pomocą niektóre typowe metody. Klasy pomocnika DPI zarządzane są dostępne dla wewnętrznych i zewnętrznych integratorzy programu Visual Studio do skalowania, ikony, mapy bitowe, imagestrips i imagelists adresu. Oparte na Win32 macierzystego języka C / C ++ pomocników są dostępne dla skalowania HICON, HBITMAP i HIMAGELIST oraz VsUI::GdiplusImage. Skalowanie mapy bitowej zwykle wymaga tylko zmiana jednego wiersza po tym odwołanie do biblioteki pomocnika. Na przykład:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Skalowanie imagelist zależy od tego, czy imagelist zakończeniu w czasie ładowania lub jest dołączany w czasie wykonywania. Jeśli zakończone w czasie ładowania, należy wywołać `LogicalToDeviceUnits()` z listy obrazów, jak będzie mapy bitowej. Gdy kod musi załadować poszczególnych mapy bitowej przed redagowania imagelist, upewnij się, że skalowanie rozmiaru obrazów imagelist:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

W kodzie natywnym wymiary mogą być skalowane, tworząc imagelist w następujący sposób:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Zezwalaj na funkcje w bibliotece, Określanie algorytmu zmiany rozmiaru. Podczas skalowania obrazy mają być umieszczone w imagelists, upewnij się określić kolor tła używany dla przejrzystości lub użyj NearestNeighbor skalowania (co spowoduje zakłócenia w 125% i 150%).

Zapoznaj się z <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dokumentacji w witrynie MSDN.

W poniższej tabeli przedstawiono przykłady jak obrazy powinny być skalowana w taki sposób, w odpowiedniej rozdzielczości DPI czynnik skalowania. Obrazy opisane w kolorze pomarańczowym oznaczają naszych najlepszych praktyk, począwszy od programu Visual Studio 2013 (100 do 200% Skalowanie DPI):

![Skalowanie problemów z technologią DPI](../extensibility/media/dpi-issues-scaling.png "skalowanie problemów z technologią DPI")

## <a name="layout-issues"></a>Problemy z rozmieszczeniem
Typowe problemy z rozmieszczeniem można uniknąć przede wszystkim przez utrzymywanie punktów w interfejsie użytkownika, skalowania i względem siebie nawzajem, a nie przy użyciu bezwzględny lokalizacji (w szczególności w jednostkach pikseli). Na przykład:

- Układ i tekstu pozycji wymagane jest dostosowanie do konta w celu skalowania w górę obrazów.

- Kolumny w siatkach konieczne szerokości dostosowana tekstu skalowany w górę.

- Odstęp między elementami i zakodowanych rozmiarów będzie również trzeba skalowany w górę. Rozmiary oparte tylko na tekst wymiary są zazwyczaj odpowiedni, ponieważ czcionki są automatycznie skalowane w górę.

  Funkcje pomocnicze są dostępne w <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> klasy, aby umożliwić skalowanie na osi X i Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkcje zezwalają na skalowanie X / osi Y)

- miejsce int = DpiHelper.LogicalToDeviceUnitsX (10);

- wysokość int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Istnieją przeciążenia LogicalToDeviceUnits, aby zezwolić na skalowanie obiektów, takich jak prostokąt, pkt i rozmiaru.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Używanie klasy DPIHelper biblioteki/skalowanie obrazów i układ
Biblioteka pomocnicza DPI usługi Visual Studio jest dostępny w formularzach macierzystymi i zarządzanymi i mogą być używane poza Visual Studio shell przez inne aplikacje.

Korzystanie z biblioteki, przejdź do [przykłady rozszerzania programu Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) i sklonuj przykładowe DPI_Images_Icons wysoka.

W plikach źródłowych obejmują *VsUIDpiHelper.h* i wywołać funkcje statyczne `VsUI::DpiHelper` klasy:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Nie należy używać funkcji pomocnika modułu poziomie klasy lub statycznych zmiennych. Biblioteka również używa danych statycznych dla synchronizacji wątków i możesz napotkać problemy z zainicjowaniem zamówienia. Przekonwertuj te elementy statyczne zmienne Członkowskie Niestatyczne lub opakowywanie ich do funkcji (dzięki czemu mogą uzyskać skonstruowany na dostęp pierwszy).

Dostęp do funkcji pomocnika DPI z kodu zarządzanego, który będzie uruchamiany w środowisku Visual Studio:

- Projekt konsumencki musi odwoływać się najnowszą wersję MPF powłoki. Na przykład:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Upewnij się, projekt zawiera odwołania do **System.Windows.Forms**, **PresentationCore**, i **PresentationUI**.

- W kodzie, należy użyć **Microsoft.VisualStudio.PlatformUI** przestrzeni nazw i wywołanie statyczne funkcje DpiHelper klasy. Dla obsługiwanych typów (punkty, rozmiary, prostokąty i tak dalej) są dostarczane skalowana w funkcji rozszerzenia, które zwracają nowe obiekty. Na przykład:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Obsługa WPF rozmycia obrazu, którą można powiększać interfejsu użytkownika
W środowisku WPF mapy bitowe zmieniany jest rozmiar automatycznie przez WPF dla bieżącego poziomu powiększenia DPI przy użyciu algorytmu dwusześcienne wysokiej jakości (ustawienie domyślne), co sprawdza się w przypadku obrazów lub dużych zrzuty ekranu, ale jest nieodpowiedni dla ikony elementu menu, ponieważ wprowadza ona postrzegany rozmycia .

Zalecenia:

- Logo obrazu i banery kompozycji, domyślnie <xref:System.Windows.Media.BitmapScalingMode> zmiany rozmiaru w trybie może być używana.

- Elementy menu i obrazy nadruków <xref:System.Windows.Media.BitmapScalingMode> należy używać, gdy nie powoduje innych artefaktów zakłócenia wyeliminować rozmycia (w 200% i 300%).

- Dla dużych powiększenia poziomów nie wielokrotność 100%, (na przykład 250% lub 350%), skalowanie nadruków obrazów za pomocą dwusześcienne skutkuje rozmyte, rozmycia interfejsu użytkownika. Lepszy wynik uzyskany przez pierwszy skalowanie obrazu z NearestNeighbor do największych wielokrotność 100%, (na przykład 200% lub 300%) i skalowanie przy użyciu dwusześcienne z tego miejsca. Zobacz szczególny przypadek: prescaling obrazów WPF dla dużych DPI poziomy, aby uzyskać więcej informacji.

  Klasa DpiHelper w przestrzeni nazw Microsoft.VisualStudio.PlatformUI oferuje członka <xref:System.Windows.Media.BitmapScalingMode> które mogą być używane dla wiązania. Umożliwia powłoki programu Visual Studio do kontrolowania mapy bitowej tryb skalowania w produkcie jednolicie, w zależności od współczynnik skalowania DPI.

  Aby użyć go w XAML, należy dodać:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio shell już ustawia tę właściwość na okien najwyższego poziomu i okien dialogowych. Interfejsu użytkownika opartego na podsystemie WPF, uruchomiony w programie Visual Studio będzie już dziedziczyć go. Jeśli ustawienia nie są propagowane do figur konkretnego interfejsu użytkownika, można ustawić dla elementu głównego interfejsu użytkownika XAML/WPF. Miejsca, w którym dzieje się tak obejmują wyskakujące okienka w przypadku elementów z nadrzędnych Win32 i oknach projektantów, które są uruchamiane z przetwarzania, takich jak Blend.

Niektóre interfejsu użytkownika można skalować niezależnie od poziom powiększenia DPI zestaw systemu, takich jak edytor tekstu Visual Studio i opartego na podsystemie WPF Designer (pulpitu WPF i Windows Store). W takich przypadkach DpiHelper.BitmapScalingMode nie można używać. Aby rozwiązać ten problem w edytorze, zespół IDE, utworzono właściwość niestandardowa o nazwie RenderOptions.BitmapScalingMode. Wartość tej właściwości HighQuality lub NearestNeighbor w zależności od poziomu powiększenia połączonego systemu i interfejs użytkownika.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Szczególny przypadek: prescaling obrazów WPF dla dużych poziomów DPI
Poziomy powiększenia bardzo duże, które nie są wielokrotnością 100%, (na przykład 250%, 350% i tak dalej) skalowanie w nadruków obrazów z wynikami dwusześcienne rozmyte, rozmycia interfejsu użytkownika. Wrażenie obrazy te, wraz z wyraźny tekst prawie jest podobne do metody iluzji optycznego. Obrazy wydają się być bliżej okiem i poza fokus w odniesieniu do tekstu. Można zwiększyć skalowania wynik, w tym rozmiarze powiększony skalując pierwsze obraz z NearestNeighbor największych wielokrotności 100%, (na przykład 200% lub 300%) i skalowanie przy użyciu dwusześcienne do pozostałej (dodatkowe 50%).

Oto przykład różnice w wynikach, gdzie pierwszy obraz jest skalowany przy użyciu ulepszone algorytmu skalowania double-> 100% 200% -> 250% i drugi tylko z dwusześcienne 100% -> 250%.

![DPI problemy z podwójnym przykład skalowania](../extensibility/media/dpi-issues-double-scaling-example.png "DPI problemy z podwójnym przykład skalowania")

Aby włączyć interfejs użytkownika na potrzeby wyświetlania każdego elementu obrazu to skalowanie podwójnej precyzji, znaczników XAML będzie potrzeba jego zmodyfikowania. W poniższych przykładach pokazano, jak używać skalowania o podwójnej precyzji w WPF w programie Visual Studio przy użyciu biblioteki DpiHelper i Shell.12/14.

Krok 1. Prescale obraz, który ma 200%, 300% i tak dalej, za pomocą NearestNeighbor.

Prescale obraz za pomocą konwertera stosowane powiązania, czy rozszerzenie znaczników XAML. Na przykład:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Jeśli obraz musi być również motywem (większość, jeśli nie, powinny), znaczników można użyć konwertera innego, najpierw wykonującej motywów obrazu, a następnie wstępnie skalowania. Znaczników można użyć dowolnego <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> lub <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, w zależności od żądanej konwersji danych wyjściowych.

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

Krok 2. Upewnij się, że rozmiar końcowy jest prawidłowy dla bieżącego DPI.

Ponieważ WPF będzie się skalować interfejsu użytkownika dla bieżącego DPI, przy użyciu właściwości BitmapScalingMode nastavit UIElement kontrolkę typu obraz przy użyciu obrazu prescaled, zgodnie z jej źródła będzie wyglądać dwa lub trzy razy większy niż powinien. Poniżej przedstawiono kilka sposobów na licznika w tym celu:

- Jeśli znasz wymiaru oryginalny obraz w skali 100%, można określić dokładny rozmiar kontrolka obrazu. Te rozmiary zostanie naliczona, że rozmiar interfejsu użytkownika przed skalowaniem jest stosowany.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Jeśli rozmiar oryginalny obraz nie jest znany, LayoutTransform można skalować w dół końcowego obiektu obrazu. Na przykład:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Włączanie obsługi HDPI do obiektu
Domyślnie przez formanty obiektu (na przykład formantu WebBrowser w WPF lub interfejs IWebBrowser2) nie włączaj HDPI wykrywania i obsługi technicznej. Wynik będzie osadzonego formantu z zawartością wyświetlania, która jest zbyt mała w wysokiej rozdzielczości. Poniżej opisano sposób włączania obsługi wysokiej rozdzielczości DPI w wystąpieniu obiektu określonego w sieci web.

Implementuj interfejs IDocHostUIHandler (zobacz artykuł w witrynie MSDN w [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Opcjonalnie można zaimplementować interfejsu ICustomDoc (zobacz artykuł w witrynie MSDN w [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Kojarzenie klasy, która implementuje IDocHostUIHandler za pomocą obiektu dokumentu. Jeśli zaimplementowano interfejs ICustomDoc powyżej, następnie zaraz po właściwości dokumentu obiektu jest prawidłowa, go rzutować ICustomDoc i wywołać metodę SetUIHandler, przekazując klasę, która implementuje IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Jeśli użytkownik nie implementuje interfejsu ICustomDoc, a następnie jak obiektu dokumentu właściwość jest prawidłowa, należy go rzutować IOleObject i wywołania `SetClientSite` jest metoda w klasie, która implementuje IDocHostUIHandler. Ustaw flagę DOCHOSTUIFLAG_DPI_AWARE na DOCHOSTUIINFO przekazany do `GetHostInfo` wywołanie metody:

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

Powinna to być wszystkie opcje, które będzie konieczne uzyskanie kontroli nad obiektu do obsługi HPDI.

## <a name="tips"></a>Porady

1. Zmiana właściwości dokumentu w kontrolce obiektu może być konieczne ponowne kojarzenie dokumentu przy użyciu klasy IDocHostUIHandler.

2. Jeśli powyższe czynności zakończą się niepowodzeniem, jest to znany problem, za pomocą obiektu nie pobieranie zmiany flagi DPI. Jest najbardziej niezawodnym sposobem ustalenia, to aby przełączyć optyczne powiększenia obiektu, wywołań dwóch znaczenie w przypadku dwóch różnych wartości powiększenia. Ponadto jeśli to rozwiązanie jest wymagane, może być konieczne to wykonać w przypadku każdego wywołania Nawigacja.

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
