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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7bb19262d4ce5fd1b3139f05cd9bbc57131db1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070365"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
W architekturze debugera *serwer* programu:

- Jest kontenerem portów i dostawców portów, który komunikuje porty i dostawcy portów z menedżerem debugowania sesji (SDM) i aparatami debugowania.

- Może identyfikować siebie według nazwy i wyliczać jej porty i dostawców portów.

- Jest reprezentowany przez interfejs [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , który jest implementowany tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia programu Visual Studio uruchomionego).

## <a name="see-also"></a>Zobacz też
- [Porty](../../extensibility/debugger/ports.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
