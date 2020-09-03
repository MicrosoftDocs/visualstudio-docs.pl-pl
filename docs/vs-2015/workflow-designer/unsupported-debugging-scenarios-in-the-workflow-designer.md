---
title: Nieobsługiwane scenariusze debugowania w Projektant przepływu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdbe68b416560b85580e3dd30e5f8138b7cd08fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606936"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy
Projektant przepływu pracy w programie [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] dodał wiele nowych funkcji, ale nadal istnieją scenariusze debugowania, które nie są obsługiwane przez program. Szczegóły tego dokumentu nie są obsługiwane w scenariuszach debugowania Projektant przepływu pracy.

- Nie można kontynuować wykonywania po edycji kodu.

- Nie można kontynuować wykonywania z dowolnego miejsca w przepływie pracy (w dalszej kolejności).

- Nie można kontynuować wykonywania, dopóki nie zostanie osiągnięty kursor (Uruchom do kursora).

- Nie można użyć projektanta przepływu pracy do debugowania przepływów pracy utworzonych w kodzie bez użycia projektanta.

- Przepływy pracy utworzone we wcześniejszych wersjach programu [!INCLUDE[wf](../includes/wf-md.md)] nie mogą być debugowane w [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] projektancie.

- Nie można definiować punktów przerwania dla linków między działaniami lub <xref:System.Activities.Statements.Flowchart> węzłami.

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
