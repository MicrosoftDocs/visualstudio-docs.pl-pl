---
title: Widok systemu Windows | Microsoft Docs
description: Widok systemu Windows pokazuje drzewo wszystkich okien i kontrolek. Użyj go jako punktu wyjścia, aby uzyskać informacje o interesujących Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34a66e9c2728798330b52f87afe8ecdea8733508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906325"
---
# <a name="windows-view"></a>Widok okien
Podczas pierwszego otwierania programu Spy + + widok systemu Windows wyświetla drzewo wszystkich okien i kontrolek w systemie. Wyświetlane są dojścia do okna i nazwa klasy. Bieżące okno pulpit znajduje się w górnej części drzewa. Wszystkie inne okna są elementami podrzędnymi pulpitu i są wyświetlane zgodnie z hierarchią standardowego okna. Okna elementów równorzędnych pojawiają się na listach expansible z wcięciem poniżej ich elementów nadrzędnych.

 Na poniższym rysunku przedstawiono typowy widok systemu Windows Spy + + z rozwiniętym górnym węzłem.

 ![Widok systemu Windows Spy&#43;&#43; ](../debugger/media/spy--_windowsview.png "_WindowsView Spy + +") Widok systemu Windows Spy + +

 Bieżące okno pulpit znajduje się w górnej części drzewa. Wszystkie inne okna są elementami podrzędnymi pulpitu i są wyświetlane zgodnie z hierarchią standardowego okna z równorzędnymi oknami uporządkowanymi według kolejności Z. Można rozwinąć lub zwinąć dowolny węzeł nadrzędny drzewa, klikając symbol + lub-obok węzła.

 Gdy widok systemu Windows ma fokus, można użyć narzędzia wyszukiwania w oknie [dialogowym Wyszukiwanie okna](../debugger/window-search-dialog-box.md) , aby wyświetlić informacje z dowolnego okna otwartego w systemie.

## <a name="in-this-section"></a>W tej sekcji
 [Instrukcje: korzystanie z narzędzia wyszukiwania](../debugger/how-to-use-the-finder-tool.md) Pokazuje, w jaki sposób to narzędzie skanuje okna pod kątem właściwości lub komunikatów.

 [Instrukcje: wyszukiwanie okna w widoku systemu Windows](../debugger/how-to-search-for-a-window-in-windows-view.md) Wyjaśnia, jak znaleźć określone okno w widoku systemu Windows.

 [Instrukcje: Wyświetlanie właściwości okna](../debugger/how-to-display-window-properties.md) , w którym można otworzyć okno dialogowe Właściwości okna.

## <a name="related-sections"></a>Sekcje pokrewne
 [Widoki Spy + +](../debugger/spy-increment-views.md) Wyjaśnia widoki drzewa Spy + + systemu Windows, komunikatów, procesów i wątków.

 [Korzystanie z programu Spy + +](../debugger/using-spy-increment.md) Wprowadzenie do narzędzia Spy + + i wyjaśnienie, jak można go użyć.

 Okno [dialogowe Znajdowanie okna](../debugger/find-window-dialog-box.md) Służy do wyświetlania właściwości lub komunikatów z określonego okna.

 [Wyszukiwanie okna](../debugger/window-search-dialog-box.md) — okno dialogowe Służy do znajdowania węzła dla określonego okna w widoku systemu Windows.

 Okno [dialogowe Właściwości okna](../debugger/window-properties-dialog-box.md) Służy do wyświetlania właściwości okna wybranego w widoku systemu Windows.

 [Spy + + — Odwołanie](../debugger/spy-increment-reference.md) Zawiera sekcje opisujące poszczególne menu Spy + + i okna dialogowego.