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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915326"
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
