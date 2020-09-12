---
title: Właściwość uczestniczy w skojarzeniu
description: Nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d473c3aa83bc5ac4ca802067b9b9eb32073d32f1
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036213"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>&lt;Nie można usunąć nazwy właściwości właściwości, &gt; ponieważ uczestniczy ona w &lt; nazwie skojarzenia skojarzenia&gt;

Wybrana właściwość jest ustawiana jako **Właściwość skojarzenia** dla skojarzenia między klasami wskazanymi w komunikacie o błędzie. Właściwości nie mogą zostać usunięte, jeśli uczestniczą w skojarzeniu między klasami danych.

Ustaw **Właściwość skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz linię skojarzenie w **projektancie o/R** , który łączy klasy danych wskazane w komunikacie o błędzie.

2. Kliknij dwukrotnie wiersz, aby otworzyć okno dialogowe **Edytor skojarzeń** .

3. Usuń właściwość ze **właściwości skojarzenia**.

4. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)