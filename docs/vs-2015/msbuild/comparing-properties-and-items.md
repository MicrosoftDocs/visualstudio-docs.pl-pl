---
title: Porównanie właściwości i elementów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9418bd27d2f089b57cc2fb2abcf7b6610342f32d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758463"
---
# <a name="comparing-properties-and-items"></a>Porównanie właściwości i elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Właściwości programu MSBuild i elementy zarówno służą do przekazywania informacji do zadań, oceny warunków i przechowywania wartości, które można się odwoływać w całym pliku projektu.  
  
-   Właściwości to pary nazwa wartość. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](msbuild-properties1.md).  
  
-   Elementy są obiektami, które zazwyczaj reprezentują pliki. Obiekty elementu może być skojarzony kolekcji metadanych. Metadane są pary nazwa wartość. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Wartości skalarnych i wektory  
 Ponieważ właściwości programu MSBuild są pary nazwa wartość, które mają tylko jedną wartość ciągu, są często określane jako *skalarne*. Ponieważ typy elementów MSBuild to listy elementów, są często określane jako *wektor*. Jednak w praktyce właściwości może reprezentować wiele wartości i typów elementów może mieć zero lub jeden elementów.  
  
### <a name="target-dependency-injection"></a>Wstrzykiwanie zależności docelowej  
 Aby zobaczyć, jak właściwości może reprezentować wiele wartości, należy rozważyć użycie typowym dodawania miejsca docelowego do listy elementów docelowych, które ma zostać utworzony. Ta lista jest zwykle reprezentowany przez wartość właściwości przy użyciu nazwy docelowej, oddzielając je średnikami.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 `BuildDependsOn` Właściwość jest zwykle używana jako argument elementu docelowego `DependsOnTargets` atrybutu, efektywnie podczas konwertowania go do listy elementów. Tę właściwość można przesłonić, aby dodać element docelowy lub zmienić kolejność wykonywania obiektów docelowych. Na przykład  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Dodaje element docelowy CustomBuild listę docelową, dzięki czemu `BuildDependsOn` wartość `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Począwszy od programu MSBuild 4.0, wstrzykiwanie zależności docelowy jest przestarzały. Użyj `AfterTargets` i `BeforeTargets` zamiast atrybutów. Aby uzyskać więcej informacji, zobacz [kolejności kompilacji docelowej](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Konwertowanie pomiędzy ciągami a listy elementów  
 Program MSBuild wykonuje konwersje do i z typów elementów i wartości ciągu, zgodnie z potrzebami. Aby zobaczyć, jak listy elementów może stać się wartość ciągu, należy wziąć pod uwagę co się stanie, jeśli typ elementu jest używana jako wartość właściwości programu MSBuild:  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Typ elementu ma OutputDir `Include` atrybutu o wartości "odwołaniach\\; Certyfikaty\\". Program MSBuild analizuje ten ciąg na dwa elementy: KeyFiles\ i certyfikaty\\. Typ elementu OutputDir stosowania jako wartość właściwości OutputDirList MSBuild konwertuje lub "spłaszcza" typ elementu do ciągu rozdzielonych średnikami "odwołaniach\\; Certyfikaty\\".  
  
## <a name="properties-and-items-in-tasks"></a>Właściwości i elementy w zadaniach  
 Właściwości i elementy są używane jako dane wejściowe i wyjściowe zadań programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
 Właściwości są przekazywane do zadań jako atrybuty. W zadaniu właściwość narzędzia MSBuild jest reprezentowany przez typ właściwości, których wartość można przekonwertować do i z ciągu. Typy obsługiwanych właściwość obejmują `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, i dowolny typ, który <xref:System.Convert.ChangeType%2A> może obsłużyć.  
  
 Elementy są przekazywane do zadań, jak <xref:Microsoft.Build.Framework.ITaskItem> obiektów. W zadaniu <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> reprezentuje wartość elementu i <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> pobiera jego metadanych.  
  
 Listy elementów typu elementu mogą być przekazywane jako tablica `ITaskItem` obiektów. Począwszy od programu .NET Framework 3.5, elementy można usunąć z listy elementów w elemencie docelowym przy użyciu `Remove` atrybutu. Ponieważ elementów można usunąć z listy elementów, jest możliwe dla typu elementu zawierały elementów. Jeśli lista elementów jest przekazywany do zadania, kod w zadaniu powinna sprawdzać, czy taka możliwość.  
  
## <a name="property-and-item-evaluation-order"></a>Właściwości i kolejność obliczania elementu  
 W fazie oceny procesu kompilacji zaimportowane pliki są włączane do kompilacji w kolejności, w jakiej są wyświetlane. Właściwości i elementy są zdefiniowane w trzech przebiegów w następującej kolejności:  
  
- Właściwości są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane.  
  
- Definicje elementów są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane.  
  
- Elementy są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane.  
  
  W fazie wykonanie procesu kompilacji właściwości i elementy, które są zdefiniowane w ramach obiekty docelowe są oceniane razem w jednej fazie w kolejności, w jakiej są wyświetlane.  
  
  To nie jest jednak całą historię. Jeśli jest zdefiniowana właściwość, definicja elementu lub elementu, jego wartość jest szacowana. Ewaluator wyrażeń rozwija ciąg, który określa wartość. Rozszerzenie ciągu jest zależna od fazy kompilacji. Poniżej przedstawiono bardziej szczegółowe kolejność obliczania właściwości i elementów:  
  
- W fazie obliczania kompilacji:  
  
  -   Właściwości są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane. Funkcje właściwości są wykonywane. Wartości właściwości w $(PropertyName) formularza zostaną rozwinięte w wyrażeniach. Ustawiono wartość właściwości rozszerzonej wyrażenia.  
  
  -   Definicje elementów są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane. Funkcje właściwości już zostały rozszerzone w wyrażeniach. Metadane wartości są ustawiane na rozwinięty wyrażeń.  
  
  -   Typy elementów są zdefiniowane i modyfikować w kolejności, w jakiej są wyświetlane. Wartości elementów w @(ItemType) formularza zostaną rozwinięte. Przekształceń elementów również są rozwijane. W wyrażeniach w już zostały rozszerzone funkcje właściwości i wartości. Wartości elementów listy i metadanych są ustawiane na rozwinięty wyrażenia.  
  
- W fazie wykonanie procesu kompilacji:  
  
  -   Właściwości i elementy, które są zdefiniowane w ramach obiekty docelowe są oceniane razem w kolejności, w jakiej są wyświetlane. Funkcje właściwości są wykonywane, i wartości właściwości zostaną rozwinięte w wyrażeniach. Wartości elementów i przekształceń elementów również są rozwijane. Wartości właściwości elementu typu wartości i wartości metadanych są ustawione na rozwinięty wyrażeń.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Subtelnych efektów kolejność obliczania  
 W fazie oceny kompilacji oceny właściwości poprzedza obliczania wartości elementu. Niemniej jednak właściwości mogą mieć wartości, które wydają się zależy od wartości elementu. Rozważmy poniższy skrypt.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Wykonywanie zadania komunikat wyświetla ten komunikat:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Jest to spowodowane wartość `KeyFileVersion` jest faktycznie ciągiem "@(KeyFile ->"% (wersja)")". Element i przekształceń elementów nie zostały rozszerzona, gdy właściwość najpierw została zdefiniowana, więc `KeyFileVersion` właściwość została przypisana wartość nierozwiniętymi ciągu.  
  
 W fazie wykonywania kompilacji podczas przetwarzania zadania komunikat MSBuild rozszerza ciąg "@(KeyFile ->"% (wersja)")" umożliwiające uzyskanie "1.0.0.3".  
  
 Należy zauważyć, że ten sam komunikat zostanie wyświetlony, nawet wtedy, gdy właściwości i elementów grupy zostały cofnięte w kolejności.  
  
 Drugi przykład należy wziąć pod uwagę co może się zdarzyć w przypadku właściwości i elementów grupy znajduje się w obrębie elementów docelowych:  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Zadanie komunikatu wyświetla ten komunikat:  
  
```  
KeyFileVersion:   
```  
  
 Jest to spowodowane w fazie wykonanie procesu kompilacji, właściwości i elementów grupy zdefiniowane obiekty docelowe są oceniane od góry do dołu w tym samym czasie. Gdy `KeyFileVersion` jest zdefiniowany, `KeyFile` jest nieznany. W związku z tym przekształcenie elementu rozwija do pustego ciągu.  
  
 W tym przypadku odwracając kolejność grup właściwości i elementu spowoduje przywrócenie oryginalnej wiadomości:  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Wartość `KeyFileVersion` jest ustawiona na "1.0.0.3", a nie do "@(KeyFile ->"% (wersja)")". Zadanie komunikatu wyświetla ten komunikat:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
