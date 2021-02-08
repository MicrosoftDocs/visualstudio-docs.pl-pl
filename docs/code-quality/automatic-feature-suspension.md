---
title: Automatyczne wstrzymanie funkcji
ms.date: 11/04/2016
description: Dowiedz się, w jaki sposób program Visual Studio zmniejsza zakres analizy, wyłącza tryb niskiego opóźnienia odzyskiwania pamięci i opróżnia pamięć podręczną, gdy pamięć systemowa jest ograniczona.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: efd053a846a7bf70f475db44788b14152498dc0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843725"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji

Jeśli ilość dostępnej pamięci systemowej spadnie do 200 MB lub mniej, program Visual Studio wyświetli następujący komunikat w edytorze kodu:

![Tekst alertu wstrzymywanie pełnej analizy rozwiązania](../code-quality/media/fsa_alert.png)

Gdy program Visual Studio wykryje stan niskiej ilości pamięci, automatycznie zawiesza pewne funkcje zaawansowane, aby pomóc zachować stabilność. Program Visual Studio będzie nadal działał jak wcześniej, ale jego wydajność jest obniżona.

W przypadku niedostatecznej ilości pamięci wykonywane są następujące akcje:

- Analiza kodu na żywo dla Visual C# i Visual Basic jest zredukowana do minimalnego zakresu.

- Tryb niskiego opóźnienia [odzyskiwania pamięci](/dotnet/standard/garbage-collection/index) (GC) dla Visual C# i Visual Basic jest wyłączony.

- Pamięci podręczne programu Visual Studio są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawianie wydajności programu Visual Studio

Porady i wskazówki dotyczące poprawy wydajności programu Visual Studio w przypadku dużych rozwiązań lub warunków braku pamięci można znaleźć w temacie [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Analiza kodu na żywo jest ograniczona do minimalnego zakresu

Domyślnie wykonywanie analizy kodu na żywo jest wykonywane w przypadku otwartych dokumentów i projektów. Ten zakres analizy można dostosować do bieżącego dokumentu lub zwiększyć do całego rozwiązania. Aby uzyskać więcej informacji, zobacz [How to: Configure Live Code Analysis Scope for Managed Code](./configure-live-code-analysis-scope-managed-code.md). W niewielkim stanie pamięci program Visual Studio wymusza zmniejszenie zakresu analizy na żywo do bieżącego dokumentu. Można jednak ponownie włączyć preferowany zakres analizy, wybierając przycisk **ponownie włącz** na pasku informacyjnym, gdy zostanie wyświetlony lub przez ponowne uruchomienie programu Visual Studio. W oknie dialogowym Opcje zawsze są wyświetlane bieżące ustawienia zakresu analizy kodu na żywo.

## <a name="gc-low-latency-disabled"></a>Wyłączono niski czas oczekiwania na odzyskiwanie pamięci

Aby ponownie włączyć tryb niskiego opóźnienia GC, uruchom ponownie program Visual Studio. Domyślnie program Visual Studio włącza tryb niskiego opóźnienia GC podczas wpisywania, aby upewnić się, że wpisywanie nie blokuje żadnych operacji GC. Jeśli jednak niewielka ilość pamięci powoduje, że program Visual Studio wyświetli ostrzeżenie o automatycznym zawieszeniu, tryb niskiego opóźnienia GC jest wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio powoduje ponowne włączenie domyślnego zachowania GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Opróżnione pamięci podręczne programu Visual Studio

Jeśli będziesz kontynuować bieżącą sesję programistyczną lub ponownie uruchom program Visual Studio, wszystkie pamięci podręczne programu Visual Studio zostaną natychmiast opróżnione, ale rozpocznie się ponowne wypełnianie. Opróżnione pamięci podręczne obejmują pamięć podręczną dla następujących funkcji:

- Znajdź wszystkie odwołania

- Przejdź do

- Dodaj przy użyciu

Ponadto pamięci podręczne używane na potrzeby wewnętrznych operacji programu Visual Studio również są wyczyszczone.

> [!NOTE]
> Ostrzeżenie o zawieszeniu funkcji automatycznych występuje tylko raz dla poszczególnych rozwiązań, a nie dla poszczególnych sesji. Oznacza to, że w przypadku przełączenia z Visual Basic do Visual C# (lub odwrotnie) i uruchomienia do innego stanu niskiej ilości pamięci można prawdopodobnie uzyskać kolejne ostrzeżenie o zawieszeniu funkcji automatycznej.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](./configure-live-code-analysis-scope-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
