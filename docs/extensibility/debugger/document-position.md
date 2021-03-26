---
title: Położenie dokumentu | Microsoft Docs
description: Dowiedz się, w jaki sposób położenie dokumentu w debugowaniu w programie Visual Studio zapewnia abstrakcję pozycji w pliku źródłowym, jak znany IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097256"
---
# <a name="document-position"></a>Położenie dokumentu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowaniu *pozycja dokumentu*:

- Zapewnia abstrakcję pozycji w pliku źródłowym, jak znany jest IDE. W większości języków dzisiaj pozycja dokumentu może być uważana za pozycję w pliku źródłowym.

- Opisuje położenie w dokumencie źródłowym do aparatu debugowania.

- Jest zaimplementowany przez interfejs [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Zobacz też
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [Kontekst dokumentu](../../extensibility/debugger/document-context.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
- [Interfejsy dostawcy symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
