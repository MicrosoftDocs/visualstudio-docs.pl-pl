---
title: Obsługa kreatora dla zagnieżdżonych projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 206fd12ea8f198e1659a49ed566e726e49878c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180342"
---
# <a name="wizard-support-for-nested-projects"></a>Obsługa kreatora dla zagnieżdżonych projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Środowisko IDE uruchamia dwa kreatory, które mogą implementować projekt nadrzędny dla zagnieżdżonych projektów: kreatora **nowego projektu** i kreatora **dodawania elementu** .  
  
 Jeśli użytkownik uruchamia kreatora **nowego projektu** , wybierając pozycję **Dodaj projekt** i klikając pozycję **Nowy projekt** w menu plik lub wybierając pozycję **Dodaj** i klikając prawym przyciskiem myszy **Nowy projekt** w Eksplorator rozwiązań, IDE uruchamia polecenie **addproject** , a implementacja projektu nadrzędnego polecenia **addproject** zwraca plik projektu szablonu lub plik kreatora (. vsz), który zawiera zestaw parametrów kontekstu.  
  
 Analogicznie, implementacja projektu nadrzędnego dla kreatorów **AddItem** zwraca plik. vsz, który ma inny zestaw parametrów kontekstu.  
  
 Aby uzyskać więcej informacji na temat kreatorów, zobacz [Kreator (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [Parametry kontekstu](../../extensibility/internals/context-parameters.md) i [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
