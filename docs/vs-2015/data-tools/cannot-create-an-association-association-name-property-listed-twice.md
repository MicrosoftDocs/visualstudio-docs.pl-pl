---
title: Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — Właściwość wyświetlana dwukrotnie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662558"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — Właściwość wymieniona dwukrotnie.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można utworzyć skojarzenia \<association name> . Ta sama właściwość jest wymieniona więcej niż raz: \<property name> .

 Skojarzenia są definiowane przez wybrane **właściwości skojarzenia** w oknie dialogowym **Edytor skojarzeń** . Właściwości mogą być wyświetlane tylko raz dla każdej klasy w skojarzeniu.

 Właściwość w komunikacie pojawia się więcej niż jeden raz we **właściwościach skojarzenia**klasy nadrzędnej lub podrzędnej.

### <a name="to-resolve-this-condition"></a>Aby rozwiązać ten problem

- Sprawdź komunikat i zanotuj właściwość określoną w komunikacie.

- Kliknij przycisk **OK** , aby odrzucić okno komunikatu.

- Sprawdź **właściwości skojarzenia** i Usuń zduplikowane wpisy.

- Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [LINQ to SQL narzędzia w programie Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [: Tworzenie skojarzenia (relacji) między klasami LINQ to SQL (Projektant o/r)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [: tworzenie klas LINQ to SQL (projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
