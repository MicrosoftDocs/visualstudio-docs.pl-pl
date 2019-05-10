---
title: Nie można usunąć właściwości, ponieważ uczestniczy w skojarzeniu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d277919229316768cde27efdc9b2797d0351e9fe
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458501"
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

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)