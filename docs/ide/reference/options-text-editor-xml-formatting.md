---
title: Opcje, Edytor tekstu, XML, formatowanie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e20b2f7ebe351aa050ea66468fb33aba8e4a31bc
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525072"
---
# <a name="options-text-editor-xml-formatting"></a>Opcje, Edytor tekstu, XML, formatowanie

Użyj **formatowanie** Strona opcji, aby określić, jak sformatowane elementów i atrybutów w dokumentach XML. Aby uzyskać dostęp do opcji formatowania, XML, wybierz opcję **narzędzia** > **opcje** > **edytora tekstów** > **XML**, a następnie wybierz **formatowanie**.

## <a name="attributes"></a>Atrybuty

**Zachowaj ręczne formatowanie atrybutów**

Nie formatowania atrybutów. To ustawienie jest ustawieniem domyślnym.

> [!NOTE]
> W przypadku atrybutów w wielu wierszach, Edytor wcięcie każdego wiersza atrybutów, aby dopasować wcięcie elementu nadrzędnego.

**Wyrównaj atrybuty w osobnym wierszu**

Wyrównaj atrybuty drugie i kolejne w pionie, tak aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu byłaby wyrównana atrybuty:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatycznie Formatuj ponownie

**Przy wklejaniu ze Schowka**

Formatowania tekstu XML wklejonych ze Schowka.

**Po zakończeniu tagu końcowego**

Formatowania elementu, po zakończeniu tagu końcowego.

## <a name="mixed-content"></a>Zawartość mieszana

**Formatuj zawartość mieszaną domyślnie.**

Próba ponownego sformatowania zawartość mieszana, z wyjątkiem sytuacji, gdy zawartość znajduje się w `xml:space="preserve"` zakresu. To ustawienie jest ustawieniem domyślnym.

Jeśli element zawiera tekst i znacznik, uznaje się zawartość mieszaną zawartość i być. Poniżej przedstawiono przykład elementu z zawartością mieszane.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz także

- [Opcje XML — różne](options-text-editor-xml-miscellaneous.md)
- [Narzędzia XML w programie Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)