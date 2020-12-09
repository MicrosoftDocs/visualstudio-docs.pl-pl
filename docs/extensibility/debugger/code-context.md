---
title: Kontekst kodu | Microsoft Docs
description: Dowiedz się więcej o kontekście kodu w debugowaniu programu Visual Studio, który opisuje położenie w kodzie, który istnieje, gdy program został zatrzymany w punkcie przerwania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 60eabaca8d39d40649e20e022b25ce1b02bd8faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914312"
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
