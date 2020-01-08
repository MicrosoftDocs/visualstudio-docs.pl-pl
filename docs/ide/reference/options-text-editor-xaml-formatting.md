---
title: Opcje, edytor tekstu, XAML, formatowanie
ms.date: 10/29/2018
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d340a3b9468ea23c4cab23aabe19a7c1390955a3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568246"
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie

Na stronie właściwości **formatowania** można określić sposób formatowania elementów i atrybutów w dokumentach XAML. Aby otworzyć okno dialogowe **Opcje** , kliknij menu **Narzędzia** , a następnie kliknij przycisk **Opcje**. Aby uzyskać dostęp do strony właściwości **formatowania** , rozwiń węzeł **Edytor tekstu** > **XAML** > **Formatowanie** .

## <a name="auto-formatting-events"></a>Zdarzenia Autoformatowania

Autoformatowanie może wystąpić, gdy zostanie wykryte dowolne z poniższych zdarzeń.

- Ukończenie tagu końcowego lub tagu prostego.

- Wykonanie tagu początkowego.

- Wklejanie ze schowka.

- Formatowanie poleceń klawiatury.

Można określić, które zdarzenia powodują Autoformatowanie.

**Po zakończeniu tagu końcowego lub tagu prostego**

Autoformatowanie występuje po zakończeniu wpisywania tagu końcowego lub tagu prostego. Tag prosty nie ma żadnych atrybutów, na przykład `<Button />`.

**Po zakończeniu tagu początkowego**

Autoformatowanie jest wykonywane po zakończeniu wpisywania tagu początkowego.

**Przy wklejaniu ze schowka**

Autoformatowanie występuje po wklejeniu kodu XAML ze schowka do widoku XAML.

## <a name="quotation-mark-style"></a>Styl cudzysłowu

To ustawienie wskazuje, czy wartości atrybutów są ujęte w znaki pojedynczego lub podwójnego cudzysłowu. Funkcja autoformatującego i Autouzupełnianie IntelliSense używają tego ustawienia.

Po ustawieniu tej opcji będzie to miało zastosowanie tylko atrybuty dodane w projektancie lub ręcznie w widoku XAML.

**Podwójne cudzysłowy (")**

Wartości atrybutów są ujęte w cudzysłów.
`<Button Name="button1">Hello</Button>`

**Apostrofy (')**

Wartości atrybutów są ujęte w apostrofy.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Zawijanie tagów

Możesz określić długość linii dla zawijania tagów. Gdy funkcja zawijania tagów jest włączona, wszystkie XAML dodane później za pomocą projektanta zostaną odpowiednio opakowane.

**Zawijaj tagi, które przekraczają określoną długość**

Określa, czy linie są opakowane w długości linii określonej przez **Długość**.

**Długość**

Liczba znaków, jaką może zawierać linia. W razie potrzeby niektóre linie XAML mogą przekroczyć określoną długość wiersza.

## <a name="attribute-spacing"></a>Odstępy między atrybutami

Użyj tego ustawienia, aby kontrolować sposób, w jaki atrybuty są rozmieszczone w dokumencie XAML

**Zachowaj znaki nowego wiersza i odstępy między atrybutami**

Autoformatowanie nie ma wpływ na nowe wiersze i odstępy między atrybutami.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Wstaw pojedyncze odstępy między atrybutami**

Atrybuty zajmują jedną linię, z jedną spacją oddzielającą sąsiednie atrybuty. Ustawienia zawijania tagów są stosowane.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umieść każdy atrybut w osobnym wierszu**

Każdy atrybut zajmuje własny wiersz, który jest przydatny, gdy istnieje wiele atrybutów.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Umieść pierwszy atrybut w tym samym wierszu co tag początkowy**

Po zaznaczeniu ten pierwszy atrybut jest wyświetlany w tym samym wierszu co tag początkowy elementu.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Odstępy elementów

To ustawienie służy do sterowania sposobem rozmieszczania elementów w dokumencie XAML.

**Zachowaj nowe wiersze w zawartości**

Puste wiersze w zawartości elementu nie są usuwane.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Zwiń wiele pustych wierszy w zawartości do pojedynczego wiersza**

Puste wiersze w zawartości elementu są zwijane do jednego wiersza.

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
