---
title: Opcje, Edytor tekstu, XML, formatowanie
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0d8420df205d49df3c6799e62adbc4e759a4aed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826523"
---
# <a name="options-text-editor-xml-formatting"></a>Opcje, Edytor tekstu, XML, formatowanie

Użyj **formatowanie** stronę właściwości, aby określić, jak sformatowane elementów i atrybutów w dokumentach XML. Aby otworzyć **opcje** okno dialogowe, kliknij przycisk **narzędzia** menu, a następnie kliknij przycisk **opcje**. Aby uzyskać dostęp do **formatowanie** właściwości rozwiń **edytora tekstów** > **XML** > **formatowanie** węzła .

## <a name="attributes"></a>Atrybuty

**Zachowaj ręczne formatowanie atrybutów**

Nie formatowania atrybutów. To ustawienie jest ustawieniem domyślnym.

> [!NOTE]
> W przypadku atrybutów w wielu wierszach, Edytor wcięcie każdego wiersza atrybutów, aby dopasować wcięcie elementu nadrzędnego.

**Wyrównaj atrybuty w osobnym wierszu**

Wyrównaj atrybuty drugie i kolejne w pionie, tak aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu atrybuty byłaby wyrównana.

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

- [Instrukcje: Tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generowanie kodu](../code-generation-in-visual-studio.md)