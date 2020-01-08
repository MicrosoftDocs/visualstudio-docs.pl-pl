---
title: Opcje, Edytor tekstu, XML, formatowanie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568142"
---
# <a name="options-text-editor-xml-formatting"></a>Opcje, Edytor tekstu, XML, formatowanie

Na stronie opcje **formatowania** można określić sposób formatowania elementów i atrybutów w dokumentach XML. Aby uzyskać dostęp do opcji formatowania XML, wybierz **narzędzia** > **Opcje** > **edytorze tekstów** > **XML**, a następnie wybierz **Formatowanie**.

## <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

**Zachowaj ręczne formatowanie atrybutów**

Nie należy formatować atrybutów. To ustawienie jest ustawieniem domyślnym.

> [!NOTE]
> Jeśli atrybuty są w wielu wierszach, Edytor Wetnij każdy wiersz atrybutów, aby dopasować wcięcia elementu nadrzędnego.

**Wyrównaj atrybuty każdy w osobnym wierszu**

Wyrównaj drugą i kolejne atrybuty w pionie, aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu wyrównania atrybutów:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Autoformatowanie

**Przy wklejaniu ze schowka**

Umożliwia sformatowanie tekstu XML wklejonego ze schowka.

**Po zakończeniu tagu końcowego**

Ponownie sformatuj element po zakończeniu znacznika końcowego.

## <a name="mixed-content"></a>Zawartość mieszana

**Domyślnie sformatuj zawartość mieszaną.**

Spróbuj ponownie sformatować zawartość mieszaną, z wyjątkiem sytuacji, gdy zawartość znajduje się w zakresie `xml:space="preserve"`. To ustawienie jest ustawieniem domyślnym.

Jeśli element zawiera mieszankę tekstu i znaczników, zawartość jest traktowana jako zawartość mieszana. Poniżej znajduje się przykład elementu z zawartością mieszaną.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz także

- [Opcje XML — różne](options-text-editor-xml-miscellaneous.md)
- [Narzędzia XML w programie Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
