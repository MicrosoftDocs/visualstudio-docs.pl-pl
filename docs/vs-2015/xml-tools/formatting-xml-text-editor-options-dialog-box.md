---
title: Formatowanie, XML, Edytor tekstu, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670970"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatowanie, XML, Edytor tekstu, Opcje, okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe umożliwia określenie ustawień formatowania dla edytora XML. Dostęp do okna dialogowego **Opcje** można uzyskać z menu **Narzędzia** .

> [!NOTE]
> Te ustawienia są dostępne po wybraniu folderu **Edytor tekstu** , folderu **XML** , a następnie opcji **formatowania** z okna dialogowego **Opcje** .

## <a name="attributes"></a>Atrybuty
 **Zachowaj ręczne formatowanie atrybutów** Atrybuty nie są formatowane ponownie. Domyślnie włączone.

> [!NOTE]
> Jeśli atrybuty są w wielu wierszach, Edytor Wetnij każdy wiersz atrybutów, aby dopasować wcięcia elementu nadrzędnego.

 **Wyrównaj atrybuty każdy w osobnym wierszu** Wyrównuje drugie i kolejne atrybuty w pionie, aby dopasować wcięcie pierwszego atrybutu. Następujący tekst XML jest przykładem sposobu wyrównania atrybutów.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Autoformatowanie
 **Przy wklejaniu ze schowka** Umożliwia sformatowanie tekstu XML wklejonego ze schowka.

 **Po zakończeniu tagu końcowego** Ponownie formatuje element po zakończeniu znacznika końcowego.

## <a name="mixed-content"></a>Zawartość mieszana
 **Domyślnie zachowuj zawartość mieszaną** Określa, czy Edytor formatuje zawartość mieszaną. Domyślnie edytor próbuje ponownie sformatować zawartość mieszaną, z wyjątkiem przypadków, gdy zawartość znajduje się w zakresie `xml:space="preserve"`.

 Jeśli element zawiera mieszankę tekstu i znaczników, zawartość jest traktowana jako zawartość mieszana. Poniżej znajduje się przykład elementu z zawartością mieszaną.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Zobacz też
 [Właściwości dokumentu XML,](../xml-tools/xml-document-properties-properties-window.md) [Składniki edytora XML](../xml-tools/xml-editor-components.md) okna właściwości
