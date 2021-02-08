---
title: Położenie dokumentu | Microsoft Docs
description: Dowiedz się, w jaki sposób położenie dokumentu w debugowaniu w programie Visual Studio zapewnia abstrakcję pozycji w pliku źródłowym, jak znany IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840720"
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
