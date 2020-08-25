---
title: Jak ręcznie uruchomić analizę kodu dla kodu zarządzanego
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1077e2cdae790fe8a7b7309b1e6427cd3ef81b48
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800167"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Instrukcje: ręczne uruchamianie analizy kodu dla kodu zarządzanego (wymaga programu Visual Studio 2019 w wersji 16,5 lub nowszej)
Domyślnie .NET Compiler Platform ("Roslyn") analizatory kodu analizują kod C# lub Visual Basic w trakcie pisania przez przeprowadzenie analizy na żywo, a także podczas kompilowania. W związku z tym zwykle nie jest wymagane Ręczne wyzwalanie analizy kodu. Istnieje jednak kilka scenariuszy, w których warto ręcznie wyzwolić analizę kodu:

- Domyślnie Analiza kodu na żywo wykonuje analizatory tylko dla otwartych plików w programie Visual Studio. Jednak użytkownik może chcieć wyświetlić ostrzeżenia analizy kodu dla wszystkich plików w określonym projekcie lub rozwiązaniu. Jeśli tak, należy wyzwolić analizę kodu raz w projekcie lub rozwiązaniu. Możesz też włączyć funkcję ciągłej analizy kodu na żywo do wykonania na całym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [How to: Configure Live Code Analysis Scope for Managed Code](./configure-live-code-analysis-scope-managed-code.md).
- Możesz preferować przepływ pracy wykonywania analizy kodu na żądanie w celu przeprowadzenia ciągłej analizy na żywo lub analizy czasu kompilacji. W takim przypadku można wyłączyć wykonywanie analizatora podczas analizy na żywo i/lub kompilacji. Aby uzyskać informacje na temat wyłączania analizy, zobacz [Jak wyłączyć analizę kodu źródłowego](disable-code-analysis.md). Następnie warto ręcznie wyzwolić analizę kodu w projekcie lub rozwiązaniu. 

### <a name="run-code-analysis-manually"></a>Ręczne przeprowadzanie analizy kodu

1. W **Eksplorator rozwiązań**wybierz projekt.

2. W menu **Analizuj** wybierz opcję **Uruchom analizę kodu dla** *nazwy projektu*.

Analiza kodu rozpocznie wykonywanie w tle. Powinien zostać wyświetlony komunikat **Analiza kodu dla \<project> ...** na pasku stanu programu Visual Studio w kierunku lewego dolnego rogu. Po zakończeniu analizy kodu komunikat o stanie zmieni się na **Analiza kodu ukończona dla \<project> **. Lista błędów zostanie wkrótce odświeżona przy użyciu całej diagnostyki analizy kodu.
