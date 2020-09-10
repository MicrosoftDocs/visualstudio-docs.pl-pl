---
title: Właściwość wyświetlana dwukrotnie
description: Nie można utworzyć skojarzenia — Właściwość wymieniona dwukrotnie
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c496a25b093c88cca68d31bd22ccc6deca9a33a
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743197"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — Właściwość wymieniona dwukrotnie.

Nie można utworzyć skojarzenia \<association name> . Ta sama właściwość jest wymieniona więcej niż raz: \<property name> .

Skojarzenia są definiowane przez wybrane **właściwości skojarzenia** w oknie dialogowym **Edytor skojarzeń** . Właściwości mogą być wyświetlane tylko raz dla każdej klasy w skojarzeniu.

Właściwość w komunikacie pojawia się więcej niż jeden raz we **właściwościach skojarzenia**klasy nadrzędnej lub podrzędnej.

## <a name="to-resolve-this-condition"></a>Aby rozwiązać ten problem

- Sprawdź komunikat i zanotuj właściwość określoną w komunikacie.

- Kliknij przycisk **OK** , aby odrzucić okno komunikatu.

- Sprawdź **właściwości skojarzenia** i Usuń zduplikowane wpisy.

- Kliknij pozycję **OK**.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Instrukcje: Tworzenie skojarzenia między klasami LINQ to SQL (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)