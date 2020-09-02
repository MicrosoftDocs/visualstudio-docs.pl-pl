---
title: Nie można utworzyć skojarzenia — Właściwość wymieniona dwukrotnie
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 50c9311ef09172ea082d2419495f26b51ff1d6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536802"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — Właściwość wymieniona dwukrotnie.

Nie można utworzyć skojarzenia \<association name> . Ta sama właściwość jest wymieniona więcej niż raz: \<property name> .

Skojarzenia są definiowane przez wybrane **właściwości skojarzenia** w oknie dialogowym **Edytor skojarzeń** . Właściwości mogą być wyświetlane tylko raz dla każdej klasy w skojarzeniu.

Właściwość w komunikacie pojawia się więcej niż jeden raz we **właściwościach skojarzenia**klasy nadrzędnej lub podrzędnej.

## <a name="to-resolve-this-condition"></a>Aby rozwiązać ten problem

- Sprawdź komunikat i zanotuj właściwość określoną w komunikacie.

- Kliknij przycisk **OK** , aby odrzucić okno komunikatu.

- Sprawdź **właściwości skojarzenia** i Usuń zduplikowane wpisy.

- Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Instrukcje: Tworzenie skojarzenia między klasami LINQ to SQL (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)