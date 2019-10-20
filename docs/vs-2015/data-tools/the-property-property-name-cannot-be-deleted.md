---
title: Nie można usunąć właściwości &lt;property nazwy &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667242"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Nie można usunąć właściwości &lt;property nazwy &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można usunąć właściwości \<property >, ponieważ jest ona ustawiona jako właściwość rozróżniacza dla dziedziczenia między \<class nazw > i \<class >

 Wybrana właściwość jest ustawiana jako **właściwość rozróżniacza** dla dziedziczenia między klasami wskazanymi w komunikacie o błędzie. Nie można usunąć właściwości, jeśli uczestniczą w konfiguracji dziedziczenia między klasami danych.

 Ustaw **Właściwość dyskryminatora** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W Projektancie O/R wybierz linię dziedziczenia, która łączy klasy danych wskazane w komunikacie o błędzie.

2. Ustaw właściwość **dyskryminatora** na inną właściwość.

3. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Konfigurowanie dziedziczenia przy użyciu funkcji](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [dziedziczenia klasy danych projektanta o/r (Projektant o/r)](../data-tools/data-class-inheritance-o-r-designer.md) [: tworzenie klas LINQ to SQL przy użyciu dziedziczenia z jedną tabelą (Projektant o/r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
