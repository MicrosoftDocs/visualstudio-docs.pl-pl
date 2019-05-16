---
title: 'Instrukcje: Używanie punktów przerwania w kodzie XSLT | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: df2fb0c6505bc5fa756443bd50fdb31ff151e7d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65673675"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Instrukcje: Używanie punktów przerwania w kodzie XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz ustawić punkty przerwania w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania w tagu, gdy rozpoczyna się wykonywanie punkt przerwania zostanie przeniesione do następna instrukcja, która zawiera informacje o wiersz w źródle.  
  
 Aby uzyskać więcej informacji, zobacz [podstawy debugowania: Punkty przerwania](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustaw punkt przerwania w arkuszu stylów  
 Początkowe znaczniki, znacznikami końcowymi i węzły tekstowe arkusz stylów XSLT, można ustawić punktów przerwania. Ponadto można ustawić punktów przerwania na kod w bloku skryptu.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów  
  
1. Otworzyć arkusz stylów w edytorze XML.  
  
2. Umieść kursor w miejscu punktu przerwania, kliknij prawym przyciskiem myszy, wskaż **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.  
  
3. Kliknij przycisk Przeglądaj, przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.  
  
4. Znajdź w dokumencie źródłowym XML, a następnie kliknij przycisk **Otwórz**.  
  
     Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.  
  
5. Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustaw punkt przerwania w dokumencie źródłowym XML  
 Można ustawić punktów przerwania na elementy, atrybuty, węzeł przestrzeni nazw, komentarzy, instrukcji przetwarzania i węzły tekstowe w dokumencie źródłowym XML. Nie można ustawić punktu przerwania, w węźle dokumentu lub węzła obszaru nazw, który jest dziedziczony z elementu nadrzędnego.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie źródłowym XML  
  
1. Otwórz dokument XML w edytorze XML.  
  
2. Umieść kursor w miejscu punktu przerwania, kliknij prawym przyciskiem myszy, wskaż **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.  
  
3. Kliknij przycisk Przeglądaj, przycisk przeglądania (**...** ) na **arkusza stylów** pola w oknie właściwości dokumentu.  
  
4. Znajdź w dokumencie źródłowym XML, a następnie kliknij przycisk **Otwórz**.  
  
     Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.  
  
5. Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
