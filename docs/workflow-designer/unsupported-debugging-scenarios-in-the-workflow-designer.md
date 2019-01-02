---
title: Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88fa196d5df085249282e595031bbde09ba071a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858633"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy

Projektant przepływu pracy w programie .NET Framework 4 dodano wiele nowych funkcji, ale nadal istnieją pewne scenariusze debugowania, które nie obsługują.

Nieobsługiwany projektanta przepływu pracy debugowania scenariusze są następujące:

-   Wykonywanie nie mogą być kontynuowane po kod został zmodyfikowany.

-   Wykonywanie nie mogą być kontynuowane z dowolnego punktu w przepływie pracy (Ustaw dalej).

-   Wykonanie nie może być kontynuowane, aż do osiągnięcia kursora (Uruchom do kursora).

-   Projektanta przepływu pracy nie może służyć do debugowania utworzonych w kodzie bez korzystania z projektanta przepływów pracy.

-   Przepływy pracy utworzone we wcześniejszych wersjach programu Windows Workflow Foundation (WF) nie można debugować w programie .NET Framework 4 designer.

-   Punkty przerwania nie może być zdefiniowana w łączach między działaniami lub <xref:System.Activities.Statements.Flowchart> węzłów.

-   Schowek nie jest dostępne podczas debugowania.

-   Punkty przerwania nie są zachowywane podczas działania są kopiowane lub wklejone.

-   Nie można ustawić punktów przerwania przepływu pracy w oknie stosu wywołań.

-   Podczas tworzenia punktów przerwania w Projektancie **wiersza** i **znak** ustawienia w **nowego punktu przerwania** okna dialogowego nie są używane.

-   Menu okna lub skrót punkt przerwania nie obsługuje następujących kolumn lub opcji dla debugowanie przepływu pracy:

    -   Warunek

    -   Liczba trafień

    -   Gdy trafiony

    -   Funkcja

    -   Dane

    -   Proces

    -   Przejdź do demontażu