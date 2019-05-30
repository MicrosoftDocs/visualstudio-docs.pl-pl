---
title: Obsługa kreatora dla zagnieżdżonych projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa1dedebab95e1c1b74e1705f3a8b39a1ebe3616
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312928"
---
# <a name="wizard-support-for-nested-projects"></a>Obsługa kreatora dla zagnieżdżonych projektów
Środowisko IDE jest uruchamiane dwa kreatory, które można wdrożyć projektu nadrzędnego dla zagnieżdżonych projektów: **nowy projekt** kreatora i **elementu Dodawanie** kreatora.

 Jeśli użytkownik uruchamia **nowy projekt** kreatora, wybierając **Dodaj projekt** i klikając **nowy projekt** menu Plik, lub wybierając **Dodaj** i kliknij prawym przyciskiem myszy **nowy projekt** w Eksploratorze rozwiązań, uruchamia IDE **AddProject** polecenia i wdrażania projektu nadrzędnego **AddProject**polecenie to zwraca plik szablonu projektu lub pliku kreatora (.vsz —), który zawiera zestaw parametrów kontekstu.

 Podobnie, projektu nadrzędnego implementacji **AddItem** kreatorów zwraca plik .vsz, który ma inny zestaw parametrów kontekstu.

 Aby uzyskać więcej informacji na temat kreatorów, zobacz [kreatora (. Plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parametrów kontekstu](../../extensibility/internals/context-parameters.md) i [rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)