---
title: '&lt; &gt; Nie można usunąć nazwy właściwości właściwości | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667242"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>&lt;Nie można usunąć nazwy właściwości właściwości. &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

\<property name>Nie można usunąć właściwości, ponieważ jest ona ustawiona jako właściwość rozróżniacza dla dziedziczenia między \<class name> i\<class name>

 Wybrana właściwość jest ustawiana jako **właściwość rozróżniacza** dla dziedziczenia między klasami wskazanymi w komunikacie o błędzie. Nie można usunąć właściwości, jeśli uczestniczą w konfiguracji dziedziczenia między klasami danych.

 Ustaw **Właściwość dyskryminatora** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W Projektancie O/R wybierz linię dziedziczenia, która łączy klasy danych wskazane w komunikacie o błędzie.

2. Ustaw właściwość **dyskryminatora** na inną właściwość.

3. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Konfigurowanie dziedziczenia przy użyciu funkcji](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [dziedziczenia klasy danych projektanta o/r (Projektant o/r)](../data-tools/data-class-inheritance-o-r-designer.md) [: tworzenie klas LINQ to SQL przy użyciu dziedziczenia z jedną tabelą (Projektant o/r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
