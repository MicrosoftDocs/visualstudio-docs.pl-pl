---
title: Opcje, Edytor tekstu, XML, Formatowanie
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568142"
---
# <a name="options-text-editor-xml-formatting"></a>Opcje, Edytor tekstu, XML, Formatowanie

Strona Opcje **formatowania** służy do określania sposobu formatowania elementów i atrybutów w dokumentach XML. Aby uzyskać dostęp do opcji formatowania XML, wybierz pozycję**Opcje** >  **narzędzi** > **Edytor** > tekstu**XML**, a następnie wybierz pozycję **Formatowanie**.

## <a name="attributes"></a>Atrybuty

**Zachowywanie ręcznego formatowania atrybutów**

Nie należy formatować atrybutów. Jest to ustawienie domyślne.

> [!NOTE]
> Jeśli atrybuty znajdują się w wielu wierszach, edytor wcięcie każdego wiersza atrybutów, aby dopasować wcięcie elementu nadrzędnego.

**Wyrównywanie atrybutów w osobnym wierszu**

Wyrównaj drugi i kolejnych atrybutów w pionie, aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu wyrównania atrybutów:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatyczne formaterat

**Podczas wklejania ze schowka**

Sformatuj tekst XML wklejony ze schowka.

**Po zakończeniu tagu końcowego**

Sformatować element po zakończeniu tagu końcowego.

## <a name="mixed-content"></a>Zawartość mieszana

**Domyślnie formatuj zawartość mieszaną.**

Spróbuj sformatować zawartość mieszaną, z `xml:space="preserve"` wyjątkiem sytuacji, gdy zawartość zostanie znaleziona w zakresie. Jest to ustawienie domyślne.

Jeśli element zawiera kombinację tekstu i znaczników, zawartość jest uważana za zawartość mieszaną. Poniżej znajduje się przykład elementu o mieszanej zawartości.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz też

- [Opcje XML — różne](options-text-editor-xml-miscellaneous.md)
- [Narzędzia XML w Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
