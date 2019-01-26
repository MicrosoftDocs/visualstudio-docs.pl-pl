---
title: 'Instrukcje: Tworzenie elementu roboczego dla błędu kodu zarządzanego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1cb63612194148b5f3ea1f90d7c57e59fb84edbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941830"
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