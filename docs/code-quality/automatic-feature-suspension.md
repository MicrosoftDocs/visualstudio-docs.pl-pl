---
title: Automatyczne wstrzymanie funkcji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431244"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji

Jeśli dostępna pamięć systemowa spadnie do 200 MB lub mniej, program Visual Studio wyświetla następujący komunikat w edytorze kodu:

![Tekst alertu zawieszający pełną analizę rozwiązania](../code-quality/media/fsa_alert.png)

Gdy program Visual Studio wykryje warunek małej ilości pamięci, automatycznie zawiesza niektóre zaawansowane funkcje, aby pomóc mu pozostać stabilnym. Visual Studio nadal działa jak poprzednio, ale jego wydajność jest obniżona.

W stanie małej ilości pamięci odbywają się następujące akcje:

- Analiza kodu na żywo dla języka Visual C# i Visual Basic jest zredukowana do minimalnego zakresu.

- [Modułu wyrzucania elementów](/dotnet/standard/garbage-collection/index) bezużytecznych (GC) tryb niskiego opóźnienia dla języka Visual C# i Visual Basic jest wyłączona.

- Pamięci podręczne programu Visual Studio są opróżniane.

## <a name="improve-visual-studio-performance"></a>Zwiększanie wydajności programu Visual Studio

Aby uzyskać porady i wskazówki dotyczące poprawy wydajności programu Visual Studio w przypadku dużych rozwiązań lub warunków o małej ilości pamięci, zobacz [Zagadnienia dotyczące wydajności dla dużych rozwiązań.](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Analiza kodu na żywo jest zredukowana do minimalnego zakresu

Domyślnie analiza kodu na żywo jest wykonywana dla otwartych dokumentów i projektów. Można dostosować ten zakres analizy, aby zmniejszyć do bieżącego dokumentu lub zwiększyć do całego rozwiązania. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](./configure-live-code-analysis-scope-managed-code.md). W stanie małej ilości pamięci visual studio wymusza zakres analizy na żywo, które mają zostać zmniejszone do bieżącego dokumentu. Można jednak ponownie włączyć preferowany zakres analizy, wybierając przycisk **Ponownie włącz** na pasku informacyjnym po wyświetleniu lub ponowne uruchomienie programu Visual Studio. Okno dialogowe Opcje zawsze zawiera bieżące ustawienia zakresu analizy kodu na żywo.

## <a name="gc-low-latency-disabled"></a>GC z małym opóźnieniem wyłączone

Aby ponownie włączyć tryb małych opóźnień GC, uruchom ponownie program Visual Studio. Domyślnie visual studio włącza tryb GC o małym opóźnieniu przy każdym wpisywania, aby upewnić się, że wpisywanie nie blokuje żadnych operacji GC. Jeśli jednak warunek braku pamięci powoduje, że program Visual Studio wyświetla ostrzeżenie o automatycznym zawieszeniu, tryb małych opóźnień GC jest wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio ponownie włącza domyślne zachowanie GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Opróżnione bufory programu Visual Studio

Jeśli kontynuować bieżącą sesję rozwoju lub ponownie uruchomić program Visual Studio, wszystkie pamięci podręczne programu Visual Studio są natychmiast opróżniane, ale zaczynają ponownie wypełniać. Opróżnione bufory obejmują bufory dla następujących funkcji:

- Znajdź wszystkie odwołania

- Nawiguj do

- Dodaj using

Ponadto pamięci podręczne używane do wewnętrznych operacji programu Visual Studio są również wyczyszczone.

> [!NOTE]
> Automatyczne ostrzeżenie o zawieszeniu funkcji występuje tylko raz na podstawie rozwiązania, a nie na podstawie na sesję. Oznacza to, że jeśli przełączysz się z języka Visual Basic do języka Visual C# (lub odwrotnie) i napotkasz inny warunek braku pamięci, możesz uzyskać inne ostrzeżenie o zawieszeniu funkcji automatycznych.

## <a name="see-also"></a>Zobacz też

- [Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](./configure-live-code-analysis-scope-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals)
- [Zagadnienia dotyczące wydajności dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
