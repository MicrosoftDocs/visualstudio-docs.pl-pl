---
title: Okna dokumentów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d29d64090320a8f62491209773145c024564efa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186629"
---
# <a name="document-windows"></a>Okna dokumentów
W programie Visual Studio *okno dokumentu* jest oknem podrzędnym z ramkami, które jest skojarzone z oknem interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do wyświetlania i modyfikacji kodu źródłowego lub tekstu, ale mogą również hostować inne typy funkcjonalne. Okna dokumentów:

- Może być zorganizowany w oddzielnych lub pionowych grupach kart w nadrzędnym pliku MDI, aby można było przeglądać wiele plików jednocześnie.

- Można zadokować w dowolnej kolejności w nadrzędnym MDI.

- Mogą być swobodne.

- Są połączone w kolejności tabulacji z innymi oknami MDI.

  Polecenia służące do grupowania, dokowania i zmiennoprzecinkowej można znaleźć w menu skrótów dla karty okna dokumentu.

  Aby uzyskać więcej informacji na temat zachowania okna w programie Visual Studio, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementacja okna dokumentu
 Okna dokumentów są tworzone przez implementację edytora. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> tworzy okna dokumentów w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [starsze interfejsy w edytorze](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Aby zapewnić punkty nawigacji do tyłu i do przodu w oknie, zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>. Edytor tekstu używa znaczników tekstowych do identyfikowania punktów nawigacji w dokumencie.

## <a name="the-running-document-table"></a>Uruchomiona tabela dokumentów
 IDE korzysta z uruchomionej tabeli dokumentu (RDT) w celu śledzenia stanu każdego okna dokumentu. RDT jest mechanizmem, za pomocą którego okna dokumentów są powiadamiane o zdarzeniach, na przykład po zamknięciu rozwiązania lub edytowaniu pliku. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Zobacz także
- [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)