---
title: Obsługa kreatora dla projektów zagnieżdżonych | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703194"
---
# <a name="wizard-support-for-nested-projects"></a>Obsługa kreatora dla zagnieżdżonych projektów
IDE uruchamia dwa kreatory, które projekt nadrzędny dla projektów zagnieżdżonych można zaimplementować: Kreator **nowego projektu** i Kreator **dodaj element.**

 Jeśli użytkownik uruchamia **Kreatora nowego projektu,** wybierając pozycję **Dodaj projekt** i klikając **polecenie Nowy projekt** w menu Plik lub wybierając polecenie **Dodaj** i kliknij prawym przyciskiem myszy **nowy projekt** w Eksploratorze rozwiązań, IDE uruchamia polecenie **AddProject,** a implementacja polecenia **AddProject** projektu przez projekt nadrzędny zwraca plik projektu szablonu lub plik kreatora (.vsz), który ma zestaw parametrów kontekstowych.

 Podobnie implementacja kreatorów **AddItem** projektu nadrzędnego zwraca plik .vsz, który ma inny zestaw parametrów kontekstu.

 Aby uzyskać więcej informacji o kreatorach, zobacz [Kreator (. Vsz) Plik](../../extensibility/internals/wizard-dot-vsz-file.md), [Parametry kontekstowe](../../extensibility/internals/context-parameters.md) i [rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
