---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11554be1411e63c97c8afde7cc3a819486e862ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351328"
---
# <a name="code-context"></a>Kontekst kodu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania **kontekst kodu**:

- Udostępnia abstrakcję pozycji w kodzie, ponieważ wiadomo, że aparat debugowania (DE). Dla większości architektury w czasie wykonywania, kontekst kodu można traktować jako adres w usłudze stream instrukcji programu. Nietradycyjnych języków, w którym kod nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane za pomocą innych środków.

- W tym artykule opisano bieżącą pozycję w strumieniu wykonywania programu, który debugujesz.

- Istnieje tylko wtedy, gdy programu zostało zatrzymane w punkcie przerwania.

- Nie ma skojarzonego kontekstu.

- Jest implementowana przez [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu.

## <a name="see-also"></a>Zobacz także
- [Kontekst dokumentu](../../extensibility/debugger/document-context.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)