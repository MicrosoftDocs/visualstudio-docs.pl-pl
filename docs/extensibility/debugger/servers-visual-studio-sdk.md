---
title: Serwery (Visual Studio SDK) | Microsoft Docs
description: W tym artykule opisano definicje i rolę serwera w architekturze debugera w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9eaccebf874fa5fc0e7aaf63823547742215a568
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845300"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwer* programu:

- Jest kontenerem portów i dostawców portów, który komunikuje porty i dostawcy portów z menedżerem debugowania sesji (SDM) i aparatami debugowania.

- Może identyfikować siebie według nazwy i wyliczać jej porty i dostawców portów.

- Jest reprezentowany przez interfejs [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , który jest implementowany tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia programu Visual Studio uruchomionego).

## <a name="see-also"></a>Zobacz także
- [Porty](../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
