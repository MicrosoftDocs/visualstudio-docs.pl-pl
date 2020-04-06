---
title: Kontekst dokumentu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738920"
---
# <a name="document-context"></a>Kontekst dokumentu
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania *kontekst dokumentu:*

- Reprezentuje pozycję w pliku źródłowym. W przypadku języków, w których plik źródłowy może nie być obecny, kontekst dokumentu identyfikuje pozycję w dokumencie zwykle generowanym przez środowisko w czasie wykonywania. Na przykład aparat skryptów może wygenerować dokument ze skryptu. Aby uzyskać więcej informacji, zobacz [Pozycja dokumentu](../../extensibility/debugger/document-position.md).

- Opisuje położenie w dokumencie źródłowym, który odpowiada kontekstu kodu. Program obsługi symboli mapuje kontekst kodu do kontekstu dokumentacji przy użyciu informacji generowanych przez kompilator lub interpreter.

- Jest implementowany przez interfejs [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Zobacz też
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
- [Interfejsy dostawcy symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
