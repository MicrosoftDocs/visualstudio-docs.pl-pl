---
title: Kontekst kodu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739151"
---
# <a name="code-context"></a>Kontekst kodu
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania **kontekst kodu:**

- Zapewnia abstrakcję pozycji w kodzie, jak znany aparat debugowania (DE). W przypadku większości architektur w czasie wykonywania obecnie kontekst kodu można traktować jako adres w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, w których kod może nie być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany za pomocą innych środków.

- Opisuje bieżącą pozycję w strumieniu wykonywania programu, który debugujesz.

- Istnieje tylko wtedy, gdy program został zatrzymany w punkcie przerwania.

- Ma skojarzony kontekst dokumentu.

- Jest implementowany przez interfejs [IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Zobacz też
- [Kontekst dokumentu](../../extensibility/debugger/document-context.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
