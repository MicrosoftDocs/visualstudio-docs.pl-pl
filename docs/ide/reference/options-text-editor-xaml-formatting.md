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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568246"
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie

Strona właściwości **Formatowanie** służy do określania sposobu formatowania elementów i atrybutów w dokumentach XAML. Aby otworzyć okno dialogowe **Opcje,** kliknij menu **Narzędzia,** a następnie kliknij polecenie **Opcje**. Aby uzyskać dostęp do strony właściwości **Formatowanie,** rozwiń węzeł**Formatowanie**  > **XAML** >  **edytora tekstu.**

## <a name="auto-formatting-events"></a>Zdarzenia automatycznego formatowania

Autoformowanie może wystąpić po wykryciu któregokolwiek z następujących zdarzeń.

- Uzupełnianie tagu końcowego lub prostego tagu.

- Zakończenie tagu początkowego.

- Wklejanie ze schowka.

- Formatowanie poleceń klawiaturowych.

Można określić, które zdarzenia powodują automatyczne formatowanie.

**Po zakończeniu tagu końcowego lub prostego tagu**

Automatyczne formatowanie następuje po zakończeniu wpisywania znacznika końcowego lub prostego znacznika. Prosty tag nie ma atrybutów, na przykład `<Button />`.

**Po zakończeniu tagu startowego**

Automatyczne formatowanie odbywa się po zakończeniu wpisywania znacznika początkowego.

**Podczas wklejania ze schowka**

Automatyczne formatowanie występuje podczas wklejania xaml ze schowka do widoku XAML.

## <a name="quotation-mark-style"></a>Styl znaku oferty

To ustawienie wskazuje, czy wartości atrybutów są ujęte w pojedyncze czy podwójne cudzysłowy. Autoformater i autouzupełnianie IntelliSense używają tego ustawienia.

Po ustawieniu tej opcji dotyczy to tylko atrybutów dodanych później za pomocą projektanta lub ręcznie w widoku XAML.

**Cudzysłowy (")**

Wartości atrybutów są ujęte w cudzysłowy.
`<Button Name="button1">Hello</Button>`

**Pojedyncze cudzysłowy (')**

Wartości atrybutów są ujęte w pojedyncze cudzysłowy.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Zawijanie znaczników

Można określić długość linii dla zawijania znaczników. Gdy zawijania tagów jest włączona, wszystkie XAML następnie dodane przy użyciu projektanta zostaną zapakowane odpowiednio.

**Zawijania znaczników przekraczających określoną długość**

Określa, czy linie są zawijane na długości linii określonej przez **Długość**.

**Długość**

Liczba znaków, które może zawierać wiersz. W razie potrzeby niektóre wiersze XAML mogą przekraczać określoną długość linii.

## <a name="attribute-spacing"></a>Odstępy między atrybutami

To ustawienie służy do kontrolowania sposobu rozmieszczenia atrybutów w dokumencie XAML

**Zachowywanie nowych linii i spacji między atrybutami**

Automatyczne formatowanie nie ma wpływu na nowe linie i spacje między atrybutami.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Wstawianie pojedynczej spacji między atrybutami**

Atrybuty zajmują jeden wiersz, z jedną spacją oddzielającą sąsiednie atrybuty. Stosowane są ustawienia zawijania znaczników.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umieszczanie każdego atrybutu w osobnym wierszu**

Każdy atrybut zajmuje własną linię, co jest przydatne, gdy istnieje wiele atrybutów.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Pozycjonuj pierwszy atrybut w tym samym wierszu co znacznik początkowy**

Po zaznaczeniu pierwszego atrybutu pojawia się w tym samym wierszu co znacznik początkowy elementu.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Odstępy między elementami

To ustawienie służy do kontrolowania sposobu rozmieszczenia elementów w dokumencie XAML.

**Zachowywanie nowych wierszy w zawartości**

Puste wiersze w zawartości elementu nie są usuwane.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Zwijanie wielu pustych wierszy w zawartości do jednego wiersza**

Puste wiersze w zawartości elementu są zwinięte do pojedynczego wiersza.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Usuwanie pustych wierszy w zawartości**

Wszystkie puste wiersze w zawartości elementu są usuwane.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Zobacz też

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
