---
title: Odtwarzanie z zasobów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 286ec5b71691777af601c00e26c2db5772bd5f1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993978"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Manifest za pomocą narzędzia zasobów jest aplikacja konsolowa która przyjmuje listę zasobów obrazu (PNG lub .xaml plików) i generuje plik .imagemanifest umożliwiająca tych obrazów do użycia z usługą obrazów programu Visual Studio. To narzędzie można dodatkowo dodać obrazy do istniejących .imagemanifest. To narzędzie jest przydatne w przypadku dodawania wysokiej rozdzielczości DPI i motywów obsługę dla obrazów w celu rozszerzenia programu Visual Studio. Pliku wygenerowanego .imagemanifest należy objęte i wdrażane jako część rozszerzenia programu Visual Studio (.vsix).  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 **Składnia**  
  
 ManifestFromResources /resources:\<katalog1 >;\< Img1 >/Assembly:\<Nazwa_zestawu > \<argumentów opcjonalnych >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Nazwa przełącznika**|**Uwagi**|**Wymagane lub opcjonalne**|  
|/Resources|Rozdzielana średnikami lista obrazów lub katalogi. Ta lista zawsze powinna zawierać pełną listę obrazów, które będą znajdować się w manifeście. Jeśli tylko część listy wpisów nie uwzględnione zostaną utracone.<br /><br /> Jeśli plik danego zasobu jest paska obrazów, narzędzie będzie podzielić ją na oddzielne obrazy przed dodaniem każdego subimage do manifestu.<br /><br /> Jeśli obraz jest plikiem PNG, zaleca się, aby narzędzie może wypełnić odpowiednie atrybuty obrazu możesz sformatować nazwą jak pokazano to: \<Nazwa >. \<Szerokość >. \<Wysokość > PNG.|Wymagane|  
|/ Assembly|Nazwa zestawu zarządzanego (bez rozszerzenia) lub ścieżkę środowiska uruchomieniowego natywnego zestawu, który obsługuje zasoby (względem lokalizacji środowiska uruchomieniowego manifest).|Wymagane|  
|/ manifest|Nazwa do nadania .imagemanifest wygenerowany plik. Może to również obejmować ścieżką bezwzględną ani względną, aby utworzyć plik w innej lokalizacji. Domyślna nazwa jest zgodna z nazwą zestawu.<br /><br /> Wartość domyślna: \<Bieżący katalog >\\< zestawu\>.imagemanifest|Optional|  
|/guidName|Nazwa do nadania symbol identyfikator GUID dla wszystkich obrazów w wygenerowanym manifeście.<br /><br /> Wartość domyślna: AssetsGuid|Optional|  
|/rootPath|Ścieżka katalogu głównego, który ma zostać usunięta, a przed utworzeniem zarządzanych identyfikatorów URI zasobów. (Ta flaga jest pomagające w przypadkach, w którym narzędzie pobiera ścieżkę względną identyfikatora URI problem, powodując zasobów, aby nie można załadować).<br /><br /> Wartość domyślna: \<Current Directory>|Optional|  
|/ Recursive|Ustawienie tej flagi nakazuje narzędziu rekursywnie Wyszukaj wszystkie katalogi w argumencie /resources. Pominięcie tej flagi powoduje top-poziomu tylko wyszukiwania katalogów.|Optional|  
|/isNative|Gdy argument zestawu jest ścieżką dla natywnego zestawu, należy ustawić tę flagę. Tej flagi należy pominąć, gdy argument zestawu jest nazwa zestawu zarządzanego. (Zobacz sekcję Uwagi Aby uzyskać dodatkowe informacje dotyczące tej flagi).|Optional|  
|/newGuids|Ustawienie tej flagi informuje narzędzie w celu utworzenia nowej wartości dla symbolu identyfikatora GUID obrazów zamiast scalania z istniejącego manifestu.|Optional|  
|/newIds|Ustawienie tej flagi informuje narzędzie, aby utworzyć nowy identyfikator wartości symboli dla każdego obrazu zamiast scalanie wartości z istniejącego manifestu.|Optional|  
|/noLogo|Ustawienie tej flagi powoduje zatrzymanie produktu i praw autorskich informacje dotyczące drukowania.|Optional|  
|/?|Wydrukuj informacje pomocy.|Optional|  
|/help|Wydrukuj informacje pomocy.|Optional|  
  
 **Przykłady**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml                       /assembly:My.Assembly.Name                       /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Uwagi  
  
-   Narzędzie obsługuje tylko pliki PNG i .xaml. Inne typy obrazu lub pliku zostaną zignorowane. Dla wszystkich typów nieobsługiwany podczas analizy zasobów, generowane jest ostrzeżenie. Jeśli nie, obsługiwane obrazów znajdują się po zakończeniu działania narzędzia analizy zasobów, zostanie wygenerowany błąd  
  
-   Postępując zgodnie z sugerowanego formatu dla obrazów PNG, narzędzie ustawi wartość rozmiaru/wymiaru .png format określony rozmiar, nawet jeśli jest inny niż rzeczywisty rozmiar obrazu.  
  
-   Format szerokość i wysokość, można pominąć w przypadku obrazów PNG, ale narzędzie odczytuje rzeczywiste szerokość/wysokość obrazu i je wykorzystać do wartości rozmiaru/wymiaru obrazu.  
  
-   Uruchamianie tego narzędzia na tym samym paska obrazów wiele razy dla tego samego .imagemanifest spowoduje zduplikowane wpisy manifestu, ponieważ narzędzie spróbuje podzielić paska obrazów obrazy autonomiczne i dodać tych, które mają istniejący manifest.  
  
-   Scalanie (z pominięciem /newGuids lub /newIds) należy to robić tylko dla wygenerowanych przez narzędzie manifestów. Nie manifestów, które zostały dostosowane lub wygenerowane za pomocą innych środków może poprawnie scalić.  
  
-   Manifestów, które są generowane dla zestawów natywnych może być konieczne należy ręcznie modyfikować po generowaniu sprawia, że symbole identyfikator zgodne identyfikatory z pliku .rc natywny zestaw zasobów.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 **Manifestu obrazu prostego**  
  
 Manifestu obrazu będzie podobny do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Manifestu obrazu dla paska obrazów**  
  
 Manifestu obrazu dla paska obrazów będą podobne do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Manifestu obrazu dla zasobów obrazu natywnego zestawu**  
  
 Manifestu obrazu dla obrazów macierzystych będą podobne do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```