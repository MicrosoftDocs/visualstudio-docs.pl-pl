---
title: Dokument systemu Windows | Microsoft Docs
description: Dowiedz się więcej o oknach dokumentów w Visual Studio, w tym o tym, jak je zaimplementować i jak funkcja Uruchamiania tabeli dokumentów (RDT) śledzi ich stan.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df7a797c0b4587698197412f49eef6bfab183a7a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899917"
---
# <a name="document-windows"></a>Okna dokumentów
W Visual Studio *dokument* jest oknem podrzędnym w ramce skojarzonym z oknem interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do wyświetlania i modyfikowania kodu źródłowego lub tekstu, ale mogą również hostować inne typy funkcjonalne. Okna dokumentów:

- Można je uporządkować w oddzielnych poziomych lub pionowych grupach kart w nadrzędnym mdi, dzięki czemu można wyświetlać wiele plików w tym samym czasie.

- Można zadokować w dowolnej kolejności w nadrzędnym mdi.

- Może być zmiennoprzecinkowa.

- Są połączone w kolejności tabuły z innymi oknami MDI.

  Polecenia grupowania, dokowania i zmiennoprzecinkowego można znaleźć w menu skrótów karty okna dokumentu.

  Aby uzyskać więcej informacji na temat zachowania okna w Visual Studio, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementacja okna dokumentu
 Okna dokumentów są tworzone przez zaimplementowanie edytora. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> tworzy okna dokumentów w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [Starsze interfejsy w edytorze](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Aby zapewnić punkty nawigacji wstecz i do przodu w oknie, zaim implementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfejs. Edytor tekstu używa znaczników tekstu do identyfikowania punktów nawigacji w dokumencie.

## <a name="the-running-document-table"></a>Tabela Running document (Uruchamianie dokumentu)
 Do śledzenia stanu każdego okna dokumentu w idee jest używana tabela Uruchamianie dokumentu (RDT). RDT to mechanizm, za pomocą którego okna dokumentów są powiadamiane o zdarzeniach, takich jak zamknięcie rozwiązania lub edycja pliku. Aby uzyskać więcej informacji, zobacz [Running document table (Uruchamianie tabeli dokumentów).](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>Zobacz też
- [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)
