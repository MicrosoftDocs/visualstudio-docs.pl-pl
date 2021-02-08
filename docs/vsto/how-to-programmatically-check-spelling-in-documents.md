---
title: 'Instrukcje: Programowane sprawdzanie pisowni w dokumentach'
description: Aby programowo sprawdzić pisownię w dokumencie, można użyć metody CheckSpelling.
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
ms.openlocfilehash: 9afbb96cce5848894c83c8780e5855eadc0e59d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836140"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Instrukcje: Programowane sprawdzanie pisowni w dokumentach
  Aby sprawdzić pisownię w dokumencie, użyj <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metody. Ta metoda zwraca wartość logiczną wskazującą, czy podany parametr jest wpisany poprawnie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Aby sprawdzić pisownię i wyświetlić wyniki w oknie komunikatu

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodę i przekaż ją do zakresu tekstu, aby sprawdzić, czy występują błędy pisowni. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
