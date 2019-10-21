---
title: Automatyczne wstrzymanie funkcji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606536"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji

Jeśli ilość dostępnej pamięci systemowej spadnie do 200 MB lub mniej, program Visual Studio wyświetli następujący komunikat w edytorze kodu:

![Tekst alertu wstrzymywanie pełnej analizy rozwiązania](../code-quality/media/fsa_alert.png)

Gdy program Visual Studio wykryje stan niskiej ilości pamięci, automatycznie zawiesza pewne funkcje zaawansowane, aby pomóc zachować stabilność. Program Visual Studio będzie nadal działał jak wcześniej, ale jego wydajność jest obniżona.

W przypadku niedostatecznej ilości pamięci wykonywane są następujące akcje:

- Pełna analiza rozwiązań dla wizualizacji C# i Visual Basic jest wyłączona.

- Tryb niskiego opóźnienia [odzyskiwania pamięci](/dotnet/standard/garbage-collection/index) (GC) dla wizualizacji C# i Visual Basic jest wyłączony.

- Pamięci podręczne programu Visual Studio są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawianie wydajności programu Visual Studio

Porady i wskazówki dotyczące poprawy wydajności programu Visual Studio w przypadku dużych rozwiązań lub warunków braku pamięci można znaleźć w temacie [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Zawieszono pełną analizę rozwiązania

Domyślnie Pełna analiza rozwiązań jest włączona dla Visual Basic i wyłączone dla wizualizacji C#. Jednak w przypadku braku pamięci Pełna analiza rozwiązań jest automatycznie wyłączona dla Visual Basic i wizualizacji C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Można jednak ponownie włączyć pełną analizę rozwiązania, wybierając przycisk **ponownie włącz** na pasku informacyjnym, gdy zostanie wyświetlony, zaznaczając pole wyboru **Włącz pełną analizę rozwiązań** w oknie dialogowym Opcje lub przez ponowne uruchomienie programu Visual Studio. W oknie dialogowym Opcje zawsze są wyświetlane bieżące pełne ustawienia analizy rozwiązania. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Wyłączono niski czas oczekiwania na odzyskiwanie pamięci

Aby ponownie włączyć tryb niskiego opóźnienia GC, uruchom ponownie program Visual Studio. Domyślnie program Visual Studio włącza tryb niskiego opóźnienia GC podczas wpisywania, aby upewnić się, że wpisywanie nie blokuje żadnych operacji GC. Jeśli jednak niewielka ilość pamięci powoduje, że program Visual Studio wyświetli ostrzeżenie o automatycznym zawieszeniu, tryb niskiego opóźnienia GC jest wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio powoduje ponowne włączenie domyślnego zachowania GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Opróżnione pamięci podręczne programu Visual Studio

Jeśli będziesz kontynuować bieżącą sesję programistyczną lub ponownie uruchom program Visual Studio, wszystkie pamięci podręczne programu Visual Studio zostaną natychmiast opróżnione, ale rozpocznie się ponowne wypełnianie. Opróżnione pamięci podręczne obejmują pamięć podręczną dla następujących funkcji:

- Znajdź wszystkie odwołania

- Przejdź do

- Dodaj przy użyciu

Ponadto pamięci podręczne używane na potrzeby wewnętrznych operacji programu Visual Studio również są wyczyszczone.

> [!NOTE]
> Ostrzeżenie o zawieszeniu funkcji automatycznych występuje tylko raz dla poszczególnych rozwiązań, a nie dla poszczególnych sesji. Oznacza to, że w przypadku przełączenia z C# Visual Basic do wizualizacji (lub odwrotnie) i uruchomienia w innym stanie niskiej ilości pamięci można prawdopodobnie uzyskać kolejne ostrzeżenie o zawieszeniu funkcji automatycznej.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](/dotnet/standard/garbage-collection/fundamentals)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
