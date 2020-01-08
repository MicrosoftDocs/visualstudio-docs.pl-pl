---
title: Automatyczne wstrzymanie funkcji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6910bae3d924202fad8995d6ccd53efe848ba50
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573303"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji

Jeśli Twoje dostępnej pamięci systemowej kwalifikuje się do 200 MB lub mniej, Visual Studio wyświetla następujący komunikat w edytorze kodu:

![Tekst alertu zawieszanie pełnej analizy rozwiązania](../code-quality/media/fsa_alert.png)

Gdy program Visual Studio wykryje stan braku pamięci, automatycznie wstrzymuje niektórych zaawansowanych funkcji, aby ułatwić sobie trwały. Program Visual Studio w dalszym ciągu działać tak jak poprzednio, ale jego wydajność jest obniżona.

W stan braku pamięci wykonane następujące akcje:

- Pełnej analizy rozwiązania dla programu Visual C# i Visual Basic jest wyłączona.

- [Wyrzucanie elementów bezużytecznych](/dotnet/standard/garbage-collection/index) trybu o małych opóźnieniach (GC) dla Visual C# i Visual Basic jest wyłączona.

- Visual Studio pamięci podręczne są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawa wydajności programu Visual Studio

Aby uzyskać porady i wskazówki na temat sposobu poprawy wydajności programu Visual Studio podczas zajmowania się warunki małej ilości pamięci lub dużych rozwiązań, zobacz [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Pełnej analizy rozwiązania zawieszone

Domyślnie pełnej analizy rozwiązania jest włączona dla języka Visual Basic i wyłączone dla języka Visual C#. Jednak w stan braku pamięci pełnej analizy rozwiązania jest automatycznie wyłączana dla języka Visual Basic i Visual C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Jednakże, można ponownie włączyć pełnej analizy rozwiązania, wybierając **ponownie włączyć** informacje paska, gdy pojawia się, wybierając przycisk **Włączanie pełnej analizy rozwiązania** pole wyboru w oknie dialogowym Opcje, lub ponowne uruchomienie programu Visual Studio. Okno dialogowe Opcje zawsze wyświetla bieżące rozwiązanie pełną ustawień analizy. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC o małych opóźnieniach wyłączone

Aby ponownie włączyć tryb o małych opóźnieniach GC, uruchom ponownie program Visual Studio. Domyślnie program Visual Studio Włącza tryb o małych opóźnieniach GC, zawsze wtedy, gdy są wpisywanie, aby upewnić się, że wpisany tekst nie blokuje żadnych operacji GC. Jednak jeśli stan braku pamięci powoduje, że Visual Studio, aby wyświetlić ostrzeżenie automatyczne zawieszenie, GC o małych opóźnieniach tryb zostanie wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio włączające domyślne zachowanie GC. Aby uzyskać więcej informacji, zobacz temat <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio pamięci podręcznych opróżnione

Jeśli nadal bieżącej sesji rozwoju lub uruchom ponownie program Visual Studio, wszystkie bufory programu Visual Studio są natychmiast opróżnić, ale rozpocząć ponownie wypełnić. Pamięci podręczne opróżnione to pamięci podręczne dla następujących funkcji:

- Znajdź wszystkie odwołania

- Przejdź do

- Dodaj instrukcję Using

Ponadto używane dla operacji programu Visual Studio wewnętrznych pamięci podręcznych również zostaną wyczyszczone.

> [!NOTE]
> Ostrzeżenie dotyczące zawieszenia funkcji automatycznego pojawia się tylko raz na podstawie danego rozwiązania, a nie na podstawie sesji. Oznacza to, że jeśli przełączyć się z języka Visual Basic do Visual C# (lub odwrotnie) i w inny stan braku pamięci, prawdopodobnie uzyskasz innej ostrzeżenie dotyczące zawieszenia funkcji automatycznego.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
