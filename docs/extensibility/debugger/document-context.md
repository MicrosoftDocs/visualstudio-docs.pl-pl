---
title: Kontekst dokumentu | Microsoft Docs
description: Dowiedz się więcej o kontekście dokumentu Visual Studio debugowaniu, który reprezentuje pozycję w pliku źródłowym lub pozycję w dokumencie źródłowym dla kontekstu kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898191"
---
# <a name="document-context"></a>Kontekst dokumentu
Podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania kontekst *dokumentu:*

- Reprezentuje pozycję w pliku źródłowym. W przypadku języków, w których plik źródłowy może nie być obecny, kontekst dokumentu identyfikuje pozycję w dokumencie zwykle wygenerowaną przez środowisko uruchomieniowe. Na przykład aparat skryptów może wygenerować dokument na podstawie skryptu. Aby uzyskać więcej informacji, zobacz [Położenie dokumentu](../../extensibility/debugger/document-position.md).

- Opisuje pozycję w dokumencie źródłowym, która odpowiada kontekstowi kodu. Procedura obsługi symboli mapuje kontekst kodu na kontekst dokumentacji przy użyciu informacji generowanych przez kompilator lub interpreter.

- Jest implementowany przez [interfejs IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Zobacz też
- [Kontekst kodu](../../extensibility/debugger/code-context.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
- [Interfejsy dostawcy symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)
