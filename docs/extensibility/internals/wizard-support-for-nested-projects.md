---
title: Obsługa kreatora dla zagnieżdżonych projektów | Microsoft Docs
description: Dowiedz się więcej na temat dwóch kreatorów, które projekt nadrzędny może zaimplementować dla zagnieżdżonych projektów w pakietu VSPackage w zestawie SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b3c6dee712f79648eba203650cc70f76fcea657
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615619"
---
# <a name="wizard-support-for-nested-projects"></a>Obsługa kreatora dla zagnieżdżonych projektów
Środowisko IDE uruchamia dwa kreatory, które mogą implementować projekt nadrzędny dla zagnieżdżonych projektów: kreatora **nowego projektu** i kreatora **dodawania elementu** .

 Jeśli użytkownik uruchamia kreatora **nowego projektu** , wybierając pozycję **Dodaj projekt** i klikając pozycję **Nowy projekt** w menu plik lub wybierając pozycję **Dodaj** i klikając prawym przyciskiem myszy **Nowy projekt** w Eksplorator rozwiązań, IDE uruchamia polecenie **addproject** , a implementacja projektu nadrzędnego polecenia **addproject** zwraca plik projektu szablonu lub plik kreatora (. vsz), który zawiera zestaw parametrów kontekstu.

 Analogicznie, implementacja projektu nadrzędnego dla kreatorów **AddItem** zwraca plik. vsz, który ma inny zestaw parametrów kontekstu.

 Aby uzyskać więcej informacji na temat kreatorów, zobacz [Kreator (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [Parametry kontekstu](../../extensibility/internals/context-parameters.md) i [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
