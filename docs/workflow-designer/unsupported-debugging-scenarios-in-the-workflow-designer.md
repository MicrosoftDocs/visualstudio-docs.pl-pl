---
title: Nieobsługiwane scenariusze debugowania
description: Dowiedz się więcej na temat nieobsługiwanych scenariuszy debugowania w Projektant przepływu pracy, na przykład "nie można kontynuować wykonywania po edycji kodu".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 4e98e2a75905f4c0a4c007691a99961dbcf1477c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996269"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływu pracy

Projektant przepływu pracy nie obsługuje następujących scenariuszy debugowania:

- Nie można kontynuować wykonywania po edycji kodu.

- Nie można kontynuować wykonywania z dowolnego miejsca w przepływie pracy (w dalszej kolejności).

- Nie można kontynuować wykonywania, dopóki nie zostanie osiągnięty kursor (Uruchom do kursora).

- Nie można użyć projektanta przepływu pracy do debugowania przepływów pracy utworzonych w kodzie bez użycia projektanta.

- Przepływy pracy utworzone we wcześniejszych wersjach programu Windows Workflow Foundation (WF) nie mogą być debugowane w programie .NET Framework 4 lub nowszym.

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
