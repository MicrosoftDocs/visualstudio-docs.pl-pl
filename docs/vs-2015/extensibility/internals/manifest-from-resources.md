---
title: Manifest from Resources | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4827402b63eadf517f031b04b7c7cf2fe8a4f56b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537101"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Narzędzie Manifest from Resources to Aplikacja konsolowa, która pobiera listę zasobów obrazów (plików PNG lub XAML) i generuje plik. imagemanifest, który umożliwia korzystanie z tych obrazów w usłudze obrazów programu Visual Studio. Ponadto to narzędzie może służyć do dodawania obrazów do istniejącej imagemanifest. To narzędzie jest przydatne do dodawania obsługi dużych rozdzielczości DPI i dla obrazów do rozszerzenia programu Visual Studio. Wygenerowany plik imagemanifest powinien być dołączony do programu i wdrożony jako część rozszerzenia programu Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 **Składnia**  
  
 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /Assembly: \<AssemblyName>\<Optional Args>  
  
 **Argumenty**  
  
|**Nazwa przełącznika**|**Uwagi**|**Wymagane lub opcjonalne**|  
|-|-|-|  
|/resources|Rozdzielana średnikami lista obrazów lub katalogów. Ta lista powinna zawsze zawierać pełną listę obrazów, które będą znajdować się w manifeście. Jeśli podano tylko częściową listę, wpisy, które nie zostały uwzględnione, zostaną utracone.<br /><br /> Jeśli dany plik zasobów jest paskiem obrazu, narzędzie podzieli je na osobne obrazy przed dodaniem każdego podobrazu do manifestu.<br /><br /> Jeśli obraz jest plikiem PNG, zalecamy formatowanie nazwy podobnej do tego, aby narzędzie mogło wypełnić odpowiednie atrybuty obrazu: \<Name> .. \<Width> \<Height> . Format.|Wymagane|  
|/Assembly|Nazwa zarządzanego zestawu (bez rozszerzenia) lub ścieżka środowiska uruchomieniowego zestawu natywnego, który hostuje zasoby (względem lokalizacji środowiska uruchomieniowego manifestu).|Wymagane|  
|/manifest|Nazwa, która ma zostać nadana wygenerowanemu plikowi. imagemanifest. Może również zawierać ścieżkę bezwzględną lub względną, aby utworzyć plik w innej lokalizacji. Nazwa domyślna jest zgodna z nazwą zestawu.<br /><br /> Wartość domyślna: \<Current Directory> \\<Assembly \> . imagemanifest|Opcjonalne|  
|/guidName|Nazwa, która ma zostać nadana symbolowi GUID dla wszystkich obrazów w wygenerowanym manifeście.<br /><br /> Wartość domyślna: AssetsGuid|Opcjonalne|  
|/rootPath|Ścieżka katalogu głównego, która musi zostać usunięta przed utworzeniem zarządzanych identyfikatorów URI zasobów. (Ta flaga ma pomóc w przypadkach, w których narzędzie pobiera względną ścieżkę identyfikatora URI, powodując niepowodzenie ładowania zasobów).<br /><br /> Wartooć\<Current Directory>|Opcjonalne|  
|/recursive|Ustawienie tej flagi nakazuje narzędziu cykliczne przeszukiwanie wszelkich katalogów w argumencie/Resources. Pominięcie tej flagi spowoduje przeszukanie katalogów tylko na najwyższym poziomie.|Opcjonalne|  
|/isNative|Ustaw tę flagę, gdy argument zestawu jest ścieżką dla natywnego zestawu. Pomiń tę flagę, gdy argument zestawu jest nazwą zarządzanego zestawu. (Zobacz sekcję Uwagi, aby uzyskać dodatkowe informacje na temat tej flagi).|Opcjonalne|  
|/newGuids|Ustawienie tej flagi nakazuje narzędziu utworzenie nowej wartości symbolu GUID obrazów zamiast scalanie jednego z istniejących manifestów.|Opcjonalne|  
|/newIds|Ustawienie tej flagi nakazuje narzędziu tworzenie nowych wartości symboli identyfikatora dla każdego obrazu zamiast scalać wartości z istniejącego manifestu.|Opcjonalne|  
|/noLogo|Ustawienie tej flagi uniemożliwia drukowanie informacji o produkcie i prawach autorskich.|Opcjonalne|  
|/?|Drukuj informacje pomocy.|Opcjonalne|  
|/help|Drukuj informacje pomocy.|Opcjonalne|  
  
 **Przykłady**  
  
- ManifestFromResources/Resources: D:\Images/Assembly: My. Assembly. Name/isNative  
  
- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/manifest: MyImageManifest. imagemanifest  
  
- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/guidName: Moje obrazy/newGuids/newIds  
  
## <a name="notes"></a>Uwagi  
  
- Narzędzie obsługuje tylko pliki PNG i XAML. Wszystkie inne typy obrazów lub plików zostaną zignorowane. Jest generowane ostrzeżenie dla wszystkich nieobsługiwanych typów podczas analizowania zasobów. Jeśli nie zostaną znalezione żadne obsługiwane obrazy, gdy narzędzie zakończy Analizowanie zasobów, zostanie wygenerowany błąd  
  
- Zgodnie z proponowanym formatem obrazów PNG narzędzie ustawi rozmiar/wartość wymiaru dla pliku PNG na rozmiar określony w formacie, nawet jeśli różni się od rzeczywistego rozmiaru obrazu.  
  
- Format szerokość/wysokość można pominąć dla obrazów PNG, ale narzędzie odczytaje rzeczywistą szerokość/wysokość obrazu i użyje ich dla rozmiaru/wartości obrazu.  
  
- Uruchomienie tego narzędzia na tym samym pasku obrazu wiele razy dla tego samego pliku. imagemanifest spowoduje powstanie zduplikowanych wpisów manifestu, ponieważ narzędzie próbuje podzielić obraz na obrazy autonomiczne i dodać je do istniejącego manifestu.  
  
- Scalanie (Pomijanie/newGuids lub/newIds) powinno być wykonywane tylko w przypadku manifestów generowanych przez narzędzie. Manifesty dostosowane lub wygenerowane za pośrednictwem innych metod mogą nie zostać poprawnie scalone.  
  
- Manifesty, które są generowane dla zestawów natywnych, mogą wymagać ręcznego edytowania po wygenerowaniu, aby symbole identyfikatorów były zgodne z identyfikatorami zasobów z pliku. RC zestawu natywnego.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 **Prosty manifest obrazu**  
  
 Manifest obrazu będzie podobny do tego pliku XML:  
  
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
  
 **Manifest obrazu dla paska obrazu**  
  
 Manifest obrazu dla paska obrazu będzie podobny do tego pliku XML:  
  
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
  
 **Manifest obrazu dla zasobów obrazu zestawu natywnego**  
  
 Manifest obrazu dla obrazów natywnych będzie podobny do tego pliku XML:  
  
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
