---
title: Właściwość &lt;nazwa właściwości&gt; nie można usunąć | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e91c47ef848eda51fe71c9dce09cd1ea4893a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152093"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Właściwość \<nazwa właściwości > nie można usunąć, ponieważ jest ona ustawiona jako właściwość rozróżniacza dziedziczenia między \<Nazwa klasy > i \<Nazwa klasy >  
  
 Wybrana właściwość jest ustawiona jako **właściwość rozróżniacza** dziedziczenia między klasami wskazanego w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są one Konfigurowanie dziedziczenia między klasami danych.  
  
 Ustaw **właściwość rozróżniacza** różne właściwości klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. W Projektancie obiektów relacyjnych wybierz linię dziedziczenia, który nawiązuje połączenie klas danych wskazany w komunikacie o błędzie.  
  
2. Ustaw **dyskryminatora** właściwości inną właściwość.  
  
3. Ponownie spróbuj usunąć właściwość.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Dziedziczenie klas danych (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Przewodnik: Tworzenie klas LINQ do SQL za pomocą dziedziczenia pojedynczej tabeli (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
