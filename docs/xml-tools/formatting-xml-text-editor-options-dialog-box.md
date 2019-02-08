---
title: Formatowanie, XML, Edytor tekstu, Opcje, okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79b34c30e3d00e4f145a32acbaf769d13888298d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923204"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatowanie, XML, Edytor tekstu, okno dialogowe Opcje

To okno dialogowe umożliwia określenie ustawień formatowania edytora XML. Możesz uzyskać dostęp **opcje** okno dialogowe z **narzędzia** menu.

> [!NOTE]
> Te ustawienia są dostępne po wybraniu **edytora tekstów** folderze **XML** folder, a następnie **formatowanie** opcję **opcje** okno dialogowe.

## <a name="attributes"></a>Atrybuty
 **Zachowaj ręczne formatowanie atrybutów**

 Atrybuty nie są ponownie sformatowany. Domyślnie włączone.

> [!NOTE]
> W przypadku atrybutów w wielu wierszach, Edytor wcięcie każdego wiersza atrybutów, aby dopasować wcięcie elementu nadrzędnego.

 **Wyrównaj atrybuty na własnej linii**

 Wyrównuje drugim i kolejnych atrybutów w pionie, aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu atrybuty byłaby wyrównana.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatycznie Formatuj ponownie
 **Przy wklejaniu ze Schowka**

 Formatuje tekst XML wklejonych ze Schowka.

 **Po zakończeniu tagu końcowego**

 Formatuje element, po zakończeniu tagu końcowego.

## <a name="mixed-content"></a>Zawartość mieszana
 **Zachowaj zawartość mieszana domyślnie**

 Określa, czy edytor formatuje zawartość mieszana. Domyślnie, próbuje ponownie Formatuj zawartość mieszaną, z wyjątkiem sytuacji, gdy zawartość znajduje się w edytorze `xml:space="preserve"` zakresu.

 Jeśli element zawiera tekst i znacznik, uznaje się zawartość mieszaną zawartość i być. Oto przykład elementu z zawartością mieszane.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz także

- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)