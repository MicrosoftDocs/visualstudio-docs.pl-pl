---
title: 'Instrukcje: używanie punktów przerwania z XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656304"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Instrukcje: używanie punktów przerwania w kodzie XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Punkty przerwania można ustawić w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania na znaczniku, po rozpoczęciu wykonywania punkt przerwania przejdzie do następnej instrukcji, która zawiera informacje o wierszu źródła.

 Aby uzyskać więcej informacji, zobacz podstawowe informacje o [debugowaniu: punkty przerwania](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustawianie punktu przerwania w arkuszu stylów
 Punkty przerwania można ustawić dla tagów początkowych, tagów końcowych i węzłów tekstowych arkusza stylów XSLT. Punkty przerwania można także ustawiać w kodzie w bloku skryptu.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów

1. Otwórz arkusz stylów w edytorze XML.

2. Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż punkt **przerwania**, a następnie kliknij polecenie **Wstaw punkt przerwania**.

3. Kliknij przycisk Przeglądaj ( **..** .) w polu **wejściowym** okna właściwości dokumentu.

4. Znajdź dokument źródłowy XML i kliknij przycisk **Otwórz**.

     Ustawia plik dokumentu źródłowego używany do przekształcania XSLT.

5. Kliknij przycisk **DEBUGUJ XSL** na pasku narzędzi edytora XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustawianie punktu przerwania w dokumencie źródłowym XML
 Punkty przerwania można ustawić dla elementów, atrybutów, węzła obszaru nazw, komentarzy, instrukcji przetwarzania i węzłów tekstowych dokumentu źródłowego XML. Nie można ustawić punktu przerwania w węźle dokumentu lub w węźle przestrzeni nazw, który jest Dziedziczony z elementu nadrzędnego.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie źródłowym XML

1. Otwórz dokument XML w edytorze XML.

2. Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż punkt **przerwania**, a następnie kliknij polecenie **Wstaw punkt przerwania**.

3. Kliknij przycisk przeglądania Przeglądaj ( **...** ) w polu **arkusz stylów** okna właściwości dokumentu.

4. Znajdź dokument źródłowy XML i kliknij przycisk **Otwórz**.

     Ustawia plik dokumentu źródłowego używany do przekształcania XSLT.

5. Kliknij przycisk **DEBUGUJ XSL** na pasku narzędzi edytora XML.

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
