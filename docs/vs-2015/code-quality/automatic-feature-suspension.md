---
title: Automatyczne zawieszenie funkcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655152"
---
# <a name="automatic-feature-suspension"></a>Automatyczne wstrzymanie funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Jeśli ilość dostępnej pamięci systemowej spadnie do 200 MB lub mniejszej, program Visual Studio wyświetla następujący komunikat w edytorze kodu.

 ![Tekst alertu wstrzymywanie pełnej analizy rozwiązania](../code-quality/media/fsa-alert.png "FSA_Alert")

 Gdy program Visual Studio wykryje stan niskiej ilości pamięci, automatycznie zawiesza pewne funkcje zaawansowane, aby pomóc zachować stabilność. Gdy zostanie wyświetlone ostrzeżenie o zawieszeniu funkcji zaawansowanej, program Visual Studio będzie nadal działał jak wcześniej, ale jego wydajność będzie nieznacznie obniżona.

 W niewielkim stanie pamięci następuje:

- Pełna analiza rozwiązań dla Visual C# i Visual Basic jest wyłączona.

- Tryb niskiego opóźnienia [odzyskiwania pamięci](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) dla Visual C# i Visual Basic jest wyłączony.

- Pamięci podręczne programu Visual Studio są opróżniane.

## <a name="improve-visual-studio-performance"></a>Poprawianie wydajności programu Visual Studio
 Porady i wskazówki dotyczące poprawy wydajności programu Visual Studio w przypadku dużych rozwiązań lub warunków braku pamięci można znaleźć w temacie [zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Zawieszono pełną analizę rozwiązania
 Domyślnie Pełna analiza rozwiązań jest włączona dla Visual Basic i wyłączone dla języka Visual C#. Jednak w przypadku braku pamięci Pełna analiza rozwiązań jest automatycznie wyłączona dla Visual Basic i Visual C#, niezależnie od ich ustawień w oknie dialogowym Opcje. Można jednak ponownie włączyć pełną analizę rozwiązania, wybierając przycisk **ponownie włącz** na pasku informacyjnym, gdy zostanie wyświetlony, zaznaczając pole wyboru **Włącz pełną analizę rozwiązań** w oknie dialogowym Opcje lub przez ponowne uruchomienie programu Visual Studio. W oknie dialogowym Opcje zawsze są wyświetlane bieżące pełne ustawienia analizy rozwiązania. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Wyłączono niski czas oczekiwania na odzyskiwanie pamięci
 Aby ponownie włączyć tryb niskiego opóźnienia GC, uruchom ponownie program Visual Studio.  Domyślnie program Visual Studio włącza tryb niskiego opóźnienia GC podczas wpisywania, aby upewnić się, że wpisywanie nie blokuje żadnych operacji GC. Jeśli jednak niewielka ilość pamięci powoduje, że program Visual Studio wyświetli ostrzeżenie o automatycznym zawieszeniu, tryb niskiego opóźnienia GC jest wyłączony dla tej sesji. Ponowne uruchomienie programu Visual Studio spowoduje ponowne włączenie domyślnego zachowania GC. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Opróżnione pamięci podręczne programu Visual Studio

Wszystkie pamięci podręczne programu Visual Studio są natychmiast opróżniane, ale rozpocznie się ponowne wypełnienie w przypadku kontynuowania bieżącej sesji programistycznej lub ponownego uruchomienia programu Visual Studio. Opróżnione pamięci podręczne obejmują pamięć podręczną dla następujących funkcji.

- Znajdź wszystkie odwołania

- Przejdź do

- Dodaj przy użyciu

Ponadto pamięci podręczne używane na potrzeby wewnętrznych operacji programu Visual Studio również są wyczyszczone.

> [!NOTE]
> Ostrzeżenie o zawieszeniu funkcji automatycznych występuje tylko raz dla poszczególnych rozwiązań, a nie dla poszczególnych sesji. Oznacza to, że w przypadku przełączenia z Visual Basic do Visual C# (lub odwrotnie) i uruchomienia do innego stanu niskiej ilości pamięci można prawdopodobnie uzyskać kolejne ostrzeżenie o zawieszeniu funkcji automatycznej.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Włączanie i wyłączanie pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Podstawy dotyczące odzyskiwania pamięci](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Zagadnienia dotyczące wydajności w przypadku dużych rozwiązań](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)