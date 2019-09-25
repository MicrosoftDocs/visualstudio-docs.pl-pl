---
title: 'CA1700: Nie Nazwij wartości &#39;wyliczeniowych jako zarezerwowanych&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234390"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nie Nazwij wartości &#39;wyliczeniowych jako zarezerwowanych&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa elementu członkowskiego wyliczenia zawiera słowo "zarezerwowane".

## <a name="rule-description"></a>Opis reguły

Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. Nie powinno się oczekiwać, że użytkownicy ignorują element członkowski tylko dlatego, że jego nazwa zawiera "zastrzeżone", ani nie może polegać na przeczytaniu lub zapoznaniu się z dokumentacją. Ponadto ze względu na to, że zastrzeżone elementy członkowskie pojawiają się w przeglądarkach obiektów i inteligentnych zintegrowanych środowiskach programistycznych, mogą one spowodować pomyłkę, w której są faktycznie używane.

Zamiast używać zastrzeżonego elementu członkowskiego, Dodaj nowy element członkowski do wyliczenia w przyszłej wersji. W większości przypadków dodanie nowego elementu członkowskiego nie jest istotną zmianą, o ile dodanie nie spowoduje zmiany wartości oryginalnych elementów członkowskich.

W ograniczonej liczbie przypadków dodanie elementu członkowskiego jest istotną zmianą nawet wtedy, gdy pierwotne elementy członkowskie zachowują swoje oryginalne wartości. Przede wszystkim nie można zwrócić nowego elementu członkowskiego z istniejących ścieżek kodu bez przerywania wywołujących `switch` używających [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]instrukcji (`Select` in) na zwracanej wartości, która obejmuje całą listę elementów członkowskich i która zgłasza wyjątek w Domyślna wielkość liter. Dodatkowy problem polega na tym, że kod klienta nie może obsłużyć zmiany zachowania z metod odbicia, takich jak <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. W związku z tym, jeśli nowy element członkowski ma zostać zwrócony z istniejących metod lub znana niezgodność aplikacji jest spowodowana przez słabe użycie odbicia, jedynym rozwiązaniem do Nieprzerwania jest:

1. Dodaj nowe Wyliczenie zawierające pierwotnych i nowych członków.

2. Oznacz oryginalne Wyliczenie <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutem.

   Postępuj zgodnie z tą samą procedurą dla dowolnego widocznego na zewnątrz typów lub elementów członkowskich, które uwidaczniają oryginalne Wyliczenie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Usuń element członkowski lub zmień jego nazwę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły dla elementu członkowskiego, który jest aktualnie używany lub dla bibliotek, które zostały wcześniej wysłane.

## <a name="related-rules"></a>Powiązane reguły

[CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: Nie określaj prefiksu wartości wyliczenia z nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028 Magazyn wyliczeniowy powinien mieć wartość Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008 Wyliczenia powinny mieć wartość zerową](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)