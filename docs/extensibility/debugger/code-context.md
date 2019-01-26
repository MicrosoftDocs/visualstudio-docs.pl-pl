---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 868fa51d24b0ae3206d55ae8364224dead69e7f7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003373"
---
# <a name="code-context"></a>Kontekst kodu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania **kontekst kodu**:  
  
-   Udostępnia abstrakcję pozycji w kodzie, ponieważ wiadomo, że aparat debugowania (DE). Dla większości architektury w czasie wykonywania, kontekst kodu można traktować jako adres w usłudze stream instrukcji programu. Nietradycyjnych języków, w którym kod nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane za pomocą innych środków.  
  
-   W tym artykule opisano bieżącą pozycję w strumieniu wykonywania programu, który debugujesz.  
  
-   Istnieje tylko wtedy, gdy programu zostało zatrzymane w punkcie przerwania.  
  
-   Nie ma skojarzonego kontekstu.  
  
-   Jest implementowana przez [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz także  
 [Kontekst dokumentu](../../extensibility/debugger/document-context.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)