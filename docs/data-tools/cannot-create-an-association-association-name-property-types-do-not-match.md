---
title: Typy właściwości nie są zgodne
description: Nie można utworzyć skojarzenia — typy właściwości nie są zgodne. Wyświetl informacje o tym komunikacie Object Relational Designer programu Visual Studio (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8413ffd8b5bf2af4c4d7272173a9cb4d0fbf6cbc
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518469"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Nie można utworzyć &lt; nazwy skojarzenia skojarzenia &gt; — typy właściwości nie są zgodne.

Nie można utworzyć skojarzenia \<association name> — typy właściwości nie są zgodne. Właściwości nie mają pasujących typów: \<property names> .

Skojarzenia są definiowane przez wybrane **właściwości skojarzenia** w oknie dialogowym **Edytor skojarzeń** . Właściwości po obu stronach skojarzenia muszą być tego samego typu danych.

Właściwości wymienione w komunikacie nie mają tych samych typów danych.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź komunikat i zanotuj właściwości wywołane w komunikacie.

2. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

3. Sprawdź **właściwości skojarzenia** i wybierz właściwości tego samego typu danych.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Instrukcje: Tworzenie skojarzenia między klasami LINQ to SQL (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)