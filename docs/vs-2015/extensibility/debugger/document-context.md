---
title: Kontekst dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080036"
---
# <a name="document-context"></a>Kontekst dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania **kontekstu dokumentu**:  
  
- Reprezentuje pozycji w pliku źródłowym. W przypadku języków, gdzie plik źródłowy nie może być obecny kontekstu dokumentu identyfikuje pozycji w dokumencie, zwykle generowane przez środowisko wykonawcze. Na przykład aparat skryptów może generować dokumentu ze skryptu. Aby uzyskać więcej informacji, zobacz [położenie dokumentu](../../extensibility/debugger/document-position.md).  
  
- W tym artykule opisano pozycji w dokumencie źródłowym, który odnosi się do kontekstu kodu. Procedury obsługi symboli mapuje kontekst kodu kontekst dokumentację, korzystając z informacji generowanych przez kompilator lub interpretera.  
  
- Jest implementowana przez [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfejsy dostawca symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
