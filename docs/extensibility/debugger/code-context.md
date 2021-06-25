---
title: Kontekst | Microsoft Docs
description: Dowiedz się więcej o kontekście kodu Visual Studio debugowania, który opisuje pozycję w kodzie, która istnieje, gdy program zatrzymał się w punkcie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e3bd252990e52f4ecaede0cc5026067b28434bc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905725"
---
# <a name="code-context"></a>Kontekst kodu
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania kontekst **kodu:**

- Udostępnia abstrakcję pozycji w kodzie znanym aparatowi debugowania (DE). W przypadku większości architektur w czasie rzeczywistym kontekst kodu można uważać za adres w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, w których kod może nie być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany przez inne sposoby.

- Opisuje bieżącą pozycję w strumieniu wykonywania debugego programu.

- Istnieje tylko wtedy, gdy program został zatrzymany w punkcie przerwania.

- Ma skojarzony kontekst dokumentu.

- Jest implementowany przez [interfejs IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Zobacz też
- [Kontekst dokumentu](../../extensibility/debugger/document-context.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
