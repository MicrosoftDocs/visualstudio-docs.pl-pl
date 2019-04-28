---
title: Kontekst dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a60b95faf9c22ccec45dc560031bf517f53028b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889775"
---
# <a name="document-context"></a>Kontekst dokumentu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania *kontekstu dokumentu*:

- Reprezentuje pozycji w pliku źródłowym. W przypadku języków, gdzie plik źródłowy nie może być obecny kontekstu dokumentu identyfikuje pozycji w dokumencie, zwykle generowane przez środowisko wykonawcze. Na przykład aparat skryptów może generować dokumentu ze skryptu. Aby uzyskać więcej informacji, zobacz [pozycji dokumentu](../../extensibility/debugger/document-position.md).

- W tym artykule opisano pozycji w dokumencie źródłowym, który odnosi się do kontekstu kodu. Procedury obsługi symboli mapuje kontekst kodu kontekst dokumentację, korzystając z informacji generowanych przez kompilator lub interpretera.

- Jest implementowana przez [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.

## <a name="see-also"></a>Zobacz także
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
- [Interfejsy dostawca symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)