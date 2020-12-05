---
title: Dostawcy portów | Microsoft Docs
description: W tym artykule opisano definicje i rolę dostawcy portów w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3226053a23a45c42a45de038e44829d4a150af6
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606583"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera *dostawca portu*:

- Jest zawarty na serwerze i udostępnia porty na żądanie do tego serwera.

- Może dodawać i usuwać porty z serwera zawierającego.

- Program może wyliczyć wszystkie porty dostarczone do serwera.

- Jest reprezentowany przez interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać, wywołując [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia domyślnego dostawcę portu i domyślny port. Jeśli należy zaimplementować port niestandardowy, należy również zaimplementować niestandardowego dostawcę portu w celu dostarczenia tych portów niestandardowych.

## <a name="see-also"></a>Zobacz także
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
