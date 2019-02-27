---
title: Opcje, Edytor tekstu, XAML, formatowanie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74495c068cbd476014fa2c10088239e096d42f02
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840938"
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **formatowanie** stronę właściwości, aby określić, jak sformatowane elementów i atrybutów w dokumencie XAML. Aby otworzyć **opcje** okno dialogowe, kliknij przycisk **narzędzia** menu, a następnie kliknij przycisk **opcje**. Aby uzyskać dostęp do **formatowanie** właściwości rozwiń **edytora tekstów**, **XAML**, **formatowanie** węzła.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Automatyczne formatowanie zdarzeń
Automatyczne formatowanie może wystąpić, gdy dowolne z następujących zdarzeń wykryte.

- Uzupełnianie tagu końcowego lub prostego.

- Uzupełnianie tagu początkowego.

- Wklejanie ze Schowka.

- Formatowanie klawiaturowych.

  Można określić, zdarzenia, które powodują automatyczne formatowanie.

|||
|-|-|
|**Po zakończeniu tagu końcowego lub prostego**|Automatyczne formatowanie występuje po zakończeniu wpisywania tagu końcowego lub prostego tagu. Prostych tagów nie ma atrybutów, na przykład `<Button />`.|
|**Po zakończeniu tagu początkowego**|Automatyczne formatowanie występuje po zakończeniu wpisywania tagu początkowego.|
|**Przy wklejaniu ze Schowka**|Automatyczne formatowanie występuje podczas wklejania XAML ze Schowka w widoku XAML.|

## <a name="quotation-mark-style"></a>Styl cudzysłowu
To ustawienie wskazuje, czy wartości atrybutów są ujęte w pojedyncze lub podwójne znaki cudzysłowu. Użyj tego ustawienia, element formatujący automatycznie i automatycznego uzupełniania IntelliSense.

Po ustawieniu tej opcji tylko atrybuty później dodane przy użyciu narzędzia Projektant lub ręcznie w widoku XAML dotyczy problem.

|||
|-|-|
|**Podwójny cudzysłów (")**|Wartości atrybutów są ujęte w cudzysłów.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Pojedynczy cudzysłów (')**|Wartości atrybutów są ujęte w apostrofy.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Zawijanie tagów
Można określić długość wiersza zawijanie tagów. Po włączeniu zawijanie tagów XAML, wszystkie dodane przy użyciu narzędzia Projektant zostanie zawinięta odpowiednio.

|||
|-|-|
|**Zawijaj tagi przekraczające określoną długość**|Określa, czy wiersze są opakowane w określonej przez długość wiersza **długość**.|
|**Długość**|Liczba znaków, które mogą zawierać wiersz. Jeśli to konieczne, niektóre linie XAML może przekraczać długości określonej linii.|

## <a name="attribute-spacing"></a>Odstępy między atrybutami
To ustawienie służy do kontrolowania, jak atrybuty są rozmieszczone w dokumencie XAML

|||
|-|-|
|**Zachowaj tabulacji i spacje między atrybutami**|Nowe wiersze i spacje między atrybutami nie dotyczy automatyczne formatowanie.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Wstaw odstęp między atrybutami**|Atrybuty zajmują jeden wiersz z jednego miejsca oddzielenie sąsiadujących atrybutów. Ustawienia zawijania tag są stosowane.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Umieść każdy atrybut w osobnym wierszu**|Każdy atrybut zajmuje swój własny wiersz. Jest to przydatne, jeśli podano wiele atrybutów.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Pozycja pierwszego atrybutu w tym samym wierszu co tag początkowy**|Po zaznaczeniu tej opcji, w tym samym wierszu co tag początkowy element pojawi się pierwszy atrybut.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Odstępy między elementami
Użyj tego ustawienia, aby kontrolować sposób rozmieszczenia elementów w dokumencie XAML

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Zachowaj nowe wiersze w zawartości**                             | Puste wiersze w zawartości elementu nie są usuwane.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Zwiń wiele puste wiersze w zawartości w jeden wiersz** | Puste wiersze w zawartości elementu są zwinięte do pojedynczego wiersza.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Usuń puste wiersze w zawartości**                             | Wszystkie puste wiersze w zawartości elementu są usuwane.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Automatyczne wstawianie
To ustawienie służy do kontrolowania, kiedy tagów i cudzysłowy są generowane automatycznie.

|||
|-|-|
|**Taga zamykającego**|Określa, czy tag zamykający elementu jest generowana automatycznie, gdy zamkniesz otwierający tag o rozmiarze większym niż znak większości (>).|
|**Cudzysłowy atrybutu**|Określa, czy otaczającej cudzysłowy są generowane w przypadku wybrania wartości atrybutu z listy rozwijanej uzupełniania instrukcji.|
|**Zamykające nawiasy klamrowe dla wyrażeń MarkupExtension**|Określa, czy jako rozszerzenie znacznika zamykającego nawiasu klamrowego (}) jest generowany automatycznie po wpisaniu otwierający nawias klamrowy znak ({}).|
|**Przecinków do oddzielenia parametry wyrażeń MarkupExtension**|Określa, czy przecinkami są generowane, gdy więcej niż jeden parametr jest typu rozszerzenia znaczników.|

## <a name="default-view"></a>Widok domyślny
Użyj to ustawienie, aby określić, czy widok projektu jest wyświetlany, gdy dokumenty XAML są ładowane.

|||
|-|-|
|**Zawsze otwieranie dokumentów w pełnego widoku XAML**|Określa, czy dokumenty XAML są wyświetlane tylko w widoku XAML, bez widoku projektu. Przydatne w przypadku ładowania dużych dokumentów.|

## <a name="toolbox"></a>Przybornik
To ustawienie umożliwia określenie, czy kontrolki użytkownika i kontrolki niestandardowe są wyświetlane w przyborniku.

|||
|-|-|
|**Automatycznie wypełnij elementy przybornika**|Określa, czy kontrolki użytkownika i niestandardowe formanty w bieżącym rozwiązaniu są wyświetlane w przyborniku automatycznie.|

## <a name="see-also"></a>Zobacz też
[XAML w WPF](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)  
[Instrukcje: Zmienianie ustawień widoku XAML](http://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47)  
[XAML i przewodniki po kodzie](http://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
