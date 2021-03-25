---
title: Okna dokumentów | Microsoft Docs
description: Dowiedz się więcej o oknach dokumentów w programie Visual Studio, w tym o sposobach ich implementacji oraz sposobie śledzenia statusu uruchomionej tabeli dokumentu (RDT).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79706c98e98be55e69aaeeed7320c8b13bfd2a9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061280"
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
 Okna dokumentów są tworzone przez implementację edytora. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Interfejs tworzy okna dokumentów w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [starsze interfejsy w edytorze](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Aby zapewnić punkty nawigacji do tyłu i do przodu w oknie, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfejs. Edytor tekstu używa znaczników tekstowych do identyfikowania punktów nawigacji w dokumencie.

## <a name="the-running-document-table"></a>Uruchomiona tabela dokumentów
 IDE korzysta z uruchomionej tabeli dokumentu (RDT) w celu śledzenia stanu każdego okna dokumentu. RDT jest mechanizmem, za pomocą którego okna dokumentów są powiadamiane o zdarzeniach, na przykład po zamknięciu rozwiązania lub edytowaniu pliku. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Zobacz też
- [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)
