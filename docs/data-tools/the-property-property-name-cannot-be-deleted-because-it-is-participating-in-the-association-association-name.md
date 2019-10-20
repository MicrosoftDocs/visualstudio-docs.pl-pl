---
title: Nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e1890535fb008c8e8be6ee9dea0eda3ab3844da6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648147"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Nie można usunąć właściwości &lt;property &gt;, ponieważ uczestniczy ona w nazwie &lt;association skojarzenia &gt;

Wybrana właściwość jest ustawiana jako **Właściwość skojarzenia** dla skojarzenia między klasami wskazanymi w komunikacie o błędzie. Właściwości nie mogą zostać usunięte, jeśli uczestniczą w skojarzeniu między klasami danych.

Ustaw **Właściwość skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz linię skojarzenie w **projektancie o/R** , który łączy klasy danych wskazane w komunikacie o błędzie.

2. Kliknij dwukrotnie wiersz, aby otworzyć okno dialogowe **Edytor skojarzeń** .

3. Usuń właściwość ze **właściwości skojarzenia**.

4. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)