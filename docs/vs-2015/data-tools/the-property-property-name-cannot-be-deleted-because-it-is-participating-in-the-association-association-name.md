---
title: Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt; | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3ba746f9e4dcd8da45a002c5c763384558342ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053913"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wybrana właściwość jest ustawiona jako **właściwość skojarzenia** skojarzenia między klasami wskazanego w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są one skojarzenia między klasami danych.  
  
 Ustaw **właściwość skojarzenia** różne właściwości klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Wybierz linię skojarzenia na O/R Designer, który nawiązuje połączenie klas danych wskazany w komunikacie o błędzie.  
  
2. Kliknij dwukrotnie wiersz, aby otworzyć **Edytor skojarzeń** okno dialogowe.  
  
3. Usuń właściwość z **właściwości skojarzenia**.  
  
4. Ponownie spróbuj usunąć właściwość.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Instrukcje: Utwórz skojarzenie (Relacja) między LINQ to SQL klas (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
