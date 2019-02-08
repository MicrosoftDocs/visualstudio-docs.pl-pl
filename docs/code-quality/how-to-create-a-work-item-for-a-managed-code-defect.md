---
title: 'Instrukcje: Tworzenie elementu roboczego dla błędu kodu zarządzanego'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e2e55ddf51e0c81f57c504e398c23c8e1d3f721a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934799"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Instrukcje: Tworzenie elementu roboczego dla błędu kodu zarządzanego

Można użyć funkcji śledzenia elementu roboczego do dziennika element roboczy z poziomu programu Visual Studio. Aby użyć tej funkcji, projekt musi być częścią projektu DevOps platformy Azure w [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Aby utworzyć element roboczy dla błędu kodu zarządzanego

1. W **analizy kodu** oknie Wybierz ostrzeżenie.

2. Wybierz **akcje**, następnie wybierz **Utwórz element pracy** i wybierz typ elementu roboczego do utworzenia.

     Nowy element roboczy jest tworzony w celu określenia informacje o usterkach.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Aby utworzyć element roboczy dla wielu defektów kodu zarządzanego

1. W **lista błędów**, wybierz wiele ostrzeżeń i kliknij prawym przyciskiem myszy ostrzeżenia.

2. Wskaż **Utwórz element pracy** i kliknij typ elementu roboczego do utworzenia.

     Pojedynczym elemencie roboczym jest tworzony dla wszystkich wybranych ostrzeżeń, należy określić informacje o usterkach.