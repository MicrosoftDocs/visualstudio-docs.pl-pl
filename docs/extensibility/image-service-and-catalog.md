---
title: Usługa obrazów i wykaz | Microsoft Docs
description: Ten artykuł zawiera wskazówki i najlepsze rozwiązania dotyczące wdrażania usługi obrazów programu Visual Studio i wykazu obrazów.
ms.custom: SEO-VS-2020
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4483d73a5e6124006f09d05065b6f75f7a654e47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082130"
---
# <a name="image-service-and-catalog"></a>Usługa obrazów i wykaz
Ten Cookbook zawiera wskazówki i najlepsze rozwiązania dotyczące wdrażania usługi obrazów programu Visual Studio i katalogu obrazów wprowadzonego w programie Visual Studio 2015.

 Usługa obrazu wprowadzona w programie Visual Studio 2015 umożliwia deweloperom uzyskanie najlepszych obrazów dla urządzenia i wybranego motywu użytkownika do wyświetlania obrazu, w tym poprawianie ich dla kontekstu, w którym są wyświetlane. Przyjęcie usługi obrazów pomoże wyeliminować główne punkty bólu związane z konserwacją zasobów, HDPI skalowaniem i motywami.

|**Problemy dzisiaj**|**Rozwiązania**|
|-|-|
|Mieszanie koloru tła|Wbudowane mieszanie alfa|
|Obrazy motywów (niektóre)|Metadane motywu|
|Tryb duży kontrast|Alternatywne zasoby duży kontrast|
|Potrzebujesz wielu zasobów dla różnych trybów DPI|Zasoby wybierane z rezerwami opartymi na wektorach|
|Duplikuj obrazy|Jeden identyfikator na koncepcję obrazu|

 Dlaczego warto zastosować usługę obrazu?

- Zawsze korzystaj z najnowszego obrazu "pikseli-doskonałe" w programie Visual Studio

- Możesz przesyłać własne obrazy i korzystać z nich

- Nie trzeba testować obrazów, gdy system Windows dodaje nowe skalowanie DPI

- Rozwiązywanie starych progów architektury w implementacjach

  Pasek narzędzi powłoki programu Visual Studio przed i po użyciu usługi obrazów:

  ![Usługa obrazów przed i po](../extensibility/media/image-service-before-and-after.png "Usługa obrazów przed i po")

## <a name="how-it-works"></a>Jak to działa
 Usługa Image Service może dostarczyć obraz mapy bitowej odpowiedni dla każdej obsługiwanej struktury interfejsu użytkownika:

- WPF: BitmapSource

- WinForms: System. Drawing. map bitowych

- Win32: HBITMAP

  Diagram przepływu usługi obrazów

  ![Diagram przepływu usługi obrazów](../extensibility/media/image-service-flow-diagram.png "Diagram przepływu usługi obrazów")

  **Monikery obrazów**

  Moniker obrazu (lub moniker krótki) to para identyfikatorów GUID/identyfikatorów, która jednoznacznie identyfikuje zasób obrazu lub element zawartości listy obrazów w bibliotece obrazów.

  **Znane monikery**

  Zestaw monikerów obrazów zawartych w katalogu obrazów programu Visual Studio i publicznie używany przez dowolny składnik lub rozszerzenie programu Visual Studio.

  **Pliki manifestu obrazu**

  Pliki manifestu obrazu (*. imagemanifest*) to pliki XML, które definiują zestaw zasobów obrazu, monikery reprezentujące te elementy zawartości oraz rzeczywisty obraz lub obrazy reprezentujące każdy element zawartości. Manifesty obrazu mogą definiować autonomiczne obrazy lub listy obrazów do obsługi starszego interfejsu użytkownika. Ponadto istnieją atrybuty, które można ustawić w elemencie zawartości lub w poszczególnych obrazach za każdy element zawartości, aby zmienić czas i sposób wyświetlania tych zasobów.

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

 Jako pomoc w zakresie czytelności i konserwacji, manifest obrazu może używać symboli dla wartości atrybutów. Symbole są zdefiniowane w następujący sposób:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Podelementu**|**Definicja**|
|-|-|
|Importuj|Importuje symbole danego pliku manifestu do użycia w bieżącym manifeście|
|Guid (identyfikator GUID)|Symbol reprezentuje identyfikator GUID i musi pasować do formatowania identyfikatora GUID|
|ID (Identyfikator)|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą|
|Ciąg|Symbol reprezentuje arbitralną wartość ciągu|

 W symbolach jest rozróżniana wielkość liter i istnieje odwołanie do niej przy użyciu składni $ (symbol-nazwa):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one być używane w atrybucie URI \<Source> \<Import> elementu lub do odwoływania się do ścieżek na komputerze lokalnym.

|**Symbol**|**Opis**|
|-|-|
|CommonProgramFiles|Wartość zmiennej środowiskowej% CommonProgramFiles%|
|LocalAppData|Wartość zmiennej środowiskowej% LocalAppData%|
|ManifestFolder|Folder zawierający plik manifestu|
|Czy|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|
|ProgramFiles|Wartość zmiennej środowiskowej% ProgramFiles%|
|System|Folder *Windows\System32*|
|WinDir|Wartość zmiennej środowiskowej% WinDir%|

 **Obraz**

 \<Image>Element definiuje obraz, do którego może odwoływać się moniker. Identyfikatory GUID i ID razem tworzą moniker obrazu. Moniker obrazu musi być unikatowy w całej bibliotece obrazów. Jeśli więcej niż jeden obraz ma daną moniker, pierwszy napotkany podczas kompilowania biblioteki jest zachowywany.

 Musi zawierać co najmniej jedno źródło. Źródła o rozmiarze neutralnym zapewniają najlepsze wyniki dla szerokiego zakresu rozmiarów, ale nie są wymagane. Jeśli zostanie wyświetlona prośba o obraz rozmiaru, który nie jest zdefiniowany w \<Image> elemencie i nie ma źródła o rozmiarze neutralnym, usługa wybierze Źródło najlepszego rozmiaru i przeskaluje je do żądanego rozmiaru.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|Potrzeb Część identyfikatora GUID obrazu monikera|
|ID (Identyfikator)|Potrzeb Część identyfikatora monikera obrazu|
|AllowColorInversion|[Opcjonalne, wartość domyślna true] Wskazuje, czy obraz może być programowo odwrócony, gdy jest używany na ciemnym tle.|

 **Element źródłowy**

 \<Source>Element definiuje pojedynczy zasób źródłowy obrazu (XAML i PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Atrybut**|**Definicja**|
|-|-|
|Adresu|Potrzeb Identyfikator URI, który definiuje miejsce, z którego można załadować obraz. Może to być jedna z następujących opcji:<br /><br /> - [Identyfikator URI pakietu](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) przy użyciu urzędu Application:///<br />-Bezwzględne odwołanie do zasobu składnika<br />-Ścieżka do pliku zawierającego zasób natywny|
|Tło|Obowiązkowe Wskazuje, jaki rodzaj tła ma być używany.<br /><br /> Może to być jedna z następujących opcji:<br /><br /> *Jasne:* Źródło może być używane na jasnym tle.<br /><br /> *Ciemny:* Źródło może być używane w ciemnym tle.<br /><br /> *HighContrast:* Źródło może być używane na dowolnym tle w trybie duży kontrast.<br /><br /> *HighContrastLight:* Źródło może być używane na jasnym tle w trybie duży kontrast.<br /><br /> *HighContrastDark:* Źródło może być używane na ciemnym tle w trybie duży kontrast.<br /><br /> Jeśli atrybut Background zostanie pominięty, źródło może być używane w dowolnym tle.<br /><br /> Jeśli tło jest *jasne*, *ciemne*, *HighContrastLight* lub *HighContrastDark*, kolory źródła nigdy nie są odwracane. Jeśli tło zostanie pominięte lub ustawiona na *HighContrast*, inwersja kolorów źródła jest kontrolowana przez atrybut **AllowColorInversion** obrazu.|

\<Source>Element może mieć dokładnie jeden z następujących opcjonalnych podelementów:

|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|
|-|-|-|
|\<Size>|Wartość|Źródło będzie używane dla obrazów o danym rozmiarze (w jednostkach urządzeń). Obraz będzie kwadratowy.|
|\<SizeRange>|MinSize, brak|Źródło będzie używane dla obrazów z MinSize do rozmiaru całkowitego (w jednostkach urządzeń) włącznie. Obraz będzie kwadratowy.|
|\<Dimensions>|Szerokość, Wysokość|Źródło będzie używane dla obrazów o danej szerokości i wysokości (w jednostkach urządzeń).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie używane w przypadku obrazów o minimalnej szerokości/wysokości do maksymalnej szerokości/wysokości (w jednostkach urządzeń) włącznie.|

 \<Source>Element może również mieć opcjonalny \<NativeResource> podelement, który definiuje, \<Source> który jest ładowany z zestawu natywnego, a nie z zestawu zarządzanego.

```xml
<NativeResource Type="type" ID="int" />
```

|**Atrybut**|**Definicja**|
|-|-|
|Typ|Potrzeb Typ zasobu natywnego, XAML lub PNG|
|ID (Identyfikator)|Potrzeb Część identyfikatora całkowitego zasobu natywnego|

 **Obrazów**

 \<ImageList>Element definiuje kolekcję obrazów, które mogą być zwracane w jednym pasku. Pasek jest zbudowany na żądanie, zgodnie z potrzebami.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Atrybut**|**Definicja**|
|-|-|
|Guid (identyfikator GUID)|Potrzeb Część identyfikatora GUID obrazu monikera|
|ID (Identyfikator)|Potrzeb Część identyfikatora monikera obrazu|
|Zewnętrzna|[Opcjonalne, wartość domyślna to false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w bieżącym manifeście.|

 Moniker zawartego obrazu nie musi odwoływać się do obrazu zdefiniowanego w bieżącym manifeście. Jeśli w bibliotece obrazów nie można znaleźć zawartego obrazu, w jego miejscu zostanie użyty pusty obraz zastępczy.

## <a name="using-the-image-service"></a>Korzystanie z usługi Image Service

### <a name="first-steps-managed"></a>Pierwsze kroki (zarządzane)
 Aby korzystać z usługi Image Service, należy dodać do projektu odwołania do niektórych lub wszystkich następujących zestawów:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Wymagane, jeśli używasz wbudowanego wykazu **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Wymagane, jeśli używasz **CrispImage** i **ImageThemingUtilities** w interfejsie użytkownika WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Wymagane, jeśli używane są typy **ImageMoniker** i **structsize** .

  - **EmbedInteropTypes** powinna mieć wartość true.

- *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime*

  - Wymagane, jeśli używasz typu **IVsImageService2** .

  - **EmbedInteropTypes** powinna mieć wartość true.

- *Microsoft.VisualStudio.Utilities.dll*

  - Wymagany, jeśli używasz **BrushToColorConverter** dla **ImageThemingUtilities. ImageBackgroundColor** w interfejsie użytkownika WPF.

- *Microsoft. VisualStudio. Shell. \<VSVersion> . 2,0*

  - Wymagane, jeśli używasz typu **IVsUIObject** .

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Wymagane w przypadku korzystania z pomocników interfejsu użytkownika powiązanych z WinFormami.

  - **EmbedInteropTypes** powinna być ustawiona na wartość true

### <a name="first-steps-native"></a>Pierwsze kroki (natywne)
 Aby korzystać z usługi Image Service, należy uwzględnić niektóre lub wszystkie z następujących nagłówków w projekcie:

- **KnownImageIds. h**

  - Wymagane, jeśli używasz wbudowanego **KnownMonikers** wykazu obrazów, ale nie można użyć typu **ImageMoniker** , takiego jak podczas zwracania wartości z **IVsHierarchy GetGuidProperty** lub **GetProperty** wywołania.

- **KnownMonikers. h**

  - Wymagane, jeśli używasz wbudowanego wykazu **KnownMonikers**.

- **ImageParameters140. h**

  - Wymagane, jeśli używane są typy **ImageMoniker** i **structsize** .

- **VSShell140. h**

  - Wymagane, jeśli używasz typu **IVsImageService2** .

- **ImageThemingUtilities. h**

  - Wymagane, jeśli nie możesz pozwolić, aby usługa Image mogła je obsłużyć.

  - Nie należy używać tego nagłówka, jeśli usługa obrazów może obsłużyć wykonywanie przez nich obrazów.

::: moniker range="vs-2017"
- **VSUIDPIHelper. h**

  - Wymagane, jeśli używasz pomocników DPI do uzyskania bieżącej wartości DPI.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness. h**

  - Wymagane w przypadku korzystania z pomocników rozpoznawania DPI w celu uzyskania bieżącej wartości DPI.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Jak mogę napisać nowy interfejs użytkownika WPF?

1. Zacznij od dodania odwołań do zestawu wymaganych w powyższej sekcji pierwsze kroki do projektu. Nie musisz dodawać wszystkich z nich, więc Dodaj tylko potrzebne odwołania. (Uwaga: Jeśli używasz lub masz dostęp do **kolorów** zamiast **pędzli**, możesz pominąć odwołanie do **narzędzi**, ponieważ nie będziesz potrzebować konwertera).

2. Wybierz żądany obraz i uzyskaj jego moniker. Użyj **KnownMoniker** lub własne obrazy niestandardowe i monikery, korzystając z własnych obrazów.

3. Dodaj **CrispImages** do języka XAML. (Zobacz poniżej przykład).

4. Ustaw właściwość **ImageThemingUtilities. ImageBackgroundColor** w hierarchii interfejsu użytkownika. (Ta wartość powinna być ustawiona w lokalizacji, w której jest znany kolor tła, niekoniecznie na **CrispImage**). (Zobacz poniżej przykład).

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

 **Jak mogę zaktualizować istniejący interfejs użytkownika WPF?**

 Aktualizowanie istniejącego interfejsu użytkownika WPF to stosunkowo prosty proces obejmujący trzy podstawowe kroki:

1. Zamień wszystkie \<Image> elementy w interfejsie użytkownika na \<CrispImage> elementy.

2. Zmień wszystkie atrybuty źródłowe na atrybuty monikera.

    - Jeśli obraz nigdy nie ulegnie zmianie i używasz **KnownMonikers**, statycznie powiązać tę właściwość z **KnownMoniker**. (Zobacz powyższy przykład).

    - Jeśli obraz nigdy nie ulegnie zmianie i używasz własnego obrazu niestandardowego, należy powiązać statycznie z własnym monikerem.

    - Jeśli obraz może się zmienić, powiąż z atrybutem moniker z właściwością kodu, która powiadamia o zmianach właściwości.

3. W obszarze hierarchia interfejsu użytkownika Ustaw **ImageThemingUtilities. ImageBackgroundColor** , aby upewnić się, że wersja koloru jest prawidłowo działać.

    - Może to wymagać użycia klasy **BrushToColorConverter** . (Zobacz powyższy przykład).

## <a name="how-do-i-update-win32-ui"></a>Jak mogę zaktualizować interfejs użytkownika Win32?
 Dodaj następujące elementy do kodu, wszędzie tam, gdzie jest to konieczne, aby zastąpić pierwotne ładowanie obrazów. W razie potrzeby przełącz wartości dla HBITMAPs w porównaniu do HICONs i HIMAGELIST.

 **Pobierz usługę obrazu**

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

## <a name="how-do-i-update-winforms-ui"></a>Jak mogę zaktualizować interfejs użytkownika WinForms?
 Dodaj następujące elementy do kodu, wszędzie tam, gdzie jest to konieczne, aby zastąpić pierwotne ładowanie obrazów. Przełącz wartości w celu zwrócenia map bitowych i ikon zgodnie z wymaganiami.

 **Przydatne użycie instrukcji**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Pobierz usługę obrazu**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Zażądaj obrazu**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak mogę używać monikerów obrazów w nowym oknie narzędzi?
 Szablon projektu pakietu VSIX został zaktualizowany dla programu Visual Studio 2015. Aby utworzyć nowe okno narzędzi, kliknij prawym przyciskiem myszy projekt VSIX i wybierz polecenie **Dodaj**  >  **nowy element** (**Ctrl** + **SHIFT** + **a**). W węźle rozszerzalności dla języka projektu wybierz pozycję **okno narzędzi niestandardowych**, nadaj oknomu narzędziu nazwę i naciśnij przycisk **Dodaj** .

 Są to kluczowe miejsca do używania monikerów w oknie narzędzi. Postępuj zgodnie z instrukcjami dla każdej z nich:

1. Karta okno narzędzi, gdy karty są wystarczająco małe (używane również w  + przełączniku okna **karty** Ctrl).

    Dodaj ten wiersz do konstruktora dla klasy, która pochodzi od typu **elementu toolwindowpane** :

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Polecenie umożliwiające otwarcie okna narzędzi.

    W pliku *. vsct* pakietu, Edytuj przycisk polecenia okna narzędzia:

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

   **Jak mogę użyć monikerów obrazów w istniejącym oknie narzędzi?**

   Aktualizacja istniejącego okna narzędzi do używania monikerów obrazów jest podobna do procedury tworzenia nowego okna narzędzi.

   Są to kluczowe miejsca do używania monikerów w oknie narzędzi. Postępuj zgodnie z instrukcjami dla każdej z nich:

3. Karta okno narzędzi, gdy karty są wystarczająco małe (używane również w  + przełączniku okna **karty** Ctrl).

   1. Usuń te wiersze (jeśli istnieją) w konstruktorze dla klasy, która pochodzi od typu **elementu toolwindowpane** :

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Zobacz Krok #1 "Jak mogę użyć monikerów obrazów w nowym oknie narzędzi?". powyższej sekcji.

4. Polecenie umożliwiające otwarcie okna narzędzi.

   - Zobacz Krok #2 "Jak mogę użyć monikerów obrazów w nowym oknie narzędzi?". powyższej sekcji.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Jak mogę używać monikerów obrazów w pliku. vsct?
 Zaktualizuj plik *. vsct* , zgodnie z opisem w poniższych wierszach z komentarzem:

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

 **Co zrobić, jeśli plik my. vsct musi być także odczytywany przez starsze wersje programu Visual Studio?**

 Starsze wersje programu Visual Studio nie rozpoznają flagi polecenia **IconIsMoniker** . Możesz użyć obrazów z usługi Image Service w wersjach programu Visual Studio, które go obsługują, ale w przypadku starszych wersji programu Visual Studio nadal Używaj obrazów w starym stylu. W tym celu należy pozostawić plik *. vsct* bez zmian (i w związku z tym jest zgodny ze starszymi wersjami programu Visual Studio) i utworzyć plik CSV (wartości rozdzielane przecinkami), który mapuje z par identyfikatorów GUID/identyfikatorów zdefiniowanych w elemencie *. vsct* \<Bitmaps> do pary identyfikatorów GUID/identyfikator.

 Format pliku CSV mapowania to:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Plik CSV jest wdrażany wraz z pakietem, a jego lokalizacja jest określona przez właściwość **IconMappingFilename** atrybutu pakietu **ProvideMenuResource** :

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** jest ścieżką względną niejawnie, w $PackageFolder $ (jak w powyższym przykładzie) lub ścieżką bezwzględną jawnie umieszczoną w katalogu zdefiniowanym przez zmienną środowiskową, taką jak *@ "% USERPROFILE% \dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Jak mogę portu system projektu?
 **Jak dostarczyć ImageMonikers dla projektu**

1. Zaimplementuj **VSHPROPID_SupportsIconMonikers** w **IVsHierarchy** projektu i zwróć wartość true.

2. Zaimplementuj **VSHPROPID_IconMonikerImageList** (jeśli oryginalny projekt jest używany **VSHPROPID_IconImgList**) lub **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (jeśli oryginalny projekt jest używany **VSHPROPID_IconHandle** i **VSHPROPID_OpenFolderIconHandle**).

3. Zmień implementację oryginalnych VSHPROPIDs ikon, aby utworzyć "starsze" wersje ikon, jeśli punkty rozszerzenia ich żądają. **IVsImageService2** udostępnia funkcje niezbędne do uzyskania tych ikon

   **Dodatkowe wymagania dotyczące wersji projektu VB/C#**

   Zaimplementuj **VSHPROPID_SupportsIconMonikers** tylko wtedy, gdy wykryjesz, że projekt jest **najbardziej zewnętrzny**. W przeciwnym razie rzeczywista wersja niedostępna może nie obsługiwać monikerów obrazów w rzeczywistości, a wersja podstawowa może efektywnie "ukryć" niestandardowe obrazy.

   **Jak mogę używać monikerów obrazów w programie CPS?**

   Ustawianie obrazów niestandardowych w programie CPS (Common Project System) można wykonać ręcznie lub za pomocą szablonu elementu, który jest dostarczany z zestawem SDK systemu projektu.

   **Korzystanie z zestawu SDK rozszerzalności systemu projektu**

   Postępuj zgodnie z instrukcjami w polu [podawanie niestandardowych ikon dla typu projektu/typu elementu,](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) aby dostosować obrazy CPS. Więcej informacji na temat CPS można znaleźć w [dokumentacji rozszerzalności systemu projektu programu Visual Studio](https://github.com/Microsoft/VSProjectSystem)

   **Ręcznie używaj ImageMonikers**

4. Zaimplementuj i wyeksportuj Interfejs **IProjectTreeModifier** w systemie projektu.

5. Ustal, który **KnownMoniker** lub niestandardową moniker obrazu, którego chcesz użyć.

6. W metodzie **ApplyModifications** wykonaj następujące czynności w metodzie przed zwróceniem nowego drzewa, podobne do poniższego przykładu:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Jeśli tworzysz nowe drzewo, możesz ustawić niestandardowe obrazy, przekazując odpowiednie monikery do metody NewTree, podobnie jak w poniższym przykładzie:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak mogę skonwertować z rzeczywistego paska obrazu do paska obrazu opartego na monikerach?
 **Muszę obsługiwać HIMAGELISTs**

 Jeśli istnieje już istniejący pasek obrazu dla kodu, który chcesz zaktualizować, aby użyć usługi Image Service, ale są one ograniczone przez interfejsy API, które wymagają pominięcia na listach obrazów, można nadal korzystać z zalet usługi Image Service. Aby utworzyć pasek obrazu oparty na monikerach, wykonaj poniższe kroki, aby utworzyć manifest z istniejących monikerów.

1. Uruchom narzędzie **ManifestFromResources** , przechodząc do niego. Spowoduje to wygenerowanie manifestu dla paska.

   - Zalecane: Podaj nazwę niedomyślną dla manifestu, aby dopasować go do użycia.

2. Jeśli używasz tylko **KnownMonikers**, wykonaj następujące czynności:

   - Zastąp \<Images> sekcję manifestu sekcją \<Images/> .

   - Usuń wszystkie identyfikatory podobrazu (wszystkie elementy z \<imagestrip name> _ # #).

   - Zalecane: Zmień nazwę symbolu AssetsGuid i symbol paska obrazu, aby dopasować go do użycia.

   - Zamień identyfikator GUID każdego z **ContainedImage** na $ (ImageCatalogGuid), Zastąp każdy identyfikator **ContainedImage** z $ ( \<moniker> ) i Dodaj atrybut External = "true" do każdego **ContainedImage**

       - \<moniker> należy zastąpić **KnownMoniker** , który pasuje do obrazu, ale z "KnownMonikers". usunięte z nazwy.

   - Dodaj <zaimportować manifest = "$ (ManifestFolder) \\<względna ścieżka katalogu instalacyjnego do * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/ \*> na początku \<Symbols> sekcji.

       - Ścieżka względna jest określana na podstawie lokalizacji wdrożenia zdefiniowanej w ustawieniach tworzenia dla manifestu.

3. Uruchom narzędzie **ManifestToCode** , aby wygenerować otoki, aby istniejący kod miał moniker, którego można użyć do wysyłania zapytań do usługi Image Service dla paska obrazu.

   - Zalecane: Podaj niedomyślne nazwy otok i przestrzeni nazw, aby odpowiadały ich użyciu.

4. Wykonaj wszystkie czynności konfiguracyjne, tworzenie i wdrażanie oraz inne zmiany kodu do pracy z usługą obrazów i nowymi plikami.

   Przykładowy manifest, łącznie z obrazami wewnętrznymi i zewnętrznymi, aby zobaczyć, jak powinien wyglądać:

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

 **Nie muszę obsługiwać HIMAGELISTs**

1. Określ zestaw **KnownMonikers** , który pasuje do obrazów na pasku obrazu, lub Utwórz własne monikery dla obrazów na pasku obrazu.

2. Zaktualizuj dowolne mapowanie użyte do pobrania obrazu z wymaganego indeksu na pasku obrazu, aby użyć monikerów.

3. Zaktualizuj swój kod, aby użyć usługi Image Service do żądania monikery za pośrednictwem zaktualizowanego mapowania. (Może to oznaczać, że aktualizacja **CrispImages** dla kodu zarządzanego lub żądanie HBITMAPs lub HICONs z usługi obrazów i przekazanie ich na kod natywny).

## <a name="testing-your-images"></a>Testowanie obrazów
 Możesz użyć narzędzia Podgląd biblioteki obrazów do testowania manifestów obrazów, aby upewnić się, że wszystko jest poprawnie utworzone. Narzędzie można znaleźć w [zestawie SDK programu Visual Studio 2015](visual-studio-sdk.md). Dokumentacja tego narzędzia i innych można znaleźć [tutaj](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true).

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="samples"></a>Samples
 Niektóre przykłady programu Visual Studio w witrynie GitHub zostały zaktualizowane, aby pokazać, jak korzystać z usługi Image Service jako części różnych punktów rozszerzalności programu Visual Studio.

 Zapoznaj [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) się z najnowszymi przykładami.

### <a name="tooling"></a>Narzędzia
 Zestaw narzędzi obsługi dla usługi Image został utworzony w celu ułatwienia tworzenia/aktualizowania interfejsu użytkownika, który współpracuje z usługą obrazu. Aby uzyskać więcej informacji na temat każdego narzędzia, zapoznaj się z dokumentacją dostarczoną z narzędziami. Narzędzia są dołączone jako część [zestawu SDK programu Visual Studio 2015](visual-studio-sdk.md).

 **ManifestFromResources**

 Narzędzie Manifest from Resources pobiera listę zasobów obrazów (PNG lub XAML) i generuje plik manifestu obrazu na potrzeby używania tych obrazów z usługą Image Service.

 **ManifestToCode**

 Narzędzie Manifest to Code pobiera plik manifestu obrazu i generuje plik otoki do odwoływania się do wartości manifestu w plikach Code (C++, C# lub VB) lub *vsct* .

 **ImageLibraryViewer**

 Narzędzie do przeglądania bibliotek obrazów może ładować manifesty obrazów i umożliwia użytkownikowi manipulowanie nimi w taki sam sposób, w jaki program Visual Studio może upewnić się, że manifest został poprawnie utworzony. Użytkownik może zmienić ustawienia tła, rozmiarów, ustawienia DPI, duży kontrast i innych ustawień. Wyświetla również informacje o ładowaniu, aby znaleźć błędy w manifestach i wyświetlić informacje źródłowe dla każdego obrazu w manifeście.

## <a name="faq"></a>Często zadawane pytania

- Czy istnieją zależności, które należy uwzględnić podczas ładowania \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> ?

  - Ustaw EmbedInteropTypes = "true" we wszystkich bibliotekach DLL międzyoperacyjności.

- Jak mogę wdrożyć manifest obrazu z moim rozszerzeniem?

  - Dodaj plik *. imagemanifest* do projektu.

  - Ustaw wartość "Dołącz w VSIX" do wartości true.

- Aktualizujem mój system projektu CPS. Co się stało z **obrazami** i **StockIconService**?

  - Zostały one usunięte, gdy serwer CPS został zaktualizowany do używania monikerów. Nie musisz już wywoływać **StockIconService**, po prostu Przekaż żądane **KnownMoniker** do metody lub właściwości przy użyciu metody rozszerzenia **ToProjectSystemType ()** w narzędziu CPS. Można znaleźć mapowanie z **obrazu** **KnownMonikers** poniżej:

    |**ImageName**|**KnownMoniker**|
    |-|-|
    |ImageName. OfflineWebApp|KnownImageIds. Web|
    |ImageName. WebReferencesFolder|KnownImageIds. Web|
    |ImageName. OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName. ReferenceFolder|KnownImageIds. Reference|
    |ImageName. Reference|KnownImageIds. Reference|
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName. DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |Obraz. folder|KnownImageIds.FolderClosed|
    |ImageName. OpenFolder|KnownImageIds.FolderOpened|
    |ImageName. ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName. OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName. ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName. DependentFile|KnownImageIds.GenerateFile|
    |ImageName. MissingFile|KnownImageIds.DocumentWarning|
    |ImageName. WindowsForm|KnownImageIds.WindowsForm|
    |ImageName. WindowsUserControl|KnownImageIds. UserControl|
    |ImageName. WindowsComponent|KnownImageIds.ComponentFile|
    |Schemat ImageName.Xml|Schemat KnownImageIds.XML|
    |Plik ImageName.Xml|Plik KnownImageIds.XML|
    |ImageName. WebForm|KnownImageIds. Web|
    |ImageName. WebService|KnownImageIds. WebService|
    |ImageName. WebUserControl|KnownImageIds. WebUserControl|
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName. AspPage|KnownImageIds.ASPFile|
    |ImageName. GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName. Webconfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName. StyleSheet|KnownImageIds. StyleSheet|
    |ImageName. ScriptFile|Skrypt KnownImageIds.JS|
    |ImageName. textfile|KnownImageIds.Document|
    |ImageName. SettingsFile|KnownImageIds. Settings|
    |ImageName. resources|KnownImageIds.DocumentGroup|
    |Obraz. Mapa bitowa|KnownImageIds. Image|
    |Ilustracja. ikona|KnownImageIds.IconFile|
    |ImageName. Image|KnownImageIds. Image|
    |ImageName. ImageMap|KnownImageIds.ImageMapFile|
    |ImageName. XWorld|KnownImageIds.XWorldFile|
    |ImageName. audio|KnownImageIds. Sound|
    |Obraz. wideo|KnownImageIds. Media|
    |ImageName.Cab|Projekt KnownImageIds.CAB|
    |ImageName. jar|KnownImageIds. JARFile|
    |ImageName. DataEnvironment|KnownImageIds. DataTable|
    |ImageName. PreviewFile|KnownImageIds. Report|
    |ImageName. DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName. XsltFile|KnownImageIds. XSLTransform|
    |ImageName. Cursor|KnownImageIds.CursorFile|
    |ImageName. AppDesignerFolder|KnownImageIds. Property|
    |ImageName. Data|KnownImageIds. Database|
    |ImageName. Application|KnownImageIds. Application|
    |ImageName. DataSet|KnownImageIds. Database|
    |ImageName. pfx|KnownImageIds. Certificate|
    |ImageName. snk|KnownImageIds. Rule|
    |ImageName. VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName. Empty|KnownImageIds. Blank|
    |ImageName. MissingFolder|KnownImageIds.FolderOffline|
    |ImageName. SharedImportReference|KnownImageIds.SharedProject|
    |ImageName. SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Aktualizujem dostawcę listy uzupełniania. Jakie **KnownMonikers** pasuje do starych wartości **StandardGlyphGroup** i **StandardGlyph** ?

    |Nazwa|Nazwa|Nazwa|
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Odwołanie|
    |GlyphLibrary||Biblioteka|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Oknie dialogowym|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Fragment kodu|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Rekursja|
    |GlyphXmlItem||Tag|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||Dokument|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||Element xmldescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
