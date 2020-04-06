---
title: Dostawcy portów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738301"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera *dostawca portu:*

- Jest zawarty przez serwer i zapewnia porty na żądanie do tego serwera.

- Można dodawać i usuwać porty z serwera zawierającego.

- Można wyliczyć wszystkie porty, które dostarczyła do serwera.

- Jest reprezentowany przez interfejs [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) który jest zarejestrowany w programie Visual Studio za pośrednictwem rejestru. Ten interfejs można uzyskać, dzwoniąc do [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zapewnia domyślnego dostawcę portu i port domyślny. Jeśli port niestandardowy musi zostać zaimplementowany, dostawca portu niestandardowego również musi zostać zaimplementowany w celu dostarczenia tych portów niestandardowych.

## <a name="see-also"></a>Zobacz też
- [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Porty](../../extensibility/debugger/ports.md)
- [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
