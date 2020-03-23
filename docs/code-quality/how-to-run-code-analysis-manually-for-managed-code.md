---
title: 'Jak: Ręczne uruchamianie analizy kodu dla kodu zarządzanego'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431387"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Jak: Ręczne uruchamianie analizy kodu dla kodu zarządzanego (wymaga programu Visual Studio 2019 w wersji 16.5 lub nowszej)
Domyślnie analizatory kodu platformy kompilatora platformy .NET ("Roslyn") analizują kod języka C# lub Visual Basic podczas pisania, wykonując analizę na żywo, a także podczas kompilacji. W związku z tym zwykle nie trzeba ręcznie wyzwalać analizy kodu. Istnieją jednak pewne scenariusze, w których można ręcznie wyzwolić analizę kodu:

- Domyślnie analiza kodu na żywo wykonuje analizatory tylko dla otwartych plików w programie Visual Studio. Jednak może być zainteresowany wyświetlaniem ostrzeżenia analizy kodu dla wszystkich plików w określonym projekcie lub rozwiązaniu. Jeśli tak, chcesz wyzwolić analizę kodu raz w projekcie lub rozwiązaniu. Alternatywnie można włączyć ciągłą analizę kodu na żywo do wykonania na całe rozwiązanie. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](./configure-live-code-analysis-scope-managed-code.md).
- Możesz preferować przepływ pracy wykonywania analizy kodu na żądanie niż ciągłą analizę na żywo lub analizę czasu kompilacji. Jeśli tak, można wyłączyć wykonywanie analizatora podczas analizy na żywo i/lub kompilacji. Aby uzyskać informacje na temat wyłączania analizy, zobacz [Jak wyłączyć analizę kodu źródłowego](disable-code-analysis.md). Następnie chcesz ręcznie wyzwolić analizę kodu raz w projekcie lub rozwiązaniu. 

### <a name="run-code-analysis-manually"></a>Ręczne przeprowadzanie analizy kodu

1. W **Eksploratorze rozwiązań**kliknij projekt.

2. W menu **Analiza** kliknij polecenie **Uruchom analizę kodu w** programie Project *Name*.

Analiza kodu rozpocznie wykonywanie w tle. Powinien zostać wyświetlony komunikat **Uruchamianie analizy kodu dla \<projektu>...** na pasku stanu programu Visual Studio w kierunku lewego dolnego rogu. Po zakończeniu analizy kodu komunikat o stanie zmieni się na **Analiza kodu ukończona dla \<>projektu **. Lista błędów zostanie wkrótce odświeżona za pomocą wszystkich diagnostyki analizy kodu.
