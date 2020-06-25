---
title: Nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3e7a5063846e05fd55880e1727dd829c2db0c3a5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281399"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>&lt;Nie można usunąć nazwy właściwości właściwości, &gt; ponieważ uczestniczy ona w &lt; nazwie skojarzenia skojarzenia&gt;

Wybrana właściwość jest ustawiana jako **Właściwość skojarzenia** dla skojarzenia między klasami wskazanymi w komunikacie o błędzie. Właściwości nie mogą zostać usunięte, jeśli uczestniczą w skojarzeniu między klasami danych.

Ustaw **Właściwość skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz linię skojarzenie w **projektancie o/R** , który łączy klasy danych wskazane w komunikacie o błędzie.

2. Kliknij dwukrotnie wiersz, aby otworzyć okno dialogowe **Edytor skojarzeń** .

3. Usuń właściwość ze **właściwości skojarzenia**.

4. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)