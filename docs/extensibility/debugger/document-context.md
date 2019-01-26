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
ms.openlocfilehash: 0ad3996877ee3ba0f16972fbd5cf10cb539ac975
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993809"
---
# <a name="document-context"></a>Kontekst dokumentu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania *kontekstu dokumentu*:  
  
-   Reprezentuje pozycji w pliku źródłowym. W przypadku języków, gdzie plik źródłowy nie może być obecny kontekstu dokumentu identyfikuje pozycji w dokumencie, zwykle generowane przez środowisko wykonawcze. Na przykład aparat skryptów może generować dokumentu ze skryptu. Aby uzyskać więcej informacji, zobacz [pozycji dokumentu](../../extensibility/debugger/document-position.md).  
  
-   W tym artykule opisano pozycji w dokumencie źródłowym, który odnosi się do kontekstu kodu. Procedury obsługi symboli mapuje kontekst kodu kontekst dokumentację, korzystając z informacji generowanych przez kompilator lub interpretera.  
  
-   Jest implementowana przez [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz także  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfejsy dostawca symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)