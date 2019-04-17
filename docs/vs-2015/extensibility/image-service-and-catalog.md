---
title: Obraz usługi i wykaz | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e40401b533d5fcaad8dc9bb4530580608efaad9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670228"
---
# <a name="image-service-and-catalog"></a>Usługa obrazów i katalog obrazów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten podręcznik zawiera wskazówki i najlepsze rozwiązania dotyczące usługi obrazu w usłudze Visual Studio i katalog obrazów wprowadzone w programie Visual Studio 2015.  

 Usługa obrazów, wprowadzona w programie Visual Studio 2015 umożliwia deweloperom pobieranie najlepszych obrazów związanych z urządzeniem i motyw wybrany przez użytkownika do wyświetlania obrazu, w tym poprawny motywy dla kontekstu, w którym są wyświetlane. Wdrażanie usługi obrazów pomoże wyeliminuj główne problemy dotyczące konserwacji zasobów, HDPI skalowanie i motywów.  

|||  
|-|-|  
|**Problemy z już dziś**|**Rozwiązania**|  
|Mieszania kolorów tła|Wbudowane przenikaniem alfa|  
|Obrazy motywów (niektóre)|Motyw metadanych|  
|Trybu wysokiego kontrastu|Zasoby alternatywne o wysokim kontraście|  
|Potrzebujesz wielu zasobów dla różnych rozdzielczości DPI|Można wybierać zasobów przy użyciu opartego na wektorach rezerwowe|  
|Zduplikowane obrazów|Identyfikator jednego na koncepcji obrazu|  

 Dlaczego warto przyjąć Usługa obrazów?  

- Zawsze uzyskać najnowszego obrazu "doskonałe rozwiązanie pikseli" z programu Visual Studio  

- Możesz przesłać i korzystanie z własnych obrazów  

- Nie trzeba przetestować obrazy się kiedy Windows dodaje nowe Skalowanie DPI  

- Adres stare architektury przeszkody w swojej implementacji.  

  Narzędzi programu Visual Studio shell przed i po nim za pomocą usługi obrazów:  

  ![Usługa obrazów przed i po nim](../extensibility/media/image-service-before-and-after.png "Usługa obrazów przed i po nim")  

## <a name="how-it-works"></a>Jak to działa  
 Usługa obrazów można podać obraz mapy bitowej nadające się do dowolnej obsługiwanej architektury interfejsu użytkownika:  

- WPF: BitmapSource  

- Formularze winform: System.Drawing.Bitmap  

- Win32: HBITMAP  

  Diagram przepływu usługi obrazów  

  ![Obraz diagramu przepływu usługi](../extensibility/media/image-service-flow-diagram.png "obrazu diagramu przepływu usługi")  

  **Monikery obrazu**  

  Moniker obrazu (lub krótkiej nazwy w skrócie) jest pary identyfikator GUID/ID, który unikatowo identyfikuje zasób obrazu lub obraz listy zasobów w bibliotece obrazów.  

  **Monikery znane**  

  Zestaw monikerów obrazów znajdujących się w katalogu obrazu w usłudze Visual Studio i publicznie usprawnia według dowolnego składnika programu Visual Studio lub rozszerzenia.  

  **Pliki manifestu obrazu**  

  Pliki manifestu (.imagemanifest) obrazów są pliki XML, które definiują zestaw zasoby obrazów, monikerów, które reprezentują te zasoby i rzeczywistego obrazu lub obrazów, które reprezentują każdego zasobu. Manifesty obrazu można zdefiniować obrazy autonomiczne lub listy obrazów do obsługi starszych wersji interfejsu użytkownika. Ponadto są atrybuty, które mogą być ustawione na zasób lub na poszczególnych obrazów za każdy zasób do zmiany, kiedy i jak te zasoby są wyświetlane.  

  **Obraz schematu manifestu**  

  Manifest pełny obraz wygląda następująco:  

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

 **Symbols**  

 Jak zwiększyć czytelność i konserwacja pomocy, manifestu obrazu można użyć symboli dla wartości atrybutów. Symbole są zdefiniowane następująco:  

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
|**Element podrzędny**|**Definicja**|  
|Import|Importuje symbole dany plik manifestu do użycia w bieżącym manifeście|  
|Guid|Symbol reprezentuje identyfikator GUID i muszą być zgodne, formatowania identyfikatora GUID|  
|Identyfikator|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą.|  
|String|Symbol reprezentuje wartość dowolny ciąg|  

 Symbole jest rozróżniana wielkość liter i odwołania, przy użyciu składni $(symbol-name):  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą one być używane w atrybucie Uri \<źródło > lub \<Import > element ścieżki odwołania na komputerze lokalnym.  

|||  
|-|-|  
|**Symbol**|**Opis**|  
|CommonProgramFiles|Wartość zmiennej środowiskowej % CommonProgramFiles %|  
|LocalAppData|Wartość zmiennej środowiskowej % LocalAppData %|  
|ManifestFolder|Folder zawierający plik manifestu|  
|Moje dokumenty|Pełna ścieżka folderu Moje dokumenty bieżącego użytkownika|  
|ProgramFiles|Wartość zmiennej środowiskowej % ProgramFiles %|  
|System|Do folderu Windows\System32|  
|WinDir|Wartość zmiennej środowiskowej % WinDir %|  

 **Obraz**  

 \<Obrazu > element Określa obraz, który można się odwoływać za krótka. Identyfikator GUID i identyfikator razem tworzą monikera obrazu. Moniker obrazu musi być unikatowa w biblioteki całego obrazu. Jeśli więcej niż jeden obraz ma monikera danego, pierwszy z nich podczas kompilowania biblioteki jest ten, który jest zachowywana.  

 Musi zawierać co najmniej jedno źródło. Niezależny od rozmiaru źródeł, który zapewni najlepsze wyniki do szerokiego zakresu rozmiarów, ale nie są wymagane. Jeśli usługa zostanie poproszony o obrazu o rozmiarze nie jest zdefiniowany w \<obraz > elementu i nie istnieje źródło niezależny od rozmiaru, usługa Wybierz najlepsze źródło określonego rozmiaru i przeprowadzi jej skalowanie do żądanego rozmiaru.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Guid|[Wymagane] Identyfikator GUID część monikera obrazu|  
|Identyfikator|[Wymagane] Część Identyfikatora monikera obrazu|  
|AllowColorInversion|[Opcjonalna, domyślne true] Wskazuje, czy obraz, który może mieć jego kolorów programowo odwrócona, gdy jest używana na ciemnym tle.|  

 **Element źródłowy**  

 \<Źródło > element definiuje pojedynczy źródła zasób obrazu (XAML i PNG).  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  

|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Atrybut** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **Definicja**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      Identyfikator URI      |                                                                                                                                                                                                                                                                                                               [Wymagane] Identyfikator URI, który określa, gdzie można załadować obrazu z. Może to być jedna z następujących czynności:<br /><br /> -A [identyfikatora URI pakietu](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) za pomocą aplikacji: / / / urzędu<br />— Odwołanie do zasobu składnik bezwzględne<br />— Ścieżka do pliku zawierającego zasobu natywnego                                                                                                                                                                                                                                                                                                               |
|  Tło   | [Opcjonalnie] Wskazuje, jakie na rodzaju tła, których źródłem jest przeznaczony do użycia.<br /><br /> Może to być jedna z następujących czynności:<br /><br /> *Światła:* Źródło może być używane na tle światła.<br /><br /> <em>Ciemny:</em>źródło może być używany na ciemnym tle.<br /><br /> *HighContrast:* Źródło może służyć w dowolnym tła w trybie dużego kontrastu.<br /><br /> *HighContrastLight:* Źródło może być używane na tle światła w trybie dużego kontrastu.<br /><br /> *HighContrastDark:* Źródło może być używane na ciemnym tle w trybie dużego kontrastu.<br /><br /> W przypadku pominięcia atrybut tła źródła może służyć w dowolnym tła.<br /><br /> Jeśli tło jest *światła*, *ciemny*, *HighContrastLight*, lub *HighContrastDark*, kolory źródła nigdy nie jest odwrócona. Jeśli w tle jest pominięty lub ustawiony jako *HighContrast*, odwracanie kolorów źródło jest kontrolowane przez obraz **AllowColorInversion** atrybutu. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 A \<źródło > element może mieć dokładnie jeden następujące opcjonalne elementy podrzędne:  

||||  
|-|-|-|  
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|  
|\<Rozmiar >|Wartość|Źródła będą używane dla obrazów o danym rozmiarze (w jednostkach urządzenia). Obraz, który będzie mieć kształtu kwadratu.|  
|\<SizeRange>|MinSize, MaxSize|Źródła będą używane dla obrazów z MinSize MaxSize (w jednostkach urządzenia) (włącznie). Obraz, który będzie mieć kształtu kwadratu.|  
|\<Wymiary >|Szerokość, wysokość|Źródła będą używane dla obrazów o danym szerokość i wysokość (w jednostkach urządzenia).|  
|\<DimensionRange >|Wartości elementu MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródła będą używane dla obrazów z minimalną szerokość/wysokość, szerokość/wysokość maksymalna (w jednostkach urządzenia) (włącznie).|  

 A \<źródło > element może mieć również opcjonalny \<NativeResource > podelement, który definiuje \<źródło > który jest ładowany z natywnego zestawu, a nie zestaw zarządzany.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Typ|[Wymagane] Typ zasobu natywnego, XAML lub PNG|  
|Identyfikator|[Wymagane] Całkowitą część Identyfikatora zasobu natywnego|  

 **ImageList**  

 \<ImageList > element definiuje kolekcję obrazów, które mogą być zwracane w pojedynczej taśmy. Pasek bazuje na żądanie, zgodnie z potrzebami.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Guid|[Wymagane] Identyfikator GUID część monikera obrazu|  
|Identyfikator|[Wymagane] Część Identyfikatora monikera obrazu|  
|Zewnętrzna|[Opcjonalnie, wartość domyślna to false] Wskazuje, czy monikera obrazu odwołuje się do obrazu w bieżącym manifeście.|  

 Moniker obrazu zawarte nie musi odwoływać się do obrazu, który został zdefiniowany w bieżącym manifeście. Jeśli nie można odnaleźć obrazu zawarte w bibliotece obrazów, obraz pusty symbol zastępczy zostanie użyty w tym miejscu.  

## <a name="using-the-image-service"></a>Za pomocą usługi obrazów  

### <a name="first-steps-managed"></a>Pierwsze kroki (zarządzane)  
 Aby użyć usługi obrazu, należy dodać odwołania do niektóre lub wszystkie z następujących zestawów do projektu:  

-   **Microsoft.VisualStudio.ImageCatalog.dll**  

    -   Wymagane w przypadku użycia katalogu wbudowanego obrazu KnownMonikers  

-   **Microsoft.VisualStudio.Imaging.dll**  

    -   Wymagane w przypadku użycia **CrispImage** i **ImageThemingUtilities** w interfejsie użytkownika WPF  

-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  

    -   Wymagane w przypadku użycia **ImageMoniker** i **Structsize** typów  

    -   **EmbedInteropTypes** powinna być ustawiona na wartość true  

-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  

    -   Wymagane w przypadku użycia **IVsImageService2** typu  

    -   **EmbedInteropTypes** powinna być ustawiona na wartość true  

-   **Microsoft.VisualStudio.Utilities.dll**  

    -   Wymagane w przypadku użycia **BrushToColorConverter** dla ImageThemingUtilities. **ImageBackgroundColor** w interfejsie użytkownika WPF  

-   **Microsoft.VisualStudio.Shell. \<VSVersion >.0**  

    -   Wymagane w przypadku użycia **IVsUIObject** typu  

-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  

    -   Wymagane w przypadku użycia pomocników związane z WinForms interfejsu użytkownika  

    -   **EmbedInteropTypes** powinna być ustawiona na wartość true  

### <a name="first-steps-native"></a>Pierwsze kroki (native)  
 Aby korzystać z usługi obrazów, musisz zawiera niektóre lub wszystkie następujące nagłówki do projektu:  

-   **KnownImageIds.h**  

    -   Wymagane w przypadku użycia katalogu wbudowanego obrazu **KnownMonikers**, ale nie można użyć **ImageMoniker** typu, na przykład gdy zwracanie wartości z kolekcji **IVsHierarchy GetGuidProperty**lub **GetProperty** wywołania.  

-   **KnownMonikers.h**  

    -   Wymagane w przypadku użycia katalogu wbudowanego obrazu **KnownMonikers**.  

-   **ImageParameters140.h**  

    -   Wymagane w przypadku użycia **ImageMoniker** i **Structsize** typów.  

-   **VSShell140.h**  

    -   Wymagane w przypadku użycia **IVsImageService2** typu.  

-   **ImageThemingUtilities.h**  

    -   Wymagane, jeśli nie jesteś umożliwiające Usługa obrazów obsługi motywów dla Ciebie.  

    -   Nie należy używać tego pliku nagłówkowego, jeśli usługa obrazu może obsługiwać swoje motywów obrazu.  

-   **VSUIDPIHelper.h**  

    -   Wymagane w przypadku użycia pomocników DPI można pobrać bieżącego DPI.  

## <a name="how-do-i-write-new-wpf-ui"></a>Jak napisać nowy interfejs użytkownika WPF  

1.  Start przez dodanie odwołania do zestawów wymagane powyżej pierwsze kroki sekcji do projektu. Nie musisz dodać wszystkie z nich, więc Dodaj tylko odwołania, które są potrzebne. (Uwaga: Jeśli używasz lub mają dostęp do **kolory** zamiast **pędzle**, możesz przejść odwołanie do **narzędzia**, ponieważ nie ma potrzeby konwerter.)  

2.  Wybierz odpowiedni obraz i pobrać jego nazwie. Użyj **KnownMoniker**, lub skorzystać z własnego, jeśli masz własne niestandardowe obrazy i monikerów.  

3.  Dodaj **CrispImages** do Twojej XAML. (Zobacz poniżej przykład).  

4.  Ustaw **ImageThemingUtilities.ImageBackgroundColor** właściwość w hierarchii interfejsu użytkownika. (Ten należy ustawić w lokalizacji, gdzie kolor tła jest znany, nie musi być w systemie **CrispImage**.) (Zobacz poniżej przykład).  

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

 **Jak zaktualizować istniejące WPF UI?**  

 Aktualizowanie istniejących WPF UI jest stosunkowo prosty proces, który obejmuje trzy podstawowe kroki:  

1.  Zamień wszystkie \<obraz > elementów w interfejsie użytkownika za pomocą \<CrispImage > elementy  

2.  Zmień wszystkie atrybuty źródła krótkiej nazwy atrybutów  

    -   Jeśli obraz nie ulega zmianie i jest używana **KnownMonikers**, statycznie powiązać tę właściwość, aby **KnownMoniker**. (Zobacz przykład powyżej).  

    -   Jeśli używasz swój własny obraz niestandardowy obraz, który nigdy się nie zmienia, następnie statycznie powiązać własne krótkiej nazwy.  

    -   Jeśli obraz mogą ulec zmianie, należy powiązać atrybutu monikera do właściwości kodu, która powiadamia o zmianie właściwości.  

3.  Gdzieś w hierarchii interfejsu użytkownika, ustaw **ImageThemingUtilities.ImageBackgroundColor** aby upewnić się, że odwrócenie kolorów działa prawidłowo.  

    -   Może to wymagać stosowania **BrushToColorConverter** klasy. (Zobacz przykład powyżej).  

## <a name="how-do-i-update-win32-ui"></a>Jak zaktualizować Win32 interfejsu użytkownika?  
 Dodaj następujący kod do kodu, wszędzie tam, gdzie zastąpienie pierwotne ładowania obrazów. Przełącz wartości dla zwracania HBITMAPs a HICONs a HIMAGELIST zgodnie z potrzebami.  

 **Get-service obrazu**  

```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  

 **Żądanie obrazu**  

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

## <a name="how-do-i-update-winforms-ui"></a>Jak zaktualizować WinForms interfejsu użytkownika?  
 Dodaj następujący kod do kodu, wszędzie tam, gdzie zastąpienie pierwotne ładowania obrazów. Przełącz wartości dla zwracania bitmap i ikon, zgodnie z potrzebami.  

 **Pomocne przy użyciu instrukcji**  

```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  

 **Get-service obrazu**  

```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  

```  

 **Żądanie dotyczące obrazu**  

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak używać obrazu monikerów w nowym oknie narzędzia?  
 Szablon projektu pakietu VSIX został zaktualizowany na potrzeby programu Visual Studio 2015. Aby utworzyć nowe okno narzędzi, kliknij prawym przyciskiem myszy na projekt VSIX, a następnie wybierz pozycję "Dodaj nowy element..." (Ctrl+Shift+A). W węźle rozszerzalności dla języka projektu, wybierz pozycję "Okna narzędzi niestandardowych" nazwij okna narzędzi, a następnie naciśnij przycisk "Dodaj".  

 Są to kluczowe miejsca, do używają monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:  

1. Karta okna narzędzia, gdy karty małych wystarczająco (również stosowane w przełączniku okna Ctrl + Tab).  

    Dodaj następujący wiersz do konstruktora dla klasy, która pochodzi od klasy **obiektu ToolWindowPane** typu:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. Polecenie, aby otworzyć okno narzędzia.  

    W pliku vsct pakietu należy edytować przycisku polecenia z okna narzędzi:  

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

   **Jak używać obrazu monikerów w istniejącym oknie Narzędzie?**  

   Aktualizowanie istniejącego okna narzędzia do używają monikerów obrazu jest podobna do procedury służące do tworzenia nowego okna narzędzia.  

   Są to kluczowe miejsca, do używają monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:  

3. Karta okna narzędzia, gdy karty małych wystarczająco (również stosowane w przełączniku okna Ctrl + Tab).  

   1.  Usuń następujące wiersze (jeśli istnieją) w konstruktorze klasy, która pochodzi od klasy **obiektu ToolWindowPane** typu:  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2.  Zobacz krok #1 "Jak monikerów obrazu użycia w nowym oknie narzędzia?" powyższej sekcji.  

4. Polecenie, aby otworzyć okno narzędzia.  

   -   Zobacz krok #2 "Jak monikerów obrazu użycia w nowym oknie narzędzia?" powyższej sekcji.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Jak używać monikerów obraz w pliku vsct?  
 Zaktualizuj plik vsct, wskazane przez komentarze poniżej wiersze:  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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

 **Co zrobić, jeśli Moja pliku vsct musi także zostać odczytany przez starsze wersje programu Visual Studio?**  

 Starsze wersje programu Visual Studio nie rozpoznają **IconIsMoniker** polecenia flagi. Obrazy z usługi obrazów można użyć w wersjach programu Visual Studio, które go obsługują, ale nadal używać obrazów w starym stylu w starszych wersjach programu Visual Studio. Aby to zrobić, możesz pozostawić pliku vsct bez zmian (i w związku z tym zgodne ze starszymi wersjami programu Visual Studio) i utworzyć plik CSV (wartości rozdzielane przecinkami), który mapuje z par identyfikator/GUID zdefiniowanego w pliku vsct \<mapy bitowe > elementu obrazu Moniker identyfikator GUID/pary.  

 Format pliku CSV mapowanie jest:  

```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  

 Plik CSV jest wdrażana przy użyciu pakietu i jego lokalizacja jest określona przez **IconMappingFilename** właściwość **ProvideMenuResource** atrybut pakietu:  

```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  

 **IconMappingFilename** jest względną ścieżką niejawnie dostęp do konta root na $PackageFolder$ (tak jak w powyższym przykładzie) lub ścieżka bezwzględna jawnie umieszczone w katalogu zdefiniowany przez zmienną środowiskową, takich jak @"%UserProfile%\ dir1\dir2\MyMappingFile.csv".  

## <a name="how-do-i-port-a-project-system"></a>Jak port system projektu?  
 **Jak przekazać ImageMonikers dla projektu**  

1. Implementowanie **VSHPROPID_SupportsIconMonikers** nad projektem **IVsHierarchy**i zwraca wartość true.  

2. Implementowanie albo **VSHPROPID_IconMonikerImageList** (Jeśli oryginalny projekt **VSHPROPID_IconImgList**) lub **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (Jeśli oryginalny projekt  **VSHPROPID_IconHandle** i **VSHPROPID_OpenFolderIconHandle**).  

3. Zmień implementację oryginalnego VSHPROPIDs ikon w celu utworzenia "starszych" wersje ikony, jeśli punkty rozszerzenia zażądać ich. **IVsImageService2** udostępnia funkcje niezbędne do doprowadzenia tych ikon  

   **Dodatkowe wymagania dla języka VB / odmian systemu projektu języka C#**  

   Zawierać implementację tylko **VSHPROPID_SupportsIconMonikers** jeśli wykryje, że projekt jest **peryferyjnych flavor**. W przeciwnym razie rzeczywiste flavor peryferyjnych mogą nie obsługiwać monikerów obrazu w rzeczywistości, a Twoja wersja podstawowa mogą skutecznie "hide" dostosowanych obrazów.  

   **Jak używać monikerów obrazu w systemie CPS?**  

   Ustawienia niestandardowe obrazy w systemie CPS (Common Project System) może odbywać się ręcznie lub za pomocą szablonu elementu, który jest dostarczany z zestawem SDK rozszerzalność systemu projektów.  

   **Za pomocą funkcji rozszerzalności System projektu zestawu SDK**  

   Postępuj zgodnie z instrukcjami w artykule [Podaj niestandardowe ikony dla typu elementu typu projektu](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) dostosowywania obrazów CPS. Więcej informacji na temat CPS znajduje się w temacie [projektu systemu rozszerzalności dokumentacja programu Visual Studio](https://github.com/Microsoft/VSProjectSystem)  

   **Użyj ręcznie ImageMonikers**  

4. Implementowanie i eksportowanie **IProjectTreeModifier** interfejs w systemie projektu.  

5. Określenie **KnownMoniker** lub monikera niestandardowy obraz, którego chcesz użyć.  

6. W **ApplyModifications** metody, wykonaj następujące czynności gdzieś w metodzie przed zwróceniem nowego drzewa, podobnie jak poniższym przykładzie:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  

7. W przypadku tworzenia nowego drzewa, można ustawić niestandardowych obrazów, przekazując żądaną monikerów NewTree do metody, podobnie jak poniższym przykładzie:  

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak przekonwertować z paska rzeczywistego obrazu na pasek oparte na monikera obrazu?  
 **Potrzebuję pomocy technicznej HIMAGELISTs**  

 Zalety usługi obrazów można uzyskać nawet w sytuacji, w przypadku istniejącego paska obrazów w kodzie, który ma zostać zaktualizowany do korzystania z usługi obrazu, ale są ograniczone przez interfejsy API, które wymagają przekazywania wokół list obrazów. Aby utworzyć pasek oparte na monikera obrazu, wykonaj poniższe kroki, aby utworzyć manifest z istniejących monikerów.  

1. Uruchom **ManifestFromResources** narzędzia, podając mu paska obrazów. Spowoduje to wygenerowanie manifestu paska.  

   -   Zalecane: Podaj nazwę innego niż domyślny manifest do własnych jej użycie.  

2. Jeśli używane są tylko **KnownMonikers**, wykonaj następujące czynności:  

   -   Zastąp \<obrazów > sekcji manifestu z \<obrazów / >.  

   -   Usuń wszystkie subimage identyfikatorów (wszystko z \<imagestrip name > _ ##).  

   -   Zalecane: Zmień nazwę symbolu AssetsGuid i symbol paska obraz do potrzeb ich użycie.  

   -   Zastąp każde **ContainedImage**firmy identyfikatora GUID $(ImageCatalogGuid), Zastąp każde **ContainedImage**firmy identyfikator z $(\<moniker >) i Dodaj atrybut zewnętrznych = "true" do każdego **ContainedImage**  

       -   \<Moniker > należy zastąpić je klasą **KnownMoniker** odpowiadającej obrazu, ale z "KnownMonikers." usunięte z nazwy.  

   -   Dodaj < Import Manifest="$(ManifestFolder)\\< względna instalacji ścieżkę katalogu do\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> na początku \<symbole > sekcji.  

       -   Ścieżka względna jest ustalany w lokalizacji wdrożenia zdefiniowany w ustawieniach tworzenia manifestu.  

3. Uruchom **ManifestToCode** narzędzie do generowania otoki, aby istniejący kod jest krótka, można użyć do zapytania usługi obrazów dla paska obrazów.  

   -   Zalecane: Podaj nazwy innej niż domyślna dla otok i przestrzenie nazw w zależności od ich użycia.  

4. Wykonaj wszystkie dodaje, tworzenia instalacji/wdrażania i innych zmian w kodzie do pracy z usługą obrazu i nowe pliki.  

   W tym obrazy wewnętrzne i zewnętrzne, aby zobaczyć, co powinno to wyglądać podobnie manifestu próbki:  

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

 **Nie muszę obsługuje HIMAGELISTs**  

1.  Określa zestaw **KnownMonikers** dopasowania obrazów w swojej paska obrazów lub utworzyć własne monikery dla obrazów w swojej paska obrazów.  

2.  Zaktualizuj dowolne mapowania używane do pobierania obrazu pod indeksem wymagane paska obrazów zamiast tego użyć monikerów.  

3.  Zaktualizuj kod w celu żądania monikerów za pośrednictwem zaktualizowane mapowania przy użyciu usługi obrazu. (Może to oznaczać, aktualizacja do **CrispImages** dla zarządzanego kodu, lub żądanie HBITMAPs lub HICONs od usługi obrazów i przekazywania ich wokół dla kodu natywnego.)  

## <a name="testing-your-images"></a>Testowanie obrazów  
 Narzędzie przeglądarka biblioteki obrazów do przetestowania Twojej manifesty obrazu, aby upewnić się, że wszystko jest prawidłowo przypisany. Można znaleźć narzędzia w [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Można znaleźć dokumentację dla tego narzędzia i inne [tutaj](https://aka.ms/VSImageThemeTools).  

## <a name="additional-resources"></a>Dodatkowe zasoby  

### <a name="samples"></a>Przykłady  
 Aby pokazać, jak używać usługi obrazów jako część różne punkty rozszerzalności programu Visual Studio zostały zaktualizowane kilka przykładów programu Visual Studio w witrynie GitHub.  

 Sprawdź [ http://github.com/Microsoft/VSSDK-Extensibility-Samples ](http://github.com/Microsoft/VSSDK-Extensibility-Samples) najnowsze przykłady.  

### <a name="tooling"></a>Narzędzia  
 Zestaw narzędzi do pomocy technicznej dla usługi obrazów utworzono ułatwiające tworzenie/Aktualizowanie interfejsu użytkownika, który współpracuje z usługą obrazu. Aby uzyskać więcej informacji na temat każdego z narzędzi dokumentacji dołączoną do narzędzia. Narzędzia są dołączane jako część [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  

 **ManifestFromResources**  

 Manifest za pomocą narzędzia zasobów przyjmuje listę zasobów obrazu (PNG lub XAML) i generuje plik manifestu obrazu przy użyciu tych obrazów w usłudze obrazu.  

 **ManifestToCode**  

 Manifest, aby narzędzie do obsługi kodu przyjmuje plik manifestu obrazu i generuje plik otoki do odwoływania się do wartości kodu (C++, C# lub VB) lub .vsct — pliki z manifestu.  

 **ImageLibraryViewer**  

 Narzędzia przeglądarka biblioteki obrazów można załadować obrazu manifesty i umożliwia użytkownikowi nimi manipulować w taki sam sposób, czy program Visual Studio, upewnij się, że manifest składowe, została utworzona poprawnie. Użytkownik może zmienić tła, rozmiary, ustawienie DPI, duży kontrast i inne ustawienia. Również Wyświetla informacje ładowania, aby znaleźć błędy w manifestach i wyświetla informacje dotyczące źródła dla każdego obrazu w manifeście.  

## <a name="faq"></a>Najczęściej zadawane pytania  

-   Czy istnieją jakieś zależności, które należy uwzględnić podczas ładowania \<Include="Microsoft.VisualStudio.* odwołania. Interop.14.0.DesignTime"/ >?  

    -   Ustaw EmbedInteropTypes = "true", na wszystkich bibliotek DLLs międzyoperacyjnego.  

-   Jak wdrożyć manifestu obrazu z Moje rozszerzenie?  

    -   Dodaj plik .imagemanifest do projektu.  

    -   "Uwzględnione w VSIX" należy ustawić na wartość True.  

-   Aktualizuję projekt systemu CPS. Co się stało z **ImageName** i **StockIconService**?  

    -   o te zostały usunięte, gdy CPS został zaktualizowany do używają monikerów. Nie są już potrzebne do wywoływania **StockIconService**, po prostu Przekaż żądany **KnownMoniker** metodę lub właściwość za pomocą **ToProjectSystemType()** metody rozszerzenia w narzędzia CPS. Można znaleźć mapowania z **ImageName** do **KnownMonikers** poniżej:  

        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  

    -   Aktualizuję świadczącej listy uzupełniania. Co **KnownMonikers** pasuje do starego **StandardGlyphGroup** i **StandardGlyph** wartości?  

        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
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
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
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
        |GlyphAssembly||Tematy pomocy|  
        |GlyphLibrary||Biblioteka|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Okno dialogowe|  
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
        |GlyphJSharpProject||Elementu DocumentCollection|  
        |GlyphJSharpDocument||dokument|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||Użyciu CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||Użyciu CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|
