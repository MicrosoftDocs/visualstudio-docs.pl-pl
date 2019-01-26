---
title: Nie można usunąć właściwości
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 6940da198fddc4213bbec1271164b20cfbeb6672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994163"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Właściwość \<nazwa właściwości > nie można usunąć

Właściwość \<nazwa właściwości > nie można usunąć, ponieważ jest ona ustawiona jako **właściwość rozróżniacza** dziedziczenia między \<Nazwa klasy > i \<Nazwa klasy >

Wybrana właściwość jest ustawiona jako **właściwość rozróżniacza** dziedziczenia między klasami wskazanego w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są one Konfigurowanie dziedziczenia między klasami danych.

Ustaw **właściwość rozróżniacza** różne właściwości klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W **O/R Designer**, wybierz linię dziedziczenia, który nawiązuje połączenie klas danych wskazany w komunikacie o błędzie.

2. Ustaw **dyskryminatora** właściwości inną właściwość.

3. Ponownie spróbuj usunąć właściwość.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)