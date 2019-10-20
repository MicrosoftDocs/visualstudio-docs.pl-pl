---
title: Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: bfc4e0995a9abb88f73ff27186ed4e0d1dc81648
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649775"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy

Projektant przepływu pracy nie obsługuje następujących scenariuszy debugowania:

- Nie można kontynuować wykonywania po edycji kodu.

- Nie można kontynuować wykonywania z dowolnego miejsca w przepływie pracy (w dalszej kolejności).

- Nie można kontynuować wykonywania, dopóki nie zostanie osiągnięty kursor (Uruchom do kursora).

- Nie można użyć projektanta przepływu pracy do debugowania przepływów pracy utworzonych w kodzie bez użycia projektanta.

- Przepływy pracy utworzone we wcześniejszych wersjach programu Windows Workflow Foundation (WF) nie mogą być debugowane w programie .NET Framework 4 lub nowszym.

- Nie można definiować punktów przerwania dla linków między działaniami lub węzłami <xref:System.Activities.Statements.Flowchart>.

- Schowek nie jest dostępny podczas debugowania.

- Punkty przerwania nie są zachowywane, gdy działania są kopiowane lub wklejane.

- Nie można ustawić punktów przerwania przepływu pracy w oknie stosu wywołań.

- Podczas tworzenia punktów przerwania w projektancie, ustawienia **wiersza** i **znaku** w oknie dialogowym **nowy punkt przerwania** nie są używane.

- Okno punktu przerwania lub menu skrótów nie obsługują następujących kolumn lub opcji debugowania przepływu pracy:

  - Warunek

  - Liczba trafień

  - Po trafieniu

  - Funkcja

  - Dane

  - Proces

  - Przejdź do demontażu
