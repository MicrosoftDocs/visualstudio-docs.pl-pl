---
title: Program węzły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fa7e0969c9d45ae07280a8648036bd07c000974
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774487"
---
# <a name="program-nodes"></a>Węzły programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **węzła programu**:  
  
- Jest uproszczone opis programu.  
  
- Można zidentyfikować wraz z procesu działa oraz można dołączyć zostać odłączony lub opisywania aparatu debugowania (DE), której został utworzony, jeśli istnieje.  
  
- Jest reprezentowany przez [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, zwykle tworzony przy DE lub port. Węzły programu są dodawane do portu przez wywołanie metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł programu zostanie dodany do portu, jest dodawany do procesu, zawierające program, który reprezentuje ten węzeł programu.  
  
  Później, po rozpoczęciu sesji debugowania, w zależności od implementacji pakietu debugowania węzły programu są używane do tworzenia odpowiednich programów. Gdy proces jest poddawany kwerendzie jego programów, te programy są wyliczane, jeden dla każdego węzła program.  
  
  Zanim program jest dołączony do, IDE wymaga uproszczone opis programu. Te informacje można uzyskać z poziomu węzła programu. Gdy program jest dołączony do, IDE musi wyświetlić bardziej szczegółowe informacje, takie jak lista wszystkie wątki uruchomione w programie. Te informacje są uzyskiwane z samego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

