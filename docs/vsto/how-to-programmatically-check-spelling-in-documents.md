---
title: 'Instrukcje: Programowe sprawdzanie pisowni w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26eb7e0798fbcf6aad33dd45892a23fb0d54b812
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110092"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Instrukcje: Programowe sprawdzanie pisowni w dokumentach
  Aby sprawdzić pisownię w dokumencie, należy użyć <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metody. Ta metoda zwraca wartość logiczną, wskazującą, czy podany parametr została wpisana poprawnie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Sprawdź pisownię i wyświetlić wyniki w oknie komunikatu

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metody i przekazać go zakres tekstu pod kątem błędów pisowni. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
