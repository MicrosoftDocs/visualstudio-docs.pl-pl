---
title: Opcje, edytor tekstu, XAML, formatowanie
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 77424baa8b359846026dfa57c1bcd57b2e4cbcda
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039374"
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie

Użyj **formatowanie** stronę właściwości, aby określić, jak sformatowane elementów i atrybutów w dokumencie XAML. Aby otworzyć **opcje** okno dialogowe, kliknij przycisk **narzędzia** menu, a następnie kliknij przycisk **opcje**. Aby uzyskać dostęp do **formatowanie** właściwości rozwiń **edytora tekstów** > **XAML** > **formatowanie** węzeł.

## <a name="auto-formatting-events"></a>Automatyczne formatowanie zdarzeń

Automatyczne formatowanie może wystąpić, gdy dowolne z następujących zdarzeń wykryte.

-   Uzupełnianie tagu końcowego lub prostego.

-   Uzupełnianie tagu początkowego.

-   Wklejanie ze Schowka.

-   Formatowanie klawiaturowych.

Można określić, zdarzenia, które powodują automatyczne formatowanie.

**Po zakończeniu tagu końcowego lub prostego**

Automatyczne formatowanie występuje po zakończeniu wpisywania tagu końcowego lub prostego tagu. Prostych tagów nie ma atrybutów, na przykład `<Button />`.

**Po zakończeniu tagu początkowego**

Automatyczne formatowanie występuje po zakończeniu wpisywania tagu początkowego.

**Przy wklejaniu ze Schowka**

Automatyczne formatowanie występuje podczas wklejania XAML ze Schowka w widoku XAML.

## <a name="quotation-mark-style"></a>Styl cudzysłowu

To ustawienie wskazuje, czy wartości atrybutów są ujęte w pojedyncze lub podwójne znaki cudzysłowu. Użyj tego ustawienia, Autoformatowanie zostało i automatycznego uzupełniania IntelliSense.

Po ustawieniu tej opcji tylko atrybuty później dodane przy użyciu narzędzia Projektant lub ręcznie w widoku XAML dotyczy problem.

**Podwójny cudzysłów (")**

Wartości atrybutów są ujęte w cudzysłów.
`<Button Name="button1">Hello</Button>`

**Pojedynczy cudzysłów (')**

Wartości atrybutów są ujęte w apostrofy.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Zawijanie tagów

Można określić długość wiersza zawijanie tagów. Po włączeniu zawijanie tagów XAML, wszystkie dodane przy użyciu narzędzia Projektant zostanie zawinięta odpowiednio.

**Zawijaj tagi przekraczające określoną długość**

Określa, czy wiersze są opakowane w określonej przez długość wiersza **długość**.

**Długość**

Liczba znaków, które mogą zawierać wiersz. Jeśli to konieczne, niektóre linie XAML może przekraczać długości określonej linii.

## <a name="attribute-spacing"></a>Odstępy między atrybutami

To ustawienie służy do kontrolowania, jak atrybuty są rozmieszczone w dokumencie XAML

**Zachowaj tabulacji i spacje między atrybutami**

Automatyczne formatowanie nie dotyczy nowych wierszy i spacji między atrybutami.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Wstaw odstęp między atrybutami**

Atrybuty zajmują jeden wiersz z jednego miejsca oddzielenie sąsiadujących atrybutów. Ustawienia zawijania tag są stosowane.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umieść każdy atrybut w osobnym wierszu**

Każdy atrybut zajmuje osobnym wierszu, co jest przydatne, jeśli podano wiele atrybutów.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Pozycja pierwszego atrybutu w tym samym wierszu co tag początkowy**

Po zaznaczeniu tej opcji, w tym samym wierszu co tag początkowy element pojawi się pierwszy atrybut.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Odstępy między elementami

Użyj tego ustawienia, aby kontrolować sposób rozmieszczenia elementów w dokumencie XAML.

**Zachowaj nowe wiersze w zawartości**

Puste wiersze w zawartości elementu nie są usuwane.

```xml
<Grid>


<Button Name="button1">Hello</Button>

</Grid>
```

**Zwiń wiele puste wiersze w zawartości w jeden wiersz**

Puste wiersze w zawartości elementu są zwinięte do pojedynczego wiersza.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Usuń puste wiersze w zawartości**

Wszystkie puste wiersze w zawartości elementu są usuwane.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Zobacz także

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)