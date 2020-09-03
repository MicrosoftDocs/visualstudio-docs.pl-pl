---
title: '&lt;Nie można usunąć nazwy właściwości właściwości, &gt; ponieważ uczestniczy ona w &lt; nazwie skojarzenia skojarzenia &gt; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667273"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>&lt;Nie można usunąć nazwy właściwości właściwości, &gt; ponieważ uczestniczy ona w &lt; nazwie skojarzenia skojarzenia&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wybrana właściwość jest ustawiana jako **Właściwość skojarzenia** dla skojarzenia między klasami wskazanymi w komunikacie o błędzie. Właściwości nie mogą zostać usunięte, jeśli uczestniczą w skojarzeniu między klasami danych.

 Ustaw **Właściwość skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz linię skojarzenie w Projektancie O/R, który łączy klasy danych wskazane w komunikacie o błędzie.

2. Kliknij dwukrotnie wiersz, aby otworzyć okno dialogowe **Edytor skojarzeń** .

3. Usuń właściwość ze **właściwości skojarzenia**.

4. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz też
 [LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [: Tworzenie skojarzenia (relacji) między klasami LINQ to SQL (Projektant o/r)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [: tworzenie klas LINQ to SQL (projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
