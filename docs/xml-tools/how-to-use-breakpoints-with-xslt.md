---
title: 'Instrukcje: Używanie punktów przerwania w kodzie XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72a22937792cc06bcac18f70a2bd4c53be98f7fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894892"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Instrukcje: Używanie punktów przerwania w kodzie XSLT

Możesz ustawić punkty przerwania w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania w tagu, gdy rozpoczyna się wykonywanie punkt przerwania zostanie przeniesione do następna instrukcja, która zawiera informacje o wiersz w źródle.

Aby uzyskać więcej informacji, zobacz [podstawy debugowania: Punkty przerwania](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustaw punkt przerwania w arkuszu stylów

Początkowe znaczniki, znacznikami końcowymi i węzły tekstowe arkusz stylów XSLT, można ustawić punktów przerwania. Ponadto można ustawić punktów przerwania na kod w bloku skryptu.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów

1.  Otworzyć arkusz stylów w edytorze XML.

2.  Umieść kursor w miejscu punktu przerwania, kliknij prawym przyciskiem myszy, wskaż **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.

3.  Kliknij przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.

4.  Znajdź w dokumencie źródłowym XML, a następnie kliknij przycisk **Otwórz**.

     Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.

5.  Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustaw punkt przerwania w dokumencie źródłowym XML

Można ustawić punktów przerwania na elementy, atrybuty, węzeł przestrzeni nazw, komentarzy, instrukcji przetwarzania i węzły tekstowe w dokumencie źródłowym XML. Nie można ustawić punktu przerwania, w węźle dokumentu lub węzła obszaru nazw, który jest dziedziczony z elementu nadrzędnego.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie źródłowym XML

1.  Otwórz dokument XML w edytorze XML.

2.  Umieść kursor w miejscu punktu przerwania, kliknij prawym przyciskiem myszy, wskaż **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.

3.  Kliknij przycisk przeglądania (**...** ) na **arkusza stylów** pola w oknie właściwości dokumentu.

4.  Znajdź w dokumencie źródłowym XML, a następnie kliknij przycisk **Otwórz**.

     Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.

5.  Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)