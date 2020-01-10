---
title: 'CA2001: Unikaj wywoływania problematycznych metod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a2ed905f8291bf503217239cc287c50b970572f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851723"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Unikaj wywoływania problematycznych metod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.

## <a name="rule-description"></a>Opis reguły
 Unikaj tworzenia niepotrzebnych i potencjalnie niebezpiecznych wywołań metod.

 Naruszenie tej reguły występuje, gdy element członkowski wywołuje jedną z poniższych metod.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Wywoływanie GC. Zbieranie danych może znacząco wpłynąć na wydajność aplikacji i jest rzadko konieczne. Aby uzyskać więcej informacji, zobacz wpis w blogu dotyczącym [wydajności smakowite kąski Mariani](https://blogs.msdn.com/ricom/archive/2004/11/29/271829.aspx) w witrynie MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Wątki. Suspend i Thread. Resume są przestarzałe ze względu na nieprzewidywalne zachowanie.  Użyj innych klas w przestrzeni nazw <xref:System.Threading>, takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>i <xref:System.Threading.Semaphore>, aby synchronizować wątki lub chronić zasoby.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Metoda DangerousGetHandle stanowi zagrożenie bezpieczeństwa, ponieważ może zwrócić dojście, które jest nieprawidłowe. Zobacz <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> i metody <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>, aby uzyskać więcej informacji na temat bezpiecznego używania metody DangerousGetHandle.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Te metody mogą ładować zestawy z nieoczekiwanych lokalizacji. Na przykład zapoznaj się z wpisami w blogu Suzanne środowiska .NET CLR uwagi dotyczące języka [LoadFile a LoadFrom](https://blogs.msdn.com/suzcook/archive/2003/09/19/loadfile-vs-loadfrom.aspx) i [Wybierz kontekst powiązania](https://blogs.msdn.com/suzcook/archive/2003/05/29/57143.aspx) w witrynie MSDN w sieci Web, aby uzyskać informacje o metodach ładujących zestawy.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (Ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (Ole32)|Przez czas, gdy kod użytkownika zaczyna wykonywanie w procesie zarządzanym, jest zbyt późno na niezawodne wywoływanie CoSetProxyBlanket. Środowisko uruchomieniowe języka wspólnego (CLR) wykonuje akcje inicjowania, które mogą uniemożliwiać pomyślne wywoływanie P/Invoke użytkowników.<br /><br /> Jeśli musisz wywołać CoSetProxyBlanket dla aplikacji zarządzanej, zalecamy uruchomienie procesu przy użyciu kodu natywnego (C++), wywołanie CoSetProxyBlanket w kodzie natywnym, a następnie uruchomienie aplikacji kodu zarządzanego w procesie. (Pamiętaj o określeniu numeru wersji środowiska uruchomieniowego).|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń lub Zastąp wywołanie metody niebezpieczne lub problematyczne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Komunikaty z tej reguły należy pomijać tylko wtedy, gdy nie są dostępne żadne alternatywy dla problematycznej metody.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące niezawodności](../code-quality/reliability-warnings.md)
