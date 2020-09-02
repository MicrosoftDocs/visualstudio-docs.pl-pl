---
title: Kontekst kodu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739151"
---
# <a name="code-context"></a>Kontekst kodu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowaniu, **kontekst kodu**:

- Zapewnia abstrakcję pozycji w kodzie, która jest znana aparatowi debugowania (DE). W przypadku większości architektur w czasie wykonywania dzisiaj, kontekst kodu może być uważany za adres w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, gdzie kod nie może być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany przez inny sposób.

- Opisuje bieżącą pozycję w strumieniu wykonywania debugowanego programu.

- Występuje tylko wtedy, gdy program został zatrzymany w punkcie przerwania.

- Ma skojarzony kontekst dokumentu.

- Jest zaimplementowany przez interfejs [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Zobacz też
- [Kontekst dokumentu](../../extensibility/debugger/document-context.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
