---
title: Port Suppliers | Microsoft Docs
description: W tym artykule opisano definicję i rolę dostawcy portu w architekturze debugera w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0526135f706a42c622617a069e501297570e3b49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899124"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera dostawca *portu:*

- Jest zawarty przez serwer i udostępnia porty na żądanie do tego serwera.

- Może dodawać i usuwać porty z serwera zawierającego.

- Może wyliczyć wszystkie porty dostarczone do serwera.

- Jest reprezentowany przez [interfejs IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) który jest zarejestrowany w Visual Studio za pośrednictwem rejestru. Ten interfejs można uzyskać, wywołując [getPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Udostępnia domyślnego dostawcę portów i port domyślny. Jeśli trzeba zaimplementować port niestandardowy, należy również zaimplementować niestandardowego dostawcę portów, aby dostarczyć te porty niestandardowe.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
