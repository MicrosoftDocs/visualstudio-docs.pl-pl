---
title: Węzły programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153658"
---
# <a name="program-nodes"></a>Węzły programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W odniesieniu do architektury debugera, **węzeł programu**:  
  
- Jest lekkim opisem programu.  
  
- Może identyfikować siebie i proces, w którym jest uruchomiona, i może zostać dołączony do, zostać odłączony od i opisywany aparat debugowania (DE), który go utworzył (jeśli istnieje).  
  
- Jest reprezentowany przez interfejs [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , zwykle tworzony przez de lub port. Węzły programu są dodawane do portu przez wywołanie [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł programu zostanie dodany do portu, zostanie dodany do procesu zawierającego program, który reprezentuje ten węzeł programu.  
  
  Czasami po rozpoczęciu sesji debugowania, w zależności od implementacji pakietu debugowania, węzły programu są używane do tworzenia odpowiednich programów. Po wykonaniu zapytania dotyczącego jego programów wyliczane są programy, po jednej dla każdego węzła programu.  
  
  Przed dołączeniem programu do środowiska IDE wymaga tylko lekkiego opisu programu. Te informacje można uzyskać z węzła program. Po dołączeniu programu do środowiska IDE musi wyświetlić bardziej szczegółowe informacje, takie jak lista wszystkich wątków uruchomionych w programie. Te informacje są uzyskiwane z samego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programu](../../extensibility/debugger/programs.md)   
 [Przetwarzające](../../extensibility/debugger/processes.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
