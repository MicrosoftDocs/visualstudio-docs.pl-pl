---
title: Porównywanie właściwości i towarów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634412"
---
# <a name="compare-properties-and-items"></a>Porównaj właściwości i elementy

Właściwości i elementy MSBuild są używane do przekazywania informacji do zadań, oceny warunków i przechowywania wartości, do których można się odwoływać w całym pliku projektu.

- Właściwości są parami nazwa-wartość. Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

- Elementy są obiektami, które zazwyczaj reprezentują pliki. Obiekty elementu mogą mieć skojarzone kolekcje metadanych. Metadane są parami nazwa-wartość. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Skalary i wektory

Ponieważ właściwości MSBuild są parami nazwa-wartość, które mają tylko jedną wartość ciągu, są często opisywane jako *skalarne.* Ponieważ typy elementów MSBuild są listami elementów, są one często określane jako *wektor*. Jednak w praktyce właściwości mogą reprezentować wiele wartości, a typy elementów mogą mieć zero lub jeden element.

### <a name="target-dependency-injection"></a>Wstrzyknięcie zależności docelowej

Aby zobaczyć, jak właściwości mogą reprezentować wiele wartości, należy wziąć pod uwagę typowy wzorzec użycia do dodawania obiektu docelowego do listy obiektów docelowych, które mają zostać utworzone. Ta lista jest zazwyczaj reprezentowana przez wartość właściwości, z nazwami docelowymi oddzielonymi średnikami.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Właściwość `BuildDependsOn` jest zwykle używana jako argument `DependsOnTargets` atrybutu docelowego, skutecznie konwertując go na listę elementów. Ta właściwość może zostać zastąpiona, aby dodać obiekt docelowy lub zmienić docelową kolejność wykonywania. Na przykład:

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

dodaje cel CustomBuild do listy `BuildDependsOn` docelowej, podając wartość `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.

Począwszy od MSBuild 4.0, iniekcja zależności docelowej jest przestarzała. Zamiast `AfterTargets` tego `BeforeTargets` użyj atrybutów i. Aby uzyskać więcej informacji, zobacz [Docelowa kolejność kompilacji](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Konwersje między ciągami a listami elementów

MSBuild wykonuje konwersje do i z typów elementów i wartości ciągów w razie potrzeby. Aby zobaczyć, jak lista elementów może stać się wartością ciągu, należy wziąć pod uwagę, co się dzieje, gdy typ elementu jest używany jako wartość właściwości MSBuild:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Typ elementu OutputDir `Include` ma atrybut o wartości "KeyFiles\\; Certyfikaty\\". MSBuild analizuje ten ciąg na dwa elementy: KeyFiles\ i Certificates\\. Gdy typ elementu OutputDir jest używany jako wartość właściwości OutputDirList, MSBuild konwertuje lub "spłaszcza" typ elementu na\\ciąg oddzielany średnikiem "KeyFiles; Certyfikaty\\".

## <a name="properties-and-items-in-tasks"></a>Właściwości i elementy w zadaniach

Właściwości i elementy są używane jako dane wejściowe i wyjściowe do zadań MSBuild. Aby uzyskać więcej informacji, zobacz [Zadania](../msbuild/msbuild-tasks.md).

Właściwości są przekazywane do zadań jako atrybuty. W ramach zadania właściwość MSBuild jest reprezentowana przez typ właściwości, którego wartość można przekonwertować na i z ciągu. Obsługiwane typy właściwości `bool` `char`obejmują `DateTime` `Decimal`, `Double` `int`, `string`, , <xref:System.Convert.ChangeType%2A> , i dowolny typ, który może obsłużyć.

Elementy są przekazywane <xref:Microsoft.Build.Framework.ITaskItem> do zadań jako obiekty. W ramach <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> zadania reprezentuje wartość elementu <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> i pobiera jego metadane.

Lista elementów typu elementu może być przekazywana jako tablica `ITaskItem` obiektów. Począwszy od programu .NET Framework 3.5, elementy można usunąć z `Remove` listy elementów w miejscu docelowym przy użyciu atrybutu. Ponieważ elementy można usunąć z listy elementów, jest możliwe dla typu elementu, aby mieć zero elementów. Jeśli lista elementów jest przekazywana do zadania, kod w zadaniu powinien sprawdzić tę możliwość.

## <a name="property-and-item-evaluation-order"></a>Kolejność oceny właściwości i towaru

Podczas fazy oceny kompilacji importowane pliki są włączane do kompilacji w kolejności, w jakiej się pojawiają. Właściwości i elementy są definiowane w trzech przejściach w następującej kolejności:

- Właściwości są definiowane i modyfikowane w kolejności, w jakiej się pojawiają.

- Definicje towarów są definiowane i modyfikowane w kolejności, w jakiej się pojawiają.

- Elementy są definiowane i modyfikowane w kolejności, w jakiej się pojawiają.

Podczas fazy wykonywania kompilacji właściwości i elementy, które są zdefiniowane w ramach obiektów docelowych są oceniane razem w jednej fazie w kolejności, w jakiej się pojawiają.

Nie jest to jednak pełna historia. Po zdefiniowaniu właściwości, definicji towaru lub towaru jego wartość jest obliczana. Oceniający wyrażenie rozwija ciąg, który określa wartość. Rozwinięcie ciągu zależy od fazy kompilacji. Oto bardziej szczegółowa kolejność oceny właściwości i towaru:

- Podczas fazy oceny kompilacji:

  - Właściwości są definiowane i modyfikowane w kolejności, w jakiej się pojawiają. Funkcje właściwości są wykonywane. Wartości właściwości w postaci $(PropertyName) są rozwijane w wyrażeniach. Wartość właściwości jest ustawiona na wyrażenie rozwinięte.

  - Definicje towarów są definiowane i modyfikowane w kolejności, w jakiej się pojawiają. Funkcje właściwości zostały już rozwinięte w wyrażeniach. Wartości metadanych są ustawione na wyrażenia rozwinięte.

  - Typy elementów są definiowane i modyfikowane w kolejności, w jakiej się pojawiają. Wartości elementów w formularzu @(ItemType) są rozwijane. Przekształcenia elementów są również rozwinięte. Funkcje i wartości właściwości zostały już rozwinięte w wyrażeniach. Lista elementów i wartości metadanych są ustawiane na rozszerzone wyrażenia.

- Podczas fazy wykonywania kompilacji:

  - Właściwości i elementy, które są zdefiniowane w obrębie obiektów docelowych są oceniane razem w kolejności, w jakiej się pojawiają. Funkcje właściwości są wykonywane i wartości właściwości są rozwijane w wyrażeniach. Wartości elementów i przekształcenia elementów są również rozwijane. Wartości właściwości, wartości typu elementu i wartości metadanych są ustawiane na wyrażenia rozwinięte.

### <a name="subtle-effects-of-the-evaluation-order"></a>Subtelne efekty zlecenia oceny

W fazie oceny kompilacji oceny właściwości poprzedza oceny elementu. Niemniej jednak właściwości mogą mieć wartości, które wydają się zależeć od wartości elementu. Należy wziąć pod uwagę następujący skrypt.

```xml
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

Wykonanie zadania Wiadomość wyświetla ten komunikat:

```
KeyFileVersion: 1.0.0.3
```

Dzieje się tak, `KeyFileVersion` ponieważ wartość\@jest faktycznie ciąg " (KeyFile->'%(Version)')". Przekształcenia towarów i towarów nie zostały rozwinięte, `KeyFileVersion` gdy właściwość została zdefiniowana po raz pierwszy, więc właściwość została przypisana wartość ciągu nierozwińczonego.

Podczas fazy wykonywania kompilacji, podczas przetwarzania message zadanie, MSBuild\@rozszerza ciąg " (KeyFile->'%(Version)')" do wydajności "1.0.0.3".

Należy zauważyć, że ten sam komunikat pojawi się, nawet jeśli właściwości i grup towarów zostały wycofane w kolejności.

W drugim przykładzie należy wziąć pod uwagę, co może się zdarzyć, gdy grupy właściwości i towarów znajdują się w obrębie obiektów docelowych:

```xml
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

Zadanie Wiadomość wyświetla ten komunikat:

```
KeyFileVersion:
```

Dzieje się tak, ponieważ w fazie wykonywania kompilacji, grupy właściwości i elementów zdefiniowane w obiektach docelowych są oceniane od góry do dołu w tym samym czasie. Gdy `KeyFileVersion` jest `KeyFile` zdefiniowany, jest nieznany. W związku z tym transformacja elementu rozwija się do pustego ciągu.

W takim przypadku odwrócenie kolejności właściwości i grup elementów przywraca oryginalną wiadomość:

```xml
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

Wartość `KeyFileVersion` jest ustawiona na "1.0.0.3",\@a nie na " (KeyFile->'%(Version)')". Zadanie Wiadomość wyświetla ten komunikat:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
