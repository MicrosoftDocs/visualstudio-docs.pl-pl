---
title: Manifest from Resources | Microsoft Docs
description: Dowiedz się, jak używać narzędzia Manifest from Resources do dodawania plików .png lub XAML do pliku imagemanifest do użycia z usługą Visual Studio Image Service.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f69a46362b3076025a63625adb1ee4a478622259
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903181"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Narzędzie Manifest from Resources to aplikacja konsolowa, która pobiera listę zasobów obrazu (pliki .png lub xaml) i generuje plik .imagemanifest, który umożliwia korzystanie z tych obrazów w usłudze Visual Studio Image Service. Ponadto to narzędzie może służyć do dodawania obrazów do istniejącego pliku imagemanifest. To narzędzie jest przydatne do dodawania obsługi wysokiej rozdzielczości DPI i obsługi Visual Studio obrazów. Wygenerowany plik .imagemanifest powinien zostać uwzględniony i wdrożony w ramach rozszerzenia Visual Studio (vsix).

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Składnia**

 ManifestFromResources /resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Argumenty**

|**Nazwa przełącznika**|**Uwagi**|**Wymagane lub opcjonalne**|
|-|-|-|
|/resources|Rozdzielana średnikami lista obrazów lub katalogów. Ta lista powinna zawsze zawierać pełną listę obrazów, które będą się znajdowały w manifeście. Jeśli zostanie podana tylko część listy, wpisy, które nie zostaną uwzględnione, zostaną utracone.<br /><br /> Jeśli dany plik zasobu jest paskiem obrazu, narzędzie podzieli go na oddzielne obrazy przed dodaniem każdego obrazu podrzędnego do manifestu.<br /><br /> Jeśli obraz jest plikiem .png, zalecamy sformatowanie nazwy w ten sposób, aby narzędzie wypełniało odpowiednie atrybuty obrazu: \<Name> . \<Width> . \<Height>.png.|Wymagane|
|/assembly|Nazwa zarządzanego zestawu (bez rozszerzenia) lub ścieżka środowiska uruchomieniowego zestawu natywnego, który hostuje zasoby (względem lokalizacji środowiska uruchomieniowego manifestu).|Wymagane|
|/manifest|Nazwa, która ma być nadana wygenerowanemu plikowi .imagemanifest. Może to również zawierać ścieżkę bezwzględną lub względną, aby utworzyć plik w innej lokalizacji. Nazwa domyślna odpowiada nazwie zestawu.<br /><br /> Ustawienie domyślne: \<Current Directory> \\<assembly \> .imagemanifest|Opcjonalne|
|/guidName|Nazwa, która ma być nadaj symbolowi identyfikatora GUID dla wszystkich obrazów w wygenerowanym manifeście.<br /><br /> Ustawienie domyślne: AssetsGuid|Opcjonalne|
|/rootPath|Ścieżka główna, którą należy wyłączyć przed utworzeniem zarządzanych URI zasobów. (Ta flaga ma na celu pomoc w przypadkach, w których narzędzie pobiera nieprawidłową ścieżkę względnego URI, powodując niepowodzenie ładowania zasobów).<br /><br /> Domyślny: \<Current Directory>|Opcjonalne|
|/rekursywny|Ustawienie tej flagi nakazuje narzędziu cykliczne przeszukiwanie wszystkich katalogów w argumentze /resources. Pominięcie tej flagi spowoduje wyszukiwanie katalogów tylko na najwyższym poziomie.|Opcjonalne|
|/isNative|Ustaw tę flagę, gdy argument zestawu jest ścieżką dla zestawu natywnego. Pomiń tę flagę, gdy argument zestawu jest nazwą zarządzanego zestawu. (Aby uzyskać dodatkowe informacje na temat tej flagi, zobacz sekcję Uwagi).|Opcjonalne|
|/newGuids|Ustawienie tej flagi nakazuje narzędziu utworzenie nowej wartości dla symbolu identyfikatora GUID obrazów zamiast scalania tej wartości z istniejącego manifestu.|Opcjonalne|
|/newIds|Ustawienie tej flagi nakazuje narzędziu utworzenie nowych wartości symboli identyfikatora dla każdego obrazu zamiast scalania wartości z istniejącego manifestu.|Opcjonalne|
|/noLogo|Ustawienie tej flagi zatrzymuje drukowanie informacji o produkcie i prawach autorskich.|Opcjonalne|
|/?|Wydrukuj informacje o Pomocy.|Opcjonalne|
|/help|Wydrukuj informacje o Pomocy.|Opcjonalne|

 **Przykłady**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Uwagi

- Narzędzie obsługuje tylko pliki .png i xaml. Wszystkie inne typy plików lub obrazów zostaną zignorowane. Ostrzeżenie jest generowane dla wszystkich nieobsługiwanych typów napotkanych podczas analizowania zasobów. Jeśli po zakończeniu analizowania zasobów przez narzędzie nie zostaną znalezione żadne obsługiwane obrazy, zostanie wygenerowany błąd

- Zgodnie z sugerowanym formatem obrazów .png narzędzie ustawi wartość rozmiaru/wymiaru dla obrazu .png na rozmiar określony w formacie, nawet jeśli różni się od rzeczywistego rozmiaru obrazu.

- Format szerokości/wysokości można pominąć w przypadku obrazów .png, ale narzędzie odczyta rzeczywistą szerokość/wysokość obrazu i użyje ich dla wartości rozmiaru/wymiaru obrazu.

- Wielokrotne uruchomienie tego narzędzia na tym samym pasku obrazu dla tego samego pliku imagemanifest spowoduje zduplikowanie wpisów manifestu, ponieważ narzędzie próbuje podzielić pasek obrazu na obrazy autonomiczne i dodać je do istniejącego manifestu.

- Scalanie (pomijanie /newGuids lub /newIds) powinno odbywać się tylko dla manifestów generowanych przez narzędzie. Manifesty, które zostały dostosowane lub wygenerowane za pomocą innych środków, mogą nie zostać poprawnie scalone.

- Manifesty generowane dla zestawów natywnych mogą wymagać ręcznej edycji po generacji, aby symbole identyfikatorów dopasować identyfikatory zasobów z pliku RC zestawu macierzystego.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 **Prosty manifest obrazu**

 Manifest obrazu będzie podobny do tego .xml pliku:

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

 Manifest obrazu dla paska obrazu będzie podobny do tego .xml pliku:

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

 **Manifest obrazu dla zasobów natywnego obrazu zestawu**

 Manifest obrazu dla obrazów natywnych będzie podobny do tego .xml pliku:

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
