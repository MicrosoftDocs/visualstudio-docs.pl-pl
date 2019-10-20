---
title: Nie można usunąć właściwości
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 29344a2443708d9ddaed3d90a186ab8424638664
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640486"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Nie można usunąć właściwości \<property nazwy >

Nie można usunąć właściwości \<property >, ponieważ jest ona ustawiona jako **właściwość rozróżniacza** dla dziedziczenia między \<class nazw > i \<class >

Wybrana właściwość jest ustawiana jako **właściwość rozróżniacza** dla dziedziczenia między klasami wskazanymi w komunikacie o błędzie. Nie można usunąć właściwości, jeśli uczestniczą w konfiguracji dziedziczenia między klasami danych.

Ustaw **Właściwość dyskryminatora** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W **projektancie o/R**wybierz linię dziedziczenia, która łączy klasy danych wskazane w komunikacie o błędzie.

2. Ustaw właściwość **dyskryminatora** na inną właściwość.

3. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)