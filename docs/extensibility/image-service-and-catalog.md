---
title: Usługa i katalog obrazów | Dokumenty firmy Microsoft
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710388"
---
# <a name="image-service-and-catalog"></a>Usługa i katalog obrazów
Ta książka kucharska zawiera wskazówki i najlepsze rozwiązania dotyczące wdrażania usługi obrazów programu Visual Studio i wykazu obrazów wprowadzonych w programie Visual Studio 2015.

 Usługa obrazów wprowadzona w programie Visual Studio 2015 umożliwia deweloperom uzyskanie najlepszych obrazów dla urządzenia i wybranego motywu użytkownika do wyświetlenia obrazu, w tym poprawnej kompozycji kontekstu, w którym są wyświetlane. Przyjęcie usługi obrazu pomoże wyeliminować główne punkty bólu związane z konserwacją zasobów, skalowaniem HDPI i motywami.

|||
|-|-|
|**Problemy dzisiaj**|**Rozwiązania**|
|Mieszanie kolorów tła|Wbudowane mieszanie alfa|
|Tematy (niektóre) obrazy|Metadane motywu|
|Tryb wysokiego kontrastu|Alternatywne zasoby o wysokim kontraście|
|Potrzebujesz wielu zasobów dla różnych trybów DPI|Wybieralne zasoby z rezerwą opartą na wektorach|
|Duplikowanie obrazów|Jeden identyfikator na koncepcję obrazu|

 Dlaczego warto przyjąć usługę obrazu?

- Zawsze otrzymuj najnowszy obraz "pixel-perfect" z programu Visual Studio

- Możesz przesyłać i używać własnych obrazów

- Nie ma potrzeby testowania obrazów, gdy system Windows dodaje nowe skalowanie DPI

- Rozwiązywanie starych przeszkód architektonicznych w implementacjach

  Pasek narzędzi powłoki programu Visual Studio przed i po użyciu usługi obrazu:

  ![Usługa obrazowania przed i po](../extensibility/media/image-service-before-and-after.png "Usługa obrazowania przed i po")

## <a name="how-it-works"></a>Jak to działa
 Usługa obrazu może dostarczyć obraz bitmapowy odpowiedni dla każdej obsługiwanej struktury interfejsu użytkownika:

- WPFWPF: Źródło mapy bitowej

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagram przepływu usługi obrazów

  ![Diagram przepływu usługi obrazu](../extensibility/media/image-service-flow-diagram.png "Diagram przepływu usługi obrazu")

  **Monikery obrazów**

  Moniker obrazu (lub w skrócie moniker) to para identyfikatorów GUID/ID, która jednoznacznie identyfikuje zasób obrazu lub zasób listy obrazów w bibliotece obrazów.

  **Znane monikery**

  Zestaw monikerów obrazów zawartych w wykazie obrazów programu Visual Studio i publicznie zużywanych przez dowolny składnik lub rozszerzenie programu Visual Studio.

  **Pliki manifestu obrazu**

  Manifest obrazu *(.imagemanifest)* pliki są pliki XML, które definiują zestaw zasobów obrazu, monikers, które reprezentują te zasoby i rzeczywisty obraz lub obrazy, które reprezentują każdy zasób. Manifesty obrazów można zdefiniować autonomiczne obrazy lub listy obrazów dla obsługi starszego interfejsu użytkownika. Ponadto istnieją atrybuty, które można ustawić na zasobie lub na poszczególnych obrazów za każdego zasobu, aby zmienić, kiedy i jak te zasoby są wyświetlane.

  **Schemat manifestu obrazu**

  Pełny manifest obrazu wygląda następująco:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbole**

 Jako pomoc w zakresie czytelności i konserwacji manifest obrazu może używać symboli dla wartości atrybutów. Symbole są zdefiniowane w ten sposób:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Podelement**|**Definicja**|
|Import|Importuje symbole danego pliku manifestu do użycia w bieżącym manifeście|
|Guid (identyfikator GUID)|Symbol reprezentuje identyfikator GUID i musi być zgodny z formatowaniem guid|
|ID|Symbol reprezentuje identyfikator i musi być nieujemną całkowitej liczby|
|Ciąg|Symbol reprezentuje dowolną wartość ciągu|

 W symbolach rozróżniana jest wielkość liter i odwołuje się do niego przy użyciu składni $(nazwa symbolu):Symbols are case-sensitive, and referenced using $(symbol-name) składna:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one służyć w uri atrybut \<Source> lub \<Import> element do ścieżek odwołania na komputerze lokalnym.

|||
|-|-|
|**Symbol**|**Opis**|
|Pliki commonprogramowe|Wartość zmiennej środowiskowej %CommonProgramFiles%|
|Localappdata|Wartość zmiennej środowiskowej %LocalAppData%|
|ManifestFolder|Folder zawierający plik manifestu|
|Mydocuments|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej %ProgramFiles%|
|System|Folder *Windows\System32*|
|Windir|Wartość zmiennej środowiskowej %WinDir%|

 **Image (Obraz)**

 Element \<Image> definiuje obraz, do którego można się odwoływać za pomocą monikera. Identyfikator GUID i identyfikator razem tworzą moniker obrazu. Moniker obrazu musi być unikatowy w całej bibliotece obrazów. Jeśli więcej niż jeden obraz ma dany pseudonim, pierwszy napotkany podczas tworzenia biblioteki jest tym, który jest zachowywany.

 Musi zawierać co najmniej jedno źródło. Źródła neutralne pod względem rozmiaru dadzą najlepsze wyniki w szerokim zakresie rozmiarów, ale nie są one wymagane. Jeśli usługa jest proszona o obraz o \<rozmiarze nie zdefiniowanym w Image> element i nie ma źródła neutralnego pod względem rozmiaru, usługa wybierze najlepsze źródło specyficzne dla rozmiaru i skaluje go do żądanego rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid (identyfikator GUID)|[Wymagane] Część guid moniker obrazu|
|ID|[Wymagane] Część identyfikatora moniker obrazu|
|AllowColorInversion (Zezwalaj kolorowainwersja)|[Opcjonalnie, domyślna wartość true] Wskazuje, czy obraz może mieć swoje kolory programowo odwrócone, gdy jest używany na ciemnym tle.|

 **Źródła**

 Element \<Source> definiuje pojedynczy zasób źródłowy obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Identyfikator uri|[Wymagane] Identyfikator URI, który definiuje, gdzie obraz może być ładowany z. Może to być jedna z następujących czynności:<br /><br /> - Identyfikator [URI pakietu](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) przy użyciu application:/// urzędu<br />- Odwołanie do zasobu komponentu bezwzględnego<br />- Ścieżka do pliku zawierającego zasób macierzysty|
|Tło|[Opcjonalnie] Wskazuje, co na rodzaju tła źródło jest przeznaczone do użycia.<br /><br /> Może to być jedna z następujących czynności:<br /><br /> *Światło:* Źródło może być używane na jasnym tle.<br /><br /> *Ciemny:* Źródło może być używane na ciemnym tle.<br /><br /> *WysokiKontrast:* Źródło może być używane na dowolnym tle w trybie wysokiego kontrastu.<br /><br /> *HighContrastLight:* Źródło może być używane na jasnym tle w trybie wysokiego kontrastu.<br /><br /> *WysokiContrastDark:* Źródło może być używane na ciemnym tle w trybie wysokiego kontrastu.<br /><br /> Jeśli atrybut Background zostanie pominięty, źródło może być używane na dowolnym tle.<br /><br /> Jeśli tło jest *Jasne,* *Ciemne,* *HighContrastLight*lub *HighContrastDark*, kolory źródła nigdy nie są odwrócone. Jeśli tło zostanie pominięte lub ustawione na *HighContrast*, inwersja kolorów źródła jest kontrolowana przez atrybut **AllowColorInversion** obrazu.|

Element \<source> może mieć dokładnie jedną z następujących opcjonalnych podelementów:

||||
|-|-|-|
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|\<Rozmiar>|Wartość|Źródło będzie używane do obrazów o danym rozmiarze (w jednostkach urządzenia). Obraz będzie kwadratowy.|
|\<> SizeRange|MinSize, MaxSize|Źródło będzie używane dla obrazów z MinSize do MaxSize (w jednostkach urządzenia) włącznie. Obraz będzie kwadratowy.|
|\<Wymiary>|Szerokość, Wysokość|Źródło będzie używane do obrazów o danej szerokości i wysokości (w jednostkach urządzenia).|
|\<> DimensionRange|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie używane dla obrazów od minimalnej szerokości/wysokości do maksymalnej szerokości/wysokości (w jednostkach urządzenia) włącznie.|

 A \<Source> element może również \<mieć opcjonalne NativeResource> podelement, który definiuje \<Source>, który jest ładowany z zestawu macierzystego, a nie zestawu zarządzanego.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Typ|[Wymagane] Typ zasobu macierzystego, XAML lub PNG|
|ID|[Wymagane] Część identyfikatora liczby całkowitej zasobu macierzystego|

 **Imagelist**

 ImageList \<> element definiuje kolekcję obrazów, które mogą być zwracane w jednym pasku. Taśma jest zbudowana na żądanie, w razie potrzeby.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Guid (identyfikator GUID)|[Wymagane] Część guid moniker obrazu|
|ID|[Wymagane] Część identyfikatora moniker obrazu|
|Zewnętrzna|[Opcjonalnie, domyślnie false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker dla zawartego obrazu nie musi odwoływać się do obrazu zdefiniowanego w bieżącym manifeście. Jeśli nie można znaleźć zawartego obrazu w bibliotece obrazów, w jego miejscu zostanie użyty pusty obraz zastępczy.

## <a name="using-the-image-service"></a>Korzystanie z usługi obrazów

### <a name="first-steps-managed"></a>Pierwsze kroki (zarządzane)
 Aby korzystać z usługi obrazów, należy dodać odwołania do niektórych lub wszystkich następujących zestawów do projektu:

- *Plik Microsoft.VisualStudio.ImageCatalog.dll*

  - Wymagane, jeśli używasz wbudowanego katalogu obrazów **KnownMonikers**.

- *Plik Microsoft.VisualStudio.Imaging.dll*

  - Wymagane, jeśli używasz **CrispImage** i **ImageTheming Narzędzia** w interfejsie użytkownika WPF.

- *Plik Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Wymagane, jeśli używasz **ImageMoniker** i **ImageAttributes** typów.

  - **BedInteropTypes** powinny być ustawione na true.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Wymagane, jeśli używasz **typu IVsImageService2.**

  - **BedInteropTypes** powinny być ustawione na true.

- *Plik Microsoft.VisualStudio.Utilities.dll*

  - Wymagane, jeśli używasz **BrushToColorConverter** dla **ImageThemingUtilities.ImageBackgroundColor** w interfejsie użytkownika WPF.

- *Microsoft.VisualStudio.Shell. \<VSVersion>,0*

  - Wymagane, jeśli używasz **typu IVsUIObject.**

- *Plik Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Wymagane, jeśli używasz pomocników interfejsu użytkownika związanych z WinForms.

  - **BedInteropTypes** powinien być ustawiony na true

### <a name="first-steps-native"></a>Pierwsze kroki (natywne)
 Aby korzystać z usługi obrazów, należy dołączyć do projektu niektóre lub wszystkie z następujących nagłówków:

- **ZnaneImageIds.h**

  - Wymagane, jeśli używasz wbudowanego katalogu obrazów **KnownMonikers**, ale nie można użyć **ImageMoniker** typu, takich jak podczas zwracania wartości z **IVsHierarchy GetGuidProperty** lub **GetProperty** wywołań.

- **ZnaneMonikers.h**

  - Wymagane, jeśli używasz wbudowanego katalogu obrazów **KnownMonikers**.

- **ImageParameters140.h**

  - Wymagane, jeśli używasz **ImageMoniker** i **ImageAttributes** typów.

- **vsShell140.h**

  - Wymagane, jeśli używasz **typu IVsImageService2.**

- **ImageThemingUtilities.h**

  - Wymagane, jeśli nie można pozwolić, aby usługa obrazów obsługiwała motywy za Ciebie.

  - Nie należy używać tego nagłówka, jeśli usługa obrazów może obsługiwać motywy obrazu.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Wymagane, jeśli używasz pomocników DPI, aby uzyskać bieżącą rozdzielczość DPI.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Wymagane, jeśli używasz pomocników świadomości DPI, aby uzyskać bieżącą rozdzielczość DPI.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Jak napisać nowy interfejs użytkownika WPF?

1. Rozpocznij od dodania odwołań do zestawu wymaganych w powyższej sekcji pierwsze kroki do projektu. Nie musisz dodawać wszystkich z nich, więc dodaj tylko potrzebne odwołania. (Uwaga: jeśli używasz lub masz dostęp do **kolorów** zamiast **pędzli,** możesz pominąć odwołanie do **narzędzi,** ponieważ nie będziesz potrzebować konwertera).)

2. Wybierz żądany obraz i uzyskaj jego moniker. Użyj **KnownMoniker**, lub użyć własnego, jeśli masz własne niestandardowe obrazy i monikers.

3. Dodaj **CrispImages** do swojego XAML. (Zobacz poniższy przykład).

4. Ustaw **ImageThemingUtilities.ImageBackgroundColor** właściwość w hierarchii interfejsu użytkownika. (Należy to ustawić w miejscu, w którym kolor tła jest znany, niekoniecznie na **CrispImage**.) (Zobacz poniższy przykład).

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Jak zaktualizować istniejący interfejs użytkownika WPF?**

 Aktualizowanie istniejącego interfejsu użytkownika WPF jest stosunkowo prostym procesem, który składa się z trzech podstawowych kroków:

1. Zastąp wszystkie \<elementy> obrazu \<w interfejsie użytkownika elementami> CrispImage.

2. Zmień wszystkie atrybuty Źródło na Atrybuty Moniker.

    - Jeśli obraz nigdy się nie zmieni i używasz **ZnaneMonikers**, a następnie statycznie powiązać tę właściwość **do KnownMoniker**. (Zobacz powyższy przykład).

    - Jeśli obraz nigdy się nie zmieni i używasz własnego obrazu niestandardowego, statycznie powiązać z własnym pseudonimem.

    - Jeśli obraz można zmienić, powiązać atrybut Moniker do właściwości kodu, który powiadamia o zmianach właściwości.

3. Gdzieś w hierarchii interfejsu użytkownika, ustaw **ImageThemingUtilities.ImageBackgroundColor,** aby upewnić się, że inwersja kolorów działa poprawnie.

    - Może to wymagać użycia **BrushToColorConverter** klasy. (Zobacz powyższy przykład).

## <a name="how-do-i-update-win32-ui"></a>Jak zaktualizować interfejs użytkownika systemu Win32?
 W razie potrzeby dodaj do kodu następujące elementy, aby zastąpić nieprzetworzone ładowanie obrazów. W razie potrzeby przełącz wartości dla zwracania HBITMAPs w porównaniu z HICON versus HIMAGELIST.

 **Pobierz usługę obrazów**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Żądanie obrazu**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Jak zaktualizować interfejs użytkownika systemu WinForms?
 W razie potrzeby dodaj do kodu następujące elementy, aby zastąpić nieprzetworzone ładowanie obrazów. W razie potrzeby przełącz wartości do zwracania map bitowych i ikon.

 **Pomocne użycie instrukcji**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Pobierz usługę obrazów**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Poproś o obraz**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak korzystać z monikerów obrazów w nowym oknie narzędzi?
 Szablon projektu pakietu VSIX został zaktualizowany dla programu Visual Studio 2015. Aby utworzyć nowe okno narzędzia, kliknij prawym przyciskiem myszy projekt VSIX i wybierz polecenie **Dodaj** > **nowy element** (**Ctrl**+**Shift**+**A**). W węźle Rozszerzalność języka projektu wybierz pozycję **Okno narzędzia niestandardowego**, nadaj okno narzędzia nazwę i naciśnij przycisk **Dodaj.**

 Są to kluczowe miejsca do korzystania z monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:

1. Karta okna narzędzia, gdy karty stają się wystarczająco małe (używane również w przełączniku okna**karty** **Ctrl).**+

    Dodaj ten wiersz do konstruktora dla klasy, która wywodzi się z **typu ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Polecenie otwierania okna narzędzia.

    W pliku *vsct* pakietu edytuj przycisk polecenia okna narzędzia:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Jak korzystać z monikerów obrazów w istniejącym oknie narzędzi?**

   Aktualizowanie istniejącego okna narzędzia w celu użycia monikerów obrazów jest podobne do kroków tworzenia nowego okna narzędzia.

   Są to kluczowe miejsca do korzystania z monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:

3. Karta okna narzędzia, gdy karty stają się wystarczająco małe (używane również w przełączniku okna**karty** **Ctrl).**+

   1. Usuń te wiersze (jeśli istnieją) w konstruktorze dla klasy, która wywodzi się z **typu ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Zobacz krok #1 "Jak używać monikerów obrazów w nowym oknie narzędzia?" w powyższej części.

4. Polecenie otwierania okna narzędzia.

   - Zobacz krok #2 "Jak używać monikerów obrazów w nowym oknie narzędzia?" w powyższej części.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Jak korzystać z monikerów obrazów w pliku vsct?
 Zaktualizuj plik *vsct* zgodnie z poniższymi wierszami:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Co zrobić, jeśli mój plik vsct również musi być odczytywany przez starsze wersje programu Visual Studio?**

 Starsze wersje programu Visual Studio nie rozpoznają **iconIsMoniker** flagi polecenia. Obrazów z usługi obrazów można używać w wersjach programu Visual Studio, które go obsługują, ale nadal używać obrazów starego stylu w starszych wersjach programu Visual Studio. Aby to zrobić, należy pozostawić plik *.vsct* bez zmian (i dlatego zgodne ze starszymi wersjami programu Visual Studio) i utworzyć plik CSV (wartości oddzielone przecinkami) plik, który mapuje z par GUID/ID zdefiniowanych w pliku *vsct* \<Bitmaps> element do para identyfikatora GUID/ID identyfikatora obrazu.

 Format pliku CSV mapowania jest:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Plik CSV jest wdrażany z pakietem, a jego lokalizacja jest określona przez właściwość **IconMappingFilename** **atrybutu ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** jest ścieżką względną niejawnie zakorzenioną w $PackageFolder$ (jak w powyższym przykładzie) lub ścieżką bezwzględną jawnie zakorzenioną w katalogu zdefiniowanym przez zmienną środowiskową, taką jak *@"%UserProfile%\dir1\dir2\MyMappingFile.csv."*.

## <a name="how-do-i-port-a-project-system"></a>Jak przenieść system projektu?
 **Jak dostarczyć ImageMonikers dla projektu**

1. Zaimplementuj **VSHPROPID_SupportsIconMonikers** na **iVsHierarchy**projektu i powrót prawda.

2. Zaimplementuj **VSHPROPID_IconMonikerImageList** (jeśli oryginalny projekt użyto **VSHPROPID_IconImgList)** lub **VSHPROPID_IconMonikerGuid** **, VSHPROPID_IconMonikerId,** **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (jeśli oryginalny projekt używany **VSHPROPID_IconHandle** i **VSHPROPID_OpenFolderIconHandle**).

3. Zmień implementację oryginalnych VSHPROPIDs dla ikon, aby utworzyć "starsze" wersje ikon, jeśli punkty rozszerzeń zażądają ich. **IVsImageService2** zapewnia funkcjonalność niezbędną do uzyskania tych ikon

   **Dodatkowe wymagania dotyczące smaków projektów VB/C#**

   Zaimplementuj **VSHPROPID_SupportsIconMonikers** tylko wtedy, gdy wykryjesz, że projekt jest **najbardziej oddalony.** W przeciwnym razie rzeczywisty smak zewnętrzny może nie obsługiwać monikerów obrazu w rzeczywistości, a twój podstawowy smak może skutecznie "ukryć" niestandardowe obrazy.

   **Jak korzystać z monikerów obrazów w CPS?**

   Ustawienie obrazów niestandardowych w programie CPS (Common Project System) można wykonać ręcznie lub za pomocą szablonu elementu, który jest dostarczany z sdk rozszerzalnością systemu projektu.

   **Korzystanie z sdk rozszerzalności systemu projektu**

   Postępuj zgodnie z instrukcjami podanymi w [witrynie Podaj niestandardowe ikony typu/elementu projektu,](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) aby dostosować obrazy CPS. Więcej informacji na temat CPS można znaleźć w [dokumentacji rozszerzalności systemu Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem)

   **Ręcznie użyj ImageMonikers**

4. Implementowanie i eksportowanie interfejsu **IProjectTreeModifier** w systemie projektu.

5. Określ, którego **pseudonimu KnownMoniker** lub niestandardowego obrazu chcesz użyć.

6. W **ApplyModifications** metody, wykonaj następujące gdzieś w metodzie przed zwróceniem nowego drzewa, podobnie jak w poniższym przykładzie:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Jeśli tworzysz nowe drzewo, możesz ustawić obrazy niestandardowe, przekazując żądane monikery do metody NewTree, podobnie jak w poniższym przykładzie:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak przekonwertować z prawdziwego paska obrazu na pasek obrazu oparty na moniku?
 **Muszę wspierać HIMAGELISTs**

 Jeśli istnieje już istniejący pasek obrazu dla kodu, który chcesz zaktualizować, aby korzystać z usługi obrazów, ale są ograniczone przez interfejsy API, które wymagają przekazywania wokół list obrazów, nadal można uzyskać korzyści z usługi obrazu. Aby utworzyć pasek obrazu oparty na moniku, wykonaj poniższe czynności, aby utworzyć manifest z istniejących monikerów.

1. Uruchom **Narzędzie ManifestFromResources,** przekazując go paskiem obrazu. Spowoduje to wygenerowanie manifestu dla paska.

   - Zalecane: podaj domyślną nazwę manifestu, aby dopasować go do użycia.

2. Jeśli używasz tylko **ZnaneMonikers**, a następnie wykonaj następujące czynności:

   - Zastąp sekcję \<Obrazy> \<manifestu obrazami na obrazy/>.

   - Usuń wszystkie identyfikatory podrzędne (wszystko \<z nazwą imagestrip>_##).

   - Zalecane: zmień nazwę symbolu AssetsGuid i symbolu paska obrazu zgodnie z jego użyciem.

   - Zastąp każdy identyfikator GUID **ContainedImage**na $(ImageCatalogGuid), zastąp\<każdy identyfikator **ContainedImage**na $( moniker>) i dodaj atrybut External="true" do każdego **containedImage**

       - \<moniker> powinien zostać zastąpiony **znanymoniker,** który pasuje do obrazu, ale z "KnownMonikers". usunięte z nazwy.

   - Dodaj <Manifest\\ importu="$(ManifestFolder)<Ścieżka dir instalacji\>względnej do * \Microsoft.VisualStudio.ImageCatalog.imagemanifest"\* / \<> do górnej części sekcji Symbole>.

       - Ścieżka względna jest określana przez lokalizację wdrożenia zdefiniowaną w ustawieniach tworzenia manifestu.

3. Uruchom **Narzędzie ManifestToCode** do generowania otoki, tak aby istniejący kod ma moniker, którego można użyć do kwerendy usługi obrazu dla paska obrazu.

   - Zalecane: podaj nazwy niedefault dla otoki i przestrzenie nazw, aby dopasować ich użycie.

4. Wykonaj wszystkie dodaje, tworzenie/wdrażanie konfiguracji i inne zmiany kodu do pracy z usługą obrazu i nowych plików.

   Przykładowy manifest, w tym obrazy wewnętrzne i zewnętrzne, aby zobaczyć, jak powinien wyglądać:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Nie muszę wspierać HIMAGELISTs**

1. Określ zestaw **znanych wyszukiwarek,** które pasują do obrazów w pasku obrazu, lub utwórz własne monikery dla obrazów w pasku obrazu.

2. Zaktualizuj mapowanie używane do uzyskania obrazu w wymaganym indeksie w pasku obrazu, aby zamiast tego użyć monikerów.

3. Zaktualizuj kod, aby użyć usługi obrazów, aby zażądać monikerów za pomocą zaktualizowanego mapowania. (Może to oznaczać aktualizację do **CrispImages** dla kodu zarządzanego lub żądanie HBITMAPs lub HICONs z usługi obrazu i przekazywanie ich wokół dla kodu macierzystego.)

## <a name="testing-your-images"></a>Testowanie obrazów
 Za pomocą narzędzia Podgląd biblioteki obrazów można przetestować manifesty obrazów, aby upewnić się, że wszystko jest poprawnie nachylione. Narzędzie można znaleźć w zestawie [SDK programu Visual Studio 2015](visual-studio-sdk.md). Dokumentację dla tego narzędzia i innych można znaleźć [tutaj](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Zasoby dodatkowe

### <a name="samples"></a>Samples
 Kilka przykładów programu Visual Studio w usłudze GitHub zostało zaktualizowanych, aby pokazać, jak korzystać z usługi obrazów w ramach różnych punktów rozszerzalności programu Visual Studio.

 Sprawdź, [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) czy nie ma najnowszych próbek.

### <a name="tooling"></a>Narzędzia
 Zestaw narzędzi pomocy technicznej dla usługi obraz został stworzony, aby pomóc w tworzeniu/aktualizowaniu interfejsu użytkownika, który współpracuje z usługą obrazu. Aby uzyskać więcej informacji na temat każdego narzędzia, zapoznaj się z dokumentacją dołączną do narzędzi. Narzędzia są dołączone do zestawu [SDK programu Visual Studio 2015.](visual-studio-sdk.md)

 **Źródła manifestuFromResources**

 Narzędzie Manifest z zasobów przyjmuje listę zasobów obrazu (PNG lub XAML) i generuje plik manifestu obrazu do używania tych obrazów z usługą obrazów.

 **Kod ManifestToCode**

 Narzędzie Manifest do kodu pobiera plik manifestu obrazu i generuje plik otoki do odwoływania się do wartości manifestu w kodzie (C++, C#lub VB) lub *plikach vsct.*

 **ImageLibraryViewer**

 Narzędzie Podgląd biblioteki obrazów można załadować manifesty obrazu i umożliwia użytkownikowi manipulowanie nimi w taki sam sposób Visual Studio, aby upewnić się, że manifest jest autorem poprawnie. Użytkownik może zmieniać tło, rozmiary, ustawienie DPI, wysoki kontrast i inne ustawienia. Wyświetla również informacje o wczytywania, aby znaleźć błędy w manifestach i wyświetla informacje o źródle dla każdego obrazu w manifeście.

## <a name="faq"></a>Często zadawane pytania

- Czy są jakieś zależności, które \<należy uwzględnić podczas ładowania Reference Include="Microsoft.VisualStudio.*. Interop.14.0.DesignTime" />?

  - Ustaw EmbedInteropTypes="true" na wszystkich międzyoperacyjnych bibliotekach DLL.

- Jak wdrożyć manifest obrazu z rozszerzeniem?

  - Dodaj plik *.imagemanifest* do projektu.

  - Ustaw wartość "Uwzględnij w VSIX" na Wartość True.

- Aktualizuję system cps project. Co się stało z **ImageName** i **StockIconService?**

  - Zostały one usunięte, gdy CPS został zaktualizowany do korzystania z monikers. Nie trzeba już wywoływać **StockIconService**, wystarczy przekazać żądany **KnownMoniker** do metody lub właściwości przy użyciu metody rozszerzenia **ToProjectSystemType()** w narzędziach CPS. Możesz znaleźć mapowanie z **ImageName** do **KnownMonikers** poniżej:

    |||
    |-|-|
    |**Imagename**|**ZnanyMoniker**|
    |Nazwa obrazu.OfflineWebApp|ZnaneImageIds.Web|
    |ImageName.WebReferencesFolder|ZnaneImageIds.Web|
    |Plik ImageName.OpenReferenceFolder|ZnaneImageIds.FolderOtwarte|
    |ImageName.ReferenceFolder|ZnaneImageIds.Reference|
    |Nazwa obrazu.Odwołanie|ZnaneImageIds.Reference|
    |Nazwa obrazu.SdlWebReference|ZnaneImageIds.WebReferenceFolder|
    |Nazwa obrazu.DiscoWebReference|ZnaneImageIds.DynamicDiscoveryDocument|
    |Nazwa obrazu.Folder|ZnaneImageIds.FolderClosed|
    |ImageName.OpenFolder|ZnaneImageIds.FolderOtwarte|
    |ImageName.ExcludedFolder|ZnaneImageIds.HiddenFolder Zamknięte|
    |ImageName.OpenExcludedFolder|ZnaneImageIds.HiddenFolderOtwarte|
    |Plik ImageName.Excluded|ZnaneImageIds.HiddenFile|
    |Plik ImageName.DependentFile|ZnaneImageIds.GenerateFile|
    |Nazwa obrazu.MissingFile|ZnaneImageIds.DocumentWarning|
    |Nazwa obrazu.WindowsForm|ZnaneImageIds.WindowsForm|
    |ImageName.WindowsUserControl|ZnaneImageIds.UserControl|
    |Nazwa obrazu.WindowsComponent|ZnaneImageIds.ComponentFile|
    |Nazwa obrazu.XmlSchema|ZnaneImageIds.XMLSchema|
    |Plik ImageName.XmlFile|Plik OmiageIds.XML|
    |ImageName.WebForm|ZnaneImageIds.Web|
    |Nazwa obrazu.WebService|ZnaneImageIds.WebService|
    |ImageName.WebUserControl|ZnaneImageIds.WebUserControl|
    |Nazwa obrazu.WebCustomUserControl|ZnaneImageIds.WebCustomControl|
    |ImageName.AspPage|Plik AsP ZnaneImageIds.ASP|
    |ImageName.GlobalApplicationClass|ZnaneImageIds.SettingsFile|
    |Nazwa obrazu.WebConfig|ZnanyImageIds.ConfigurationFile|
    |ImageName.HtmlPage|Plik KnownImageIds.HTMLFile|
    |Arkusz stylów imagename.style|Arkusz znanejemimageids.stylesheet|
    |Plik imagename.script|ZnaneImageIds.JSScript|
    |Plik imagename.textfile|Dokument Znane Identyfikatory..Dokument|
    |Plik ImageName.Settings|ZnaneImageIds.Ustawienia|
    |Nazwa obrazu.Zasoby|Grupa dokumentów KnownImageIds.DocumentGroup|
    |ImageName.Bitmapa|ZnaneImageIds.Image|
    |ImageName.Icon|ZnaneImageIds.IconFile|
    |Nazwa obrazu.Obraz|ZnaneImageIds.Image|
    |ImageName.ImageMap|ZnaneImageIds.ImageMapFile|
    |Nazwa obrazu.XWorld|ZnaneImageIds.XWorldFile|
    |Nazwa obrazu.Audio|ZnaneImageIds.Sound|
    |Nazwa obrazu.Wideo|ZnaneImageIds.Media|
    |Nazwa obrazu.Cab|ZnaneImageIds.CABProject|
    |Nazwa obrazu.Jar|ZnaneImageIds.JARFile|
    |ImageName.DataŚrodowienie wzięcie|ZnaneImageIds.DataTable|
    |Plik imagename.Preview|Raport Znane Imiage.Report|
    |Nazwa obrazu.DanglingReference|ZnaneImageIds.ReferenceWarning|
    |Plik ImageName.XsltFile|ZnaneImageIds.XSLTransform|
    |ImageName.Cursor|ZnaneImageIds.CursorFile|
    |ImageName.AppDesignerFolder|Właściwość ZnaneJimageIds.Property|
    |Nazwa obrazu.Dane|ZnaneImageIds.Database|
    |Nazwa obrazu.Aplikacja|Znane Identyfikatory.Aplikacja|
    |Zestaw danych ImageName.Data|Grupa znanejemimageIds.DatabaseGroup|
    |Nazwa obrazu.Pfx|Certyfikat ZnaneJimageIds.Certyfikat|
    |Nazwa obrazu.Snk|ZnaneImageIds.Rule|
    |ImageName.VisualBasicProject|ZnaneImageIds.VBProjectNode|
    |ImageName.CSharpProject|ZnaneImageIds.CSProjectNode|
    |Nazwa obrazu.Pusta|ZnaneImageIds.Blank|
    |Nazwa obrazu.MissingFolder|ZnaneImageIds.FolderOffline|
    |Nazwa obrazu.SharedImportReference|ZnaneImageIds.SharedProject|
    |ImageName.SharedProjectCs|ZnanyImageIds.CSSharedProject|
    |Nazwa obrazu.SharedProjectVc|ZnanyImageIds.CPPSharedProject|
    |Nazwa obrazu.SharedProjectJs|ZnanyImageIds.JSSharedProject|
    |Plik ImageName.CSharpCodeFile|ZnaneImageIds.CSFileNode|
    |Plik ImageName.VisualBasicCodeFile|ZnaneImageIds.VBFileNode|

  - Aktualizuję dostawcę listy ukończenia. Co **ZnaneMonikers** dopasować do starych **StandardGlyphGroup** i **StandardGlyph** wartości?

    ||||
    |-|-|-|
    |Klasa grupy Glyph|GlyphItemPubliczny|KlasaPublic|
    |Klasa grupy Glyph|GlyphItemInternal|KlasaInternal|
    |Klasa grupy Glyph|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|KlasaInternal|
    |Klasa grupy Glyph|GlifItemChoryzowane|KlasaChchronione|
    |Klasa grupy Glyph|GlifItemPrivate|KlasaPrywatna|
    |Klasa grupy Glyph|GlyphItemShortcut (glif)|ClassShortcut (Wytniec)|
    |GlyphGroupConstant (GliphGroupConstant)|GlyphItemPubliczny|StałaPubliczna|
    |GlyphGroupConstant (GliphGroupConstant)|GlyphItemInternal|StałaWłączna|
    |GlyphGroupConstant (GliphGroupConstant)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|StałaWłączna|
    |GlyphGroupConstant (GliphGroupConstant)|GlifItemChoryzowane|StałaZabezpieczona|
    |GlyphGroupConstant (GliphGroupConstant)|GlifItemPrivate|ConstantPrivate (ConstantPrivate)|
    |GlyphGroupConstant (GliphGroupConstant)|GlyphItemShortcut (glif)|ConstantShortcut (ConstantShortcut)|
    |GlyphGroupDelegate (glifgrupydelegate)|GlyphItemPubliczny|DelegatPublic|
    |GlyphGroupDelegate (glifgrupydelegate)|GlyphItemInternal|DelegatInternal|
    |GlyphGroupDelegate (glifgrupydelegate)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|DelegatInternal|
    |GlyphGroupDelegate (glifgrupydelegate)|GlifItemChoryzowane|DelegatOchronowany|
    |GlyphGroupDelegate (glifgrupydelegate)|GlifItemPrivate|DelegatPrivate|
    |GlyphGroupDelegate (glifgrupydelegate)|GlyphItemShortcut (glif)|DelegaciKrót|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlyphItemPubliczny|WyliczeniePubliczacjaPubliczacja|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlyphItemInternal|WyliczenieInternal|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|WyliczenieInternal|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlifItemChoryzowane|WyliczenieZabezpieczone|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlifItemPrivate|WyliczeniePrwatyzacja|
    |GlyphGroupEnum (Grupa GlyphGroupEnum)|GlyphItemShortcut (glif)|Wyliczanie Skrótu|
    |GlyphGroupEnumPozyt|GlyphItemPubliczny|WyliczanieWyniestawieniePubliczne|
    |GlyphGroupEnumPozyt|GlyphItemInternal|WyliczanieItemInternal|
    |GlyphGroupEnumPozyt|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|WyliczanieItemInternal|
    |GlyphGroupEnumPozyt|GlifItemChoryzowane|WyliczanieTe zabezpieczenia|
    |GlyphGroupEnumPozyt|GlifItemPrivate|WyliczanieItemPrivate|
    |GlyphGroupEnumPozyt|GlyphItemShortcut (glif)|WyliczenieItemShortcut|
    |GlyphGroupEvent (GlyphGroupEvent)|GlyphItemPubliczny|WydarzeniePubliczne|
    |GlyphGroupEvent (GlyphGroupEvent)|GlyphItemInternal|WydarzenieInternal|
    |GlyphGroupEvent (GlyphGroupEvent)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|WydarzenieInternal|
    |GlyphGroupEvent (GlyphGroupEvent)|GlifItemChoryzowane|Chronione zdarzenia|
    |GlyphGroupEvent (GlyphGroupEvent)|GlifItemPrivate|WydarzeniePrywatne|
    |GlyphGroupEvent (GlyphGroupEvent)|GlyphItemShortcut (glif)|Zdarzenie.|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlyphItemPubliczny|WyjątekPubliczny|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlyphItemInternal|WyjątekInternal|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|WyjątekInternal|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlifItemChoryzowane|Chronione wyjątkami|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlifItemPrivate|WyjątekPrywatny|
    |GlyphGroupException (Nie zmienianie grupy glifów)|GlyphItemShortcut (glif)|WyjątekSortcut|
    |GlyphGroupField (Pola grupowe)|GlyphItemPubliczny|PolePublic|
    |GlyphGroupField (Pola grupowe)|GlyphItemInternal|PoleInternal|
    |GlyphGroupField (Pola grupowe)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|PoleInternal|
    |GlyphGroupField (Pola grupowe)|GlifItemChoryzowane|Chronione polem|
    |GlyphGroupField (Pola grupowe)|GlifItemPrivate|PolePrywatne|
    |GlyphGroupField (Pola grupowe)|GlyphItemShortcut (glif)|PoleKłe|
    |GlyphGroupInterface|GlyphItemPubliczny|InterfejsPubliczny|
    |GlyphGroupInterface|GlyphItemInternal|InterfejsInternal|
    |GlyphGroupInterface|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|InterfejsInternal|
    |GlyphGroupInterface|GlifItemChoryzowane|Chroniony interfejs|
    |GlyphGroupInterface|GlifItemPrivate|InterfejsPrywatyzny|
    |GlyphGroupInterface|GlyphItemShortcut (glif)|InterfaceShortcut (Wytniec)|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlyphItemPubliczny|MakroPubliczne|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlyphItemInternal|MakroInternal|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MakroInternal|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlifItemChoryzowane|Makrochronione|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlifItemPrivate|Makroprywatny|
    |GlyphGroupMacro (Grupa GlyphGroupMacro)|GlyphItemShortcut (glif)|Makroskręciowe|
    |Mapa grupy Glyph|GlyphItemPubliczny|MapaPubliczna|
    |Mapa grupy Glyph|GlyphItemInternal|MapaInternal|
    |Mapa grupy Glyph|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MapaInternal|
    |Mapa grupy Glyph|GlifItemChoryzowane|Chronione mapy|
    |Mapa grupy Glyph|GlifItemPrivate|MapPrivate|
    |Mapa grupy Glyph|GlyphItemShortcut (glif)|MapShortcut (MapShortcut)|
    |GlyphGroupMapItem|GlyphItemPubliczny|MapaNajpubliczna|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MapItemInternal|
    |GlyphGroupMapItem|GlifItemChoryzowane|MapItemChorytowane|
    |GlyphGroupMapItem|GlifItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut (glif)|MapItemKrót|
    |GlyphGroupMetoda|GlyphItemPubliczny|MetodaPubliczna|
    |GlyphGroupMetoda|GlyphItemInternal|MetodaInterna|
    |GlyphGroupMetoda|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MetodaInterna|
    |GlyphGroupMetoda|GlifItemChoryzowane|MetodaZabezpieczona|
    |GlyphGroupMetoda|GlifItemPrivate|MetodaPrywatna|
    |GlyphGroupMetoda|GlyphItemShortcut (glif)|MetodaSkrót|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlyphItemPubliczny|MetodaPubliczna|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlyphItemInternal|MetodaInterna|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MetodaInterna|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlifItemChoryzowane|MetodaZabezpieczona|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlifItemPrivate|MetodaPrywatna|
    |GlyphGroupOverload (Obciążenie grupy GlyphGroup)|GlyphItemShortcut (glif)|MetodaSkrót|
    |GlyphGroupModule|GlyphItemPubliczny|ModułPubliczny|
    |GlyphGroupModule|GlyphItemInternal|ModułInternal|
    |GlyphGroupModule|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|ModułInternal|
    |GlyphGroupModule|GlifItemChoryzowane|ModułZabezpieczony|
    |GlyphGroupModule|GlifItemPrivate|ModułPrywatny|
    |GlyphGroupModule|GlyphItemShortcut (glif)|ModułShortcut|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlyphItemPubliczny|Przestrzeń nazwPubliczny|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlyphItemInternal|Przestrzeń nazwInternal|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|Przestrzeń nazwInternal|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlifItemChoryzowane|Obszar nazwChronione|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlifItemPrivate|Przestrzeń nazwPrywatny|
    |GlyphGroupNamespace (GlyphGroupNamespace)|GlyphItemShortcut (glif)|Obszar nazwSkrótce|
    |GlyphGroupOperator|GlyphItemPubliczny|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|OperatorInternal|
    |GlyphGroupOperator|GlifItemChoryzowane|OperatorZabezpieczony|
    |GlyphGroupOperator|GlifItemPrivate|OperatorPrywatny|
    |GlyphGroupOperator|GlyphItemShortcut (glif)|OperatorShortcut (Wytniec) operatora|
    |GlyphGroupProperty|GlyphItemPubliczny|NieruchomościPubliczny|
    |GlyphGroupProperty|GlyphItemInternal|NieruchomośćInternal|
    |GlyphGroupProperty|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|NieruchomośćInternal|
    |GlyphGroupProperty|GlifItemChoryzowane|WłaściwościChronione|
    |GlyphGroupProperty|GlifItemPrivate|PropertyPrivate (Własność)|
    |GlyphGroupProperty|GlyphItemShortcut (glif)|PropertyShortcut (Wytniec)|
    |Struktura grupy Glyph|GlyphItemPubliczny|StrukturaPubliczny|
    |Struktura grupy Glyph|GlyphItemInternal|StrukturaInternal|
    |Struktura grupy Glyph|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|StrukturaInternal|
    |Struktura grupy Glyph|GlifItemChoryzowane|StrukturaZabezpieczona|
    |Struktura grupy Glyph|GlifItemPrivate|StrukturaPrywatna|
    |Struktura grupy Glyph|GlyphItemShortcut (glif)|StrukturaShortcut|
    |Płyta GlyphGroupTemplate|GlyphItemPubliczny|SzablonPubliczny|
    |Płyta GlyphGroupTemplate|GlyphItemInternal|SzablonInternajmalny|
    |Płyta GlyphGroupTemplate|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|SzablonInternajmalny|
    |Płyta GlyphGroupTemplate|GlifItemChoryzowane|SzablonChronione|
    |Płyta GlyphGroupTemplate|GlifItemPrivate|SzablonPrwat|
    |Płyta GlyphGroupTemplate|GlyphItemShortcut (glif)|SzablonSkrót|
    |GlyphGroupTypedef|GlyphItemPubliczny|TypDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypDefinicjaInternal|
    |GlyphGroupTypedef|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|TypDefinicjaInternal|
    |GlyphGroupTypedef|GlifItemChoryzowane|TekstDefifinitionChzabezpieczony|
    |GlyphGroupTypedef|GlifItemPrivate|TypDefinicjaPrywatna|
    |GlyphGroupTypedef|GlyphItemShortcut (glif)|TypDefinicjaZaskuj|
    |Typ grupy Glyph|GlyphItemPubliczny|TypPublic|
    |Typ grupy Glyph|GlyphItemInternal|TypInternal|
    |Typ grupy Glyph|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|TypInternal|
    |Typ grupy Glyph|GlifItemChoryzowane|TypZabezpieczony|
    |Typ grupy Glyph|GlifItemPrivate|TypPrywatny|
    |Typ grupy Glyph|GlyphItemShortcut (glif)|TypSekcut|
    |Związek GlyphGroupUnion|GlyphItemPubliczny|UniaPubliczna|
    |Związek GlyphGroupUnion|GlyphItemInternal|UniaWieńczy|
    |Związek GlyphGroupUnion|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|UniaWieńczy|
    |Związek GlyphGroupUnion|GlifItemChoryzowane|UnionProtected (UnionProtected)|
    |Związek GlyphGroupUnion|GlifItemPrivate|UniaPrywatna|
    |Związek GlyphGroupUnion|GlyphItemShortcut (glif)|UnionShortcut (UnionShortcut)|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlyphItemPubliczny|PolePublic|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlyphItemInternal|PoleInternal|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|PoleInternal|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlifItemChoryzowane|Chronione polem|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlifItemPrivate|PolePrywatne|
    |GlyphGroupVariable (Grupa GlyphGroupVariable)|GlyphItemShortcut (glif)|PoleKłe|
    |Typ glyphgroupvaluetype|GlyphItemPubliczny|ValueTypePublic|
    |Typ glyphgroupvaluetype|GlyphItemInternal|WartośćPInterna|
    |Typ glyphgroupvaluetype|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|WartośćPInterna|
    |Typ glyphgroupvaluetype|GlifItemChoryzowane|WartośćTypeChronikowane|
    |Typ glyphgroupvaluetype|GlifItemPrivate|ValueTypePrivate (Typ wartości)|
    |Typ glyphgroupvaluetype|GlyphItemShortcut (glif)|ValueTypeShortcut (Typ błędu wartości)|
    |GlyphGroupIntrinsic|GlyphItemPubliczny|ObiektPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObiektInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|ObiektInternal|
    |GlyphGroupIntrinsic|GlifItemChoryzowane|ObiektChronione|
    |GlyphGroupIntrinsic|GlifItemPrivate|ObjectPrivate ( ObjectPrivate )|
    |GlyphGroupIntrinsic|GlyphItemShortcut (glif)|Polecenie ObjectShortcut|
    |GlyphGroupJSharpMetoda|GlyphItemPubliczny|MetodaPubliczna|
    |GlyphGroupJSharpMetoda|GlyphItemInternal|MetodaInterna|
    |GlyphGroupJSharpMetoda|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|MetodaInterna|
    |GlyphGroupJSharpMetoda|GlifItemChoryzowane|MetodaZabezpieczona|
    |GlyphGroupJSharpMetoda|GlifItemPrivate|MetodaPrywatna|
    |GlyphGroupJSharpMetoda|GlyphItemShortcut (glif)|MetodaSkrót|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlyphItemPubliczny|PolePublic|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlyphItemInternal|PoleInternal|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|PoleInternal|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlifItemChoryzowane|Chronione polem|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlifItemPrivate|PolePrywatne|
    |GlyphGroupJSharpField (Grupa GlyphSSharpField)|GlyphItemShortcut (glif)|PoleKłe|
    |GlyphGroupJSharpClass|GlyphItemPubliczny|KlasaPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|KlasaInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|KlasaInternal|
    |GlyphGroupJSharpClass|GlifItemChoryzowane|KlasaChchronione|
    |GlyphGroupJSharpClass|GlifItemPrivate|KlasaPrywatna|
    |GlyphGroupJSharpClass|GlyphItemShortcut (glif)|ClassShortcut (Wytniec)|
    |GlyphGroupJSharpNamespace|GlyphItemPubliczny|Przestrzeń nazwPubliczny|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|Przestrzeń nazwInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|Przestrzeń nazwInternal|
    |GlyphGroupJSharpNamespace|GlifItemChoryzowane|Obszar nazwChronione|
    |GlyphGroupJSharpNamespace|GlifItemPrivate|Przestrzeń nazwPrywatny|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut (glif)|Obszar nazwSkrótce|
    |GlyphGroupJSharpInterface|GlyphItemPubliczny|InterfejsPubliczny|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfejsInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend (Przyjaciel Glifitemprzychyń)|InterfejsInternal|
    |GlyphGroupJSharpInterface|GlifItemChoryzowane|Chroniony interfejs|
    |GlyphGroupJSharpInterface|GlifItemPrivate|InterfejsPrywatyzny|
    |GlyphGroupJSharpInterface|GlyphItemShortcut (glif)|InterfaceShortcut (Wytniec)|
    |GlyphGroupError (glifgrupyerror)||StatusError|
    |GlyphBscFile||Plik klasy|
    |Glyphassembly||Tematy pomocy|
    |GlifBrary||Biblioteka|
    |GlyphVBProjekt||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||Nie ma wyrozumiory CPP|
    |GlyphDialogId (glifdialogid)||Okno dialogowe|
    |GlifopenFolder||FolderOtwarte|
    |GlyphClosedFolder||FolderClosed|
    |GlifArrow||GoToNext (Niem.)|
    |GlyphCSharpFile||CsFileNode (Plik)|
    |GlyphCSharpRozwiń||Fragment kodu|
    |GlifKeyword||IntellisenseKeyword (Słowo IntellisenseKeyword)|
    |Informacje glifowe||Informacje o stanie|
    |GlifReferencja||Lekcjametodreferencja|
    |GlyphRecursion (glif)||Rekursja|
    |GlyphXmlItem||Tag|
    |GlyphJSharpProjekt||DocumentCollection|
    |GlyphJSharpDocument||Dokument|
    |GlyphForwardType (Typ GlyphForward||GoToNext (Niem.)|
    |GlyphCallersGraph (glifcallersgraph)||Połączenie Telefoniczne|
    |GlyphCallGraph (glifcallgraph)||WywołanieFrom|
    |GlyphWarning (glifowarning)||StanWarning|
    |GlifMaybeReferencja||Znak zapytania|
    |GlyphMaybeCaller (glifmaybecaller)||Połączenie Telefoniczne|
    |GlyphMaybeCall (glifmaybecall)||WywołanieFrom|
    |GlyphExtensionMetoda||ExtensionMetoda|
    |GlyphExtensionMethodInternal||ExtensionMetoda|
    |GlyphExtensionMethodFriend||ExtensionMetoda|
    |GlyphExtensionMethodProtekowane||ExtensionMetoda|
    |GlyphExtensionMethodPrivate||ExtensionMetoda|
    |GlyphExtensionMethodShortcut||ExtensionMetoda|
    |Atrybut GlyphXmlAttribute||Xmlattribute|
    |Dziecko GlyphXml||Xmlelement|
    |GlyphXmlDescendant||XmlDescendant|
    |Obszar GlyphXmlNamespace||Xmlnamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowPoufność|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |Prośba o 2000 000 000 000 000 0||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantWestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConufencja|
    |GlyphCompletionOwaczenie||IntellisenseOwakowanie|
