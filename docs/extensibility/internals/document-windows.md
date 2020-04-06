---
title: Dokument Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708516"
---
# <a name="document-windows"></a>Okna dokumentów
W programie Visual Studio *okno dokumentu* jest okno podrzędne w ramce, które jest skojarzone z oknem interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do wyświetlania i modyfikowania kodu źródłowego lub tekstu, ale mogą również obsługiwać inne typy funkcjonalne. Okna dokumentów:

- Można organizować w oddzielnych poziomych lub pionowych grupach kart w nadrzędnym mdi, tak aby można było wyświetlać wiele plików w tym samym czasie.

- Może być zadokowany w dowolnej kolejności w nadrzędnym MDI.

- Może być swobodnie pływał.

- Są połączone w zakładce, aby inne okna MDI.

  Polecenia grupowania, dokowania i przestawne można znaleźć w menu skrótów karty okna dokumentu.

  Aby uzyskać więcej informacji na temat zachowania okien w programie Visual Studio, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementacja okna dokumentu
 Okna dokumentów są tworzone przez implementowanie edytora. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> tworzy okna dokumentu w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [Starsze interfejsy w edytorze](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Aby zapewnić wsteczne i do przodu punkty <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> nawigacyjne w oknie, zaimplementuj interfejs. Edytor tekstu używa znaczników tekstowych do identyfikowania punktów nawigacyjnych w dokumencie.

## <a name="the-running-document-table"></a>Tabela Uruchomiony dokument
 IDE używa uruchomionej tabeli dokumentów (RDT) do śledzenia stanu każdego okna dokumentu. RDT jest mechanizm, za pomocą którego okna dokumentu są powiadamiane o zdarzeniach, takich jak gdy rozwiązanie jest zamknięty lub gdy plik został edytowany. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Zobacz też
- [Opóźnione ładowanie dokumentów](../../extensibility/internals/delayed-document-loading.md)
