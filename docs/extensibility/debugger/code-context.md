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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 685650e0e97c3f9851f051fdaa78f86252597ff8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930723"
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
