---
title: Opcje, Edytor tekstu, XAML, formatowanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 319e09d2438b23c217f7820fe4288758a595be56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662221"
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na stronie właściwości **formatowania** można określić sposób formatowania elementów i atrybutów w dokumentach XAML. Aby otworzyć okno dialogowe **Opcje** , kliknij menu **Narzędzia** , a następnie kliknij przycisk **Opcje**. Aby uzyskać dostęp do strony właściwości **formatowania** , rozwiń węzeł **Edytor tekstu**, **XAML**, **Formatowanie** .

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Zdarzenia Autoformatowania
Autoformatowanie może wystąpić, gdy zostanie wykryte dowolne z poniższych zdarzeń.

- Ukończenie tagu końcowego lub tagu prostego.

- Wykonanie tagu początkowego.

- Wklejanie ze schowka.

- Formatowanie poleceń klawiatury.

  Można określić, które zdarzenia będą powodowały Autoformatowanie.

|||
|-|-|
|**Po zakończeniu tagu końcowego lub tagu prostego**|Autoformatowanie występuje po zakończeniu wpisywania tagu końcowego lub tagu prostego. Tag prosty nie ma żadnych atrybutów, na przykład `<Button />`.|
|**Po zakończeniu tagu początkowego**|Autoformatowanie występuje po zakończeniu wpisywania tagu początkowego.|
|**Przy wklejaniu ze schowka**|Autoformatowanie występuje po wklejeniu kodu XAML ze schowka do widoku XAML.|

## <a name="quotation-mark-style"></a>Styl cudzysłowu
To ustawienie wskazuje, czy wartości atrybutów są ujęte w znaki pojedynczego lub podwójnego cudzysłowu. To ustawienie umożliwia Autouzupełnienie programów Autostart i IntelliSense.

Po ustawieniu tej opcji będzie to miało zastosowanie tylko atrybuty dodane w projektancie lub ręcznie w widoku XAML.

|||
|-|-|
|**Podwójne cudzysłowy (")**|Wartości atrybutów są ujęte w cudzysłów.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Apostrofy (')**|Wartości atrybutów są ujęte w apostrofy.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Zawijanie tagów
Możesz określić długość linii dla zawijania tagów. Gdy funkcja zawijania tagów jest włączona, wszystkie XAML dodane później za pomocą projektanta zostaną odpowiednio opakowane.

|||
|-|-|
|**Zawijaj tagi, które przekraczają określoną długość**|Określa, czy linie są opakowane w długości linii określonej przez **Długość**.|
|**Długość**|Liczba znaków, jaką może zawierać linia. W razie potrzeby niektóre linie XAML mogą przekroczyć określoną długość wiersza.|

## <a name="attribute-spacing"></a>Odstępy między atrybutami
Użyj tego ustawienia, aby kontrolować sposób, w jaki atrybuty są rozmieszczone w dokumencie XAML

|||
|-|-|
|**Zachowaj znaki nowego wiersza i odstępy między atrybutami**|Autoformatowanie nie ma wpływ na nowe wiersze i odstępy między atrybutami.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Wstaw pojedyncze odstępy między atrybutami**|Atrybuty zajmują jedną linię, z jedną spacją oddzielającą sąsiednie atrybuty. Ustawienia zawijania tagów są stosowane.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Umieść każdy atrybut w osobnym wierszu**|Każdy atrybut zajmuje własny wiersz. Jest to przydatne, gdy istnieje wiele atrybutów.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Umieść pierwszy atrybut w tym samym wierszu co tag początkowy**|Po zaznaczeniu ten pierwszy atrybut jest wyświetlany w tym samym wierszu co tag początkowy elementu.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Odstępy elementów
Użyj tego ustawienia, aby kontrolować sposób ułożenia elementów w dokumencie XAML

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Zachowaj nowe wiersze w zawartości**                             | Puste wiersze w zawartości elementu nie są usuwane.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Zwiń wiele pustych wierszy w zawartości do pojedynczego wiersza** | Puste wiersze w zawartości elementu są zwijane do jednego wiersza.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Usuń puste wiersze w zawartości**                             | Wszystkie puste wiersze w zawartości elementu są usuwane.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Autowstawianie
To ustawienie służy do określania, kiedy Tagi i cudzysłowy są generowane automatycznie.

|||
|-|-|
|**Tagi zamykające**|Określa, czy tag zamykający elementu jest generowany automatycznie po zamknięciu tagu otwierającego o znaku większości (>).|
|**Cudzysłowy atrybutów**|Określa, czy otaczające cudzysłowy są generowane, gdy wartość atrybutu jest wybierana z listy rozwijanej uzupełniania instrukcji.|
|**Zamykające nawiasy klamrowe dla wyrażeń MarkupExtension**|Określa, czy zamykający nawias klamrowy rozszerzenia znacznika (}) jest generowany automatycznie po wpisaniu otwierającego znaku nawiasu klamrowego ({).|
|**Przecinki oddzielające parametry wyrażeń MarkupExtension**|Określa, czy przecinki są generowane po wpisaniu więcej niż jednego parametru w rozszerzeniu znacznika.|

## <a name="default-view"></a>Widok domyślny
Użyj tego ustawienia, aby określić, czy widok Projekt pojawia się po załadowaniu dokumentów XAML.

|||
|-|-|
|**Zawsze otwieraj dokumenty w pełnym widoku XAML**|Określa, czy dokumenty XAML są wyświetlane tylko w widoku XAML, bez widok Projekt. Przydatne do ładowania dużych dokumentów.|

## <a name="toolbox"></a>Przybornik
Użyj tego ustawienia, aby określić, czy kontrolki użytkownika i kontrolki niestandardowe są wyświetlane w przyborniku.

|||
|-|-|
|**Automatycznie Wypełnij elementy przybornika**|Określa, czy kontrolki użytkownika i kontrolki niestandardowe w bieżącym rozwiązaniu są automatycznie wyświetlane w przyborniku.|

## <a name="see-also"></a>Zobacz też
[XAML w WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) 
[instrukcje: Zmienianie ustawień widoku XAML](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47) 
[języka XAML i instruktażów kodu](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
