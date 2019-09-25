---
title: 'CA2001: Unikaj wywoływania problematycznych metod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233193"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Unikaj wywoływania problematycznych metod

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategoria|Microsoft.Reliability|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.

## <a name="rule-description"></a>Opis reguły

Unikaj tworzenia niepotrzebnych i potencjalnie niebezpiecznych wywołań metod. Naruszenie tej reguły występuje, gdy element członkowski wywołuje jedną z następujących metod:

|Metoda|Opis|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Wywoływanie GC. Zbieranie danych może znacząco wpłynąć na wydajność aplikacji i jest rzadko konieczne. Aby uzyskać więcej informacji, zobacz wpis w blogu [Mariani Performance smakowite kąski](http://go.microsoft.com/fwlink/?LinkId=169256) w witrynie MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Wątki. Suspend i Thread. Resume są przestarzałe ze względu na nieprzewidywalne zachowanie.  Użyj <xref:System.Threading> innych klas w przestrzeni nazw, takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, i <xref:System.Threading.Semaphore>, aby synchronizować wątki lub chronić zasoby.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Metoda DangerousGetHandle stanowi zagrożenie bezpieczeństwa, ponieważ może zwrócić dojście, które jest nieprawidłowe. <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> Zobacz<xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> i metody, aby uzyskać więcej informacji na temat bezpiecznego używania metody DangerousGetHandle.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Te metody mogą ładować zestawy z nieoczekiwanych lokalizacji. Na przykład zapoznaj się z wpisami [w blogu Suzanne programu .NET CLR uwagi dotyczące języka LoadFile a Metody](http://go.microsoft.com/fwlink/?LinkId=164450) LoadFrom i [wybierania kontekstu powiązania](http://go.microsoft.com/fwlink/?LinkId=164451) dla informacji o metodach ładujących zestawy.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) Mechanizm<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Mechanizm|Przez czas, gdy kod użytkownika zaczyna wykonywanie w procesie zarządzanym, jest zbyt późno na niezawodne wywoływanie CoSetProxyBlanket. Środowisko uruchomieniowe języka wspólnego (CLR) wykonuje akcje inicjowania, które mogą uniemożliwiać pomyślne wywoływanie P/Invoke użytkowników.<br /><br /> Jeśli musisz wywołać CoSetProxyBlanket dla aplikacji zarządzanej, zalecamy uruchomienie procesu przy użyciu kodu natywnego (C++), wywołanie CoSetProxyBlanket w kodzie natywnym, a następnie uruchomienie aplikacji kodu zarządzanego w procesie. (Pamiętaj o określeniu numeru wersji środowiska uruchomieniowego).|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Usuń lub Zastąp wywołanie metody niebezpieczne lub problematyczne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Komunikaty z tej reguły należy pomijać tylko wtedy, gdy nie są dostępne żadne alternatywy dla problematycznej metody.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące niezawodności](../code-quality/reliability-warnings.md)