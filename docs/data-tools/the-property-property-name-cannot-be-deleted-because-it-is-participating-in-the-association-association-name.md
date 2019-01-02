---
title: Nie można usunąć właściwości, ponieważ uczestniczy w skojarzeniu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4e2d519a8b35d10b3dbf71695b75e77ee6309885
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896581"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt;

Wybrana właściwość jest ustawiona jako **właściwość skojarzenia** skojarzenia między klasami wskazanego w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są one skojarzenia między klasami danych.

Ustaw **właściwość skojarzenia** różne właściwości klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz linię skojarzenia na **O/R Designer** nawiązujący połączenie z klas danych wskazany w komunikacie o błędzie.

2. Kliknij dwukrotnie wiersz, aby otworzyć **Edytor skojarzeń** okno dialogowe.

3. Usuń właściwość z **właściwości skojarzenia**.

4. Ponownie spróbuj usunąć właściwość.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)