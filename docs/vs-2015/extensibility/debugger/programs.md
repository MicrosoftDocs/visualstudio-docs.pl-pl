---
title: Programy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153642"
---
# <a name="programs"></a>Programy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W odniesieniu do architektury debugera **program**:  
  
- Jest kontenerem dla zestawu wątków i zestawu modułów. Program nie ma pojedynczej analogu w systemie operacyjnym Windows.  
  
     Program jest rodzajem podprocesu. Na przykład podczas debugowania witryny sieci Web skrypt może być traktowany jako program. Skrypt jest uruchamiany w procesie aparatu skryptów, niezależnie od innych skryptów, również ma swój własny zestaw wątków. Aparat debugowania (DE) dołącza do programu, a nie do procesu lub wątku.  
  
- Może identyfikować siebie i proces, w którym jest uruchomiona, i może zostać dołączony do, zostać odłączony od i opisujący DE, który go utworzył. Program może wykonać, zatrzymać, kontynuować i zostać zakończony.  
  
- Może wyliczyć wszystkie jej wątki. Program może również dostarczyć swój własny strumień demontażu i może wyliczyć wszystkie konteksty kodu danego położenia dokumentu.  
  
- Jest reprezentowany przez interfejs [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , utworzony przed dołączeniem programu lub jako część procesu dołączania, w zależności od implementacji. Gdy port wylicza programy, każdy program jest tworzony zgodnie z odpowiednim interfejsem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) przekazaną jako argument do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Chociaż aparaty debugowania również tworzą `IDebugProgram2` interfejsy do reprezentowania programów, te programy nie są tworzone zgodnie z węzłem programu. `IDebugProgramNode2`Interfejsy utworzone przez de są używane do rzeczywistego debugowania, podczas gdy te utworzone przez port są używane tylko do odnajdywania programów uruchomionych w procesie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzające](../../extensibility/debugger/processes.md)   
 [Węzły programu](../../extensibility/debugger/program-nodes.md)   
 [Moduły](../../extensibility/debugger/modules.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
