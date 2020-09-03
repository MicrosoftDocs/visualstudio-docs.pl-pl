---
title: Kontekst dokumentu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738920"
---
# <a name="document-context"></a>Kontekst dokumentu
W obszarze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie, *kontekst dokumentu*:

- Reprezentuje pozycję w pliku źródłowym. W przypadku języków, w których plik źródłowy może nie być obecny, kontekst dokumentu identyfikuje pozycję w dokumencie zwykle generowanym przez środowisko uruchomieniowe. Na przykład aparat skryptów może generować dokument ze skryptu. Aby uzyskać więcej informacji, zobacz [pozycja dokumentu](../../extensibility/debugger/document-position.md).

- Opisuje pozycję w dokumencie źródłowym, która odnosi się do kontekstu kodu. Procedura obsługi symboli mapuje kontekst kodu do kontekstu dokumentacji przy użyciu informacji generowanych przez kompilator lub interpreter.

- Jest zaimplementowany przez interfejs [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Zobacz też
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
- [Interfejsy dostawcy symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
