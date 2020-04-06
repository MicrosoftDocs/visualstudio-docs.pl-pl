---
title: Manifest z zasobów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707276"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Narzędzie Manifest z zasobów to aplikacja konsoli, która pobiera listę zasobów obrazu (.png lub .xaml plików) i generuje plik .imagemanifest, który umożliwia te obrazy do użycia z visual studio image service. Ponadto to narzędzie może służyć do dodawania obrazów do istniejącego .imagemanifest. To narzędzie jest przydatne do dodawania wysokiej rozdzielczości DPI i obsługi motywów dla obrazów do rozszerzenia programu Visual Studio. Wygenerowany plik .imagemanifest powinien zostać uwzględniony i wdrożony jako część rozszerzenia programu Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Składni**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /assembly:\<AssemblyName> \<Opcjonalne args>

 **Argumenty**

||||
|-|-|-|
|**Zmień nazwę**|**Uwagi**|**Wymagane lub opcjonalne**|
|/zasoby|Lista obrazów lub katalogów rozdzielanych średnikami. Ta lista powinna zawsze zawierać pełną listę obrazów, które będą w manifeście. Jeśli zostanie podana tylko lista częściowa, wpisy, które nie zostaną uwzględnione, zostaną utracone.<br /><br /> Jeśli dany plik zasobu jest paskiem obrazu, narzędzie podzieli go na oddzielne obrazy przed dodaniem każdego podobrazu do manifestu.<br /><br /> Jeśli obraz jest plikiem png, zalecamy sformatowanie takiej nazwy, aby narzędzie można \<było wypełnić odpowiednie atrybuty obrazu: Nazwa>. \<Szerokość>. \<Wysokość>.png.|Wymagany|
|/montaż|Nazwa zestawu zarządzanego (z wyłączeniem rozszerzenia) lub ścieżka środowiska uruchomieniowego natywnego zestawu, który obsługuje zasoby (względem lokalizacji środowiska wykonawczego manifestu).|Wymagany|
|/manifest|Nazwa do nadawana wygenerowanemu plikowi .imagemanifest. Może to również obejmować ścieżkę bezwzględną lub względną, aby utworzyć plik w innej lokalizacji. Nazwa domyślna jest zgodna z nazwą zestawu.<br /><br /> Domyślnie: \<Bieżący>\\<zestawu\>.imagemanifest|Optional (Opcjonalność)|
|/guidName|Nazwa do nadadawania symbolu GUID dla wszystkich obrazów w wygenerowanym manifeście.<br /><br /> Domyślnie: AssetsGuid|Optional (Opcjonalność)|
|/rootPath|Ścieżka główna, która musi zostać usunięta przed utworzeniem identyfikatorów URI zasobów zarządzanych. (Ta flaga ma pomóc w przypadkach, gdy narzędzie pobiera względną ścieżkę identyfikatora URI w błąd, powodując, że zasoby nie mogą się załadować).<br /><br /> Domyślnie: \<bieżąca> katalogu|Optional (Opcjonalność)|
|/rekursywny|Ustawienie tej flagi informuje narzędzie do rekursywnie przeszukiwać wszystkie katalogi w /resources argument. Pominięcie tej flagi spowoduje wyszukiwanie katalogów tylko na najwyższym poziomie.|Optional (Opcjonalność)|
|/isNative (|Ustaw tę flagę, gdy argument zestawu jest ścieżką dla zestawu macierzystego. Pomiń tę flagę, gdy argument zestawu jest nazwą zestawu zarządzanego. (Dodatkowe informacje na temat tej flagi można znaleźć w sekcji Uwagi).|Optional (Opcjonalność)|
|/nowyKięgi|Ustawienie tej flagi informuje narzędzie, aby utworzyć nową wartość dla symbolu GUID obrazów zamiast scalania z istniejącego manifestu.|Optional (Opcjonalność)|
|/newIds|Ustawienie tej flagi informuje narzędzie o utworzeniu nowych wartości symboli identyfikatora dla każdego obrazu zamiast scalania wartości z istniejącego manifestu.|Optional (Opcjonalność)|
|/noLogo|Ustawienie tej flagi uniemożliwia drukowanie informacji o produktach i prawach autorskich.|Optional (Opcjonalność)|
|/?|Wydrukuj informacje o Pomocy.|Optional (Opcjonalność)|
|/help|Wydrukuj informacje o Pomocy.|Optional (Opcjonalność)|

 **Przykłady**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Uwagi

- Narzędzie obsługuje tylko pliki png i xaml. Wszelkie inne typy obrazów lub plików zostaną zignorowane. Ostrzeżenie jest generowane dla wszystkich nieobsługiwał typy napotkane podczas analizowania zasobów. Jeśli po zakończeniu analizowania zasobów nie zostaną znalezione żadne obsługiwane obrazy, zostanie wygenerowany błąd

- Postępujące zgodnie z sugerowanym formatem obrazów png narzędzie ustawi wartość rozmiaru/wymiaru dla .png na rozmiar określony w formacie, nawet jeśli różni się on od rzeczywistego rozmiaru obrazu.

- Format szerokości/wysokości można pominąć dla obrazów png, ale narzędzie odczyta rzeczywistą szerokość/wysokość obrazu i użyje ich dla wartości rozmiaru/wymiaru obrazu.

- Wielokrotne uruchamianie tego narzędzia na tym samym pasku obrazu dla tego samego .imagemanifest spowoduje zduplikowane wpisy manifestu, ponieważ narzędzie próbuje podzielić pasek obrazu na obrazy autonomiczne i dodać je do istniejącego manifestu.

- Scalanie (pomijanie /newGuids lub /newIds) powinno odbywać się tylko dla manifestów generowanych przez narzędzie. Manifesty, które zostały dostosowane lub wygenerowane za pomocą innych środków, mogą nie zostać poprawnie scalone.

- Manifesty generowane dla zestawów natywnych mogą wymagać ręcznej edycji po wygenerowaniu, aby symbole identyfikatorów były zgodne z identyfikatorami zasobów z pliku rc zestawu macierzystego.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 **Prosty manifest obrazu**

 Manifest obrazu będzie podobny do tego pliku xml:

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

 Manifest obrazu dla paska obrazu będzie podobny do tego pliku xml:

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

 **Manifest obrazu dla zasobów obrazu natywnego zestawu**

 Manifest obrazu dla obrazów natywnych będzie podobny do tego pliku xml:

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
