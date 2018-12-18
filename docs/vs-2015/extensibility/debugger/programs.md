---
title: Programy | Dokumentacja firmy Microsoft
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
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a5779c9ba6c113349501efa0c8a4ebbfd137a3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771870"
---
# <a name="programs"></a>Programy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pod względem architektury debugera **program**:  
  
-   To kontener dla zestawu wątków i zestaw modułów. Program nie ma żadnych pojedynczego odpowiednio w systemie operacyjnym Windows.  
  
     Program jest rodzajem proces podrzędny. Na przykład podczas debugowania witryny sieci Web, skrypt może być traktowany jako program. Podczas uruchamiania skryptu w procesie aparatu obsługi skryptów, niezależnie od innych skryptów również ma swój własny zestaw wątków. Aparat debugowania (DE) dołącza do programu, a nie proces lub wątek.  
  
-   Można zidentyfikować wraz z procesu działa oraz można dołączyć zostać odłączony lub opisać DE, w której został utworzony, jeśli istnieje. Program można wykonać, Zatrzymaj, nadal i zostać zakończone.  
  
-   Można wyliczyć wszystkich wątków. Program można również podać własną strumienia dezasemblacji i można wyliczyć wszystkie konteksty kodu pozycji danego dokumentu.  
  
-   Jest reprezentowany przez [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsu, utworzonych przed program jest dołączona lub jako część procesu dołączania w zależności od implementacji. Gdy port wylicza programy procesu, każdy program zostanie utworzony zgodnie z odpowiednią [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu przekazywany jako argument do [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aparaty debugowania również tworzyć `IDebugProgram2` interfejsy do reprezentowania programy, te programy nie są tworzone zgodnie z węzła programu. `IDebugProgramNode2` Interfejsów utworzone przez DE służą do debugowania rzeczywiste utworzone przez port są używane tylko w przypadku odnajdywania, które programy działają w ramach procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procesy](../../extensibility/debugger/processes.md)   
 [Węzły programu](../../extensibility/debugger/program-nodes.md)   
 [Moduły](../../extensibility/debugger/modules.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

