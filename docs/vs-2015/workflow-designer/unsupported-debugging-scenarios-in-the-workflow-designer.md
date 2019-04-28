---
title: Nieobsługiwane scenariusze w Projektancie przepływu pracy debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7b3b47264190afcc75431a55ad6b8b4512f26ea0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62858176"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy
Projektant przepływu pracy w [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] dodano wiele nowych funkcji, ale nadal istnieje kilka scenariuszy debugowania, które nie obsługuje. Ten dokument wyszczególnia nieobsługiwany projektanta przepływu pracy debugowania scenariuszy.  
  
- Wykonywanie nie mogą być kontynuowane po kod został zmodyfikowany.  
  
- Wykonywanie nie mogą być kontynuowane z dowolnego punktu w przepływie pracy (Ustaw dalej).  
  
- Wykonanie nie może być kontynuowane, aż do osiągnięcia kursora (Uruchom do kursora).  
  
- Projektanta przepływu pracy nie może służyć do debugowania utworzonych w kodzie bez korzystania z projektanta przepływów pracy.  
  
- Przepływy pracy utworzone we wcześniejszych wersjach programu [!INCLUDE[wf](../includes/wf-md.md)] nie można debugować w [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] projektanta.  
  
- Punkty przerwania nie może być zdefiniowana w łączach między działaniami lub <xref:System.Activities.Statements.Flowchart> węzłów.  
  
- Schowek nie jest dostępne podczas debugowania.  
  
- Punkty przerwania nie są zachowywane podczas działania są kopiowane lub wklejone.  
  
- Nie można ustawić punktów przerwania przepływu pracy w oknie stosu wywołań.  
  
- Podczas tworzenia punktów przerwania w Projektancie **wiersza** i **znak** ustawienia w **nowego punktu przerwania** okna dialogowego nie są używane.  
  
- Menu okna lub skrót punkt przerwania nie obsługuje następujących kolumn lub opcji dla debugowanie przepływu pracy:  
  
    - Warunek  
  
    - Liczba trafień  
  
    - Gdy trafiony  
  
    - Funkcja  
  
    - Dane  
  
    - Proces  
  
    - Przejdź do demontażu