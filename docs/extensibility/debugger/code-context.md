---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbbeb9eab33bbdad7264a0296a4f6c9f86fb8a5d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851290"
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