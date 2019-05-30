---
title: Menu kontekstowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5534d0895e35e252364b491858a694a1f5b726a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341736"
---
# <a name="context-menus"></a>Menu kontekstowe
Menu kontekstowe są wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy aktywny region obszaru klienta i usuń zaznaczenie po zwolnieniu prawego przycisku myszy.

## <a name="editor-context-menus"></a>Menu kontekstowe edytora
 Przechwycenie `ECMD_SHOWCONTEXTMENU`, usługi w języka można kontrolować menu kontekstowe, które będą wyświetlane w edytorze. Aby wyświetlić menu kontekstowe, obsługi tego polecenia, gdy jest przekazywany do usługi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Jeśli nie obsługuje tego polecenia, IDE Wyświetla standardowe menu kontekstowe podane dla edytora. Można także kontrolować zawartość elementu menu kontekstowego na podstawie poszczególnych znacznika. Aby uzyskać więcej informacji na ten temat, zobacz [znaczników tekstu za pomocą starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md) i [Przechwytywanie poleceń usługi starszego języka](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)
- [Rozszerzenie menu i poleceń](../extensibility/extending-menus-and-commands.md)