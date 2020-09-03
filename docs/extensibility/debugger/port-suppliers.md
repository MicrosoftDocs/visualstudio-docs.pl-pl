---
title: Dostawcy portów | Microsoft Docs
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
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738301"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera *dostawca portu*:

- Jest zawarty na serwerze i udostępnia porty na żądanie do tego serwera.

- Może dodawać i usuwać porty z serwera zawierającego.

- Program może wyliczyć wszystkie porty dostarczone do serwera.

- Jest reprezentowany przez interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać, wywołując [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia domyślnego dostawcę portu i domyślny port. Jeśli należy zaimplementować port niestandardowy, należy również zaimplementować niestandardowego dostawcę portu w celu dostarczenia tych portów niestandardowych.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
