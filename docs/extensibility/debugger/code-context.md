---
title: Kontekst kodu | Microsoft Docs
description: Dowiedz się więcej o kontekście kodu w debugowaniu programu Visual Studio, który opisuje położenie w kodzie, który istnieje, gdy program został zatrzymany w punkcie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c668cd1fa80efe24fa596cc4e9f311e2db519246
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055040"
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
