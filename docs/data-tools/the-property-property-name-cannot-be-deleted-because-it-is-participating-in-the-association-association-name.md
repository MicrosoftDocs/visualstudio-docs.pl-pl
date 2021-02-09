---
title: Właściwość uczestniczy w skojarzeniu
description: Nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu. Wyświetl informacje na temat tego komunikatu o tym Object Relational Designer (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 99115a3c04aec71e7d000dfa4e707eacb0e28cf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866401"
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