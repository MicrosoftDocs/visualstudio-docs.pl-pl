---
title: Jak programowo sprawdzać pisownię w dokumentach
description: Dowiedz się, że aby programowo sprawdzić pisownię w dokumencie, możesz użyć metody CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7e04c542f91b9d7675eb81e7a3178e3427c52a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828855"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Jak programowo sprawdzać pisownię w dokumentach
  Aby sprawdzić pisownię w dokumencie, użyj <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metody . Ta metoda zwraca wartość logiczną, która wskazuje, czy podany parametr ma poprawne pisownię.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Aby sprawdzić pisownię i wyświetlić wyniki w oknie komunikatu

1. Wywołaj metodę i przekaż jej zakres tekstu, aby <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> sprawdzić, czy występują błędy pisowni. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet113":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet113":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
