---
title: Kontekst kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197373"
---
# <a name="code-context"></a>Kontekst kodu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowaniu, **kontekst kodu**:  
  
- Zapewnia abstrakcję pozycji w kodzie, która jest znana aparatowi debugowania (DE). W przypadku większości architektur w czasie wykonywania dzisiaj, kontekst kodu może być uważany za adres w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, gdzie kod nie może być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany przez inny sposób.  
  
- Opisuje bieżącą pozycję w strumieniu wykonywania debugowanego programu.  
  
- Występuje tylko wtedy, gdy program został zatrzymany w punkcie przerwania.  
  
- Ma skojarzony kontekst dokumentu.  
  
- Jest zaimplementowany przez interfejs [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst dokumentu](../../extensibility/debugger/document-context.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
