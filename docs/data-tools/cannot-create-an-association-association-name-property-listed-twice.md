---
title: Właściwość wyświetlana dwukrotnie
description: Nie można utworzyć skojarzenia-właściwości wymienionej dwukrotnie. Wyświetl informacje o tym komunikacie Object Relational Designer programu Visual Studio (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4466515f390db2ac3c03d302fd6ffb8da3a6176f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867350"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — Właściwość wymieniona dwukrotnie.

Nie można utworzyć skojarzenia \<association name> . Ta sama właściwość jest wymieniona więcej niż raz: \<property name> .

Skojarzenia są definiowane przez wybrane **właściwości skojarzenia** w oknie dialogowym **Edytor skojarzeń** . Właściwości mogą być wyświetlane tylko raz dla każdej klasy w skojarzeniu.

Właściwość w komunikacie pojawia się więcej niż jeden raz we **właściwościach skojarzenia** klasy nadrzędnej lub podrzędnej.

## <a name="to-resolve-this-condition"></a>Aby rozwiązać ten problem

- Sprawdź komunikat i zanotuj właściwość określoną w komunikacie.

- Kliknij przycisk **OK** , aby odrzucić okno komunikatu.

- Sprawdź **właściwości skojarzenia** i Usuń zduplikowane wpisy.

- Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Instrukcje: Tworzenie skojarzenia między klasami LINQ to SQL (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)