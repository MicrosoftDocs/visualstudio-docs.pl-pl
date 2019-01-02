---
title: 'CA2109: Przejrzyj widoczne procedury obsługi zdarzeń'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d234fe466395b5267c18eae9aa14d855d58abe2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860848"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Przejrzyj widoczne procedury obsługi zdarzeń

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Wykryto publiczną lub chronioną metodę obsługi zdarzeń.

## <a name="rule-description"></a>Opis reguły
 Metoda widoczna na zewnątrz obsługi zdarzeń przedstawia informacje o problem z zabezpieczeniami, który wymaga wykonania przeglądu.

Nie ujawniaj metody obsługi zdarzeń, chyba że jest to absolutnie konieczne. Program obsługi zdarzeń, typu delegata, która wywołuje metodę narażonych można dodać do dowolnego zdarzenia, tak długo, jak sygnatury procedury obsługi i zdarzenia są zgodne. Zdarzenia potencjalnie może zostać wywołane przez dowolny kod i często są wywoływane przez system wysoce zaufanym kod w odpowiedzi na działania użytkownika, takie jak kliknięcie przycisku. Dodawanie sprawdzania zabezpieczeń do metody obsługi zdarzeń nie uniemożliwia kodu rejestrowania programu obsługi zdarzeń, który wywołuje tę metodę.

 Żądanie nie może chronić niezawodne metody wywoływane przez program obsługi zdarzeń. Zabezpieczenia zapotrzebowania na pomoc zabezpieczyć kod z niezaufanych wywołujących badanie obiektów wywołujących w stosie wywołań. Kod, który dodaje procedurę obsługi zdarzeń do zdarzenia nie jest musi występować w stosie wywołań, po uruchomieniu metody obsługi zdarzeń. W związku z tym stos wywołań może mieć tylko bardzo zaufane obiekty wywołujące po wywołaniu metody obsługi zdarzeń. To powoduje, że zapotrzebowanie wprowadzone przez metodę programu obsługi zdarzeń została wykonana pomyślnie. Ponadto żądane uprawnienie może być oceniane pod po wywołaniu metody. Z tego względu ryzyko nie naprawianie naruszenie tej zasady może być oceniana tylko po zapoznaniu się z metody obsługi zdarzeń. Podczas przeglądania kodu należy wziąć pod uwagę następujące kwestie:

- Powoduje obsługi zdarzenia wykonania żadnych operacji, które są niebezpieczne lub możliwe do wykorzystania, takich jak Potwierdzanie uprawnień lub uprawnienie kodu niezarządzanego z pominięciem?

- Co to są zagrożenia bezpieczeństwa, do i z kodu, ponieważ go można uruchomić w dowolnym momencie tylko bardzo zaufanych obiektów wywołujących w stosie?

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, przejrzyj metody, a następnie ocenić następujące czynności:

- Czy można utworzyć metody obsługi zdarzeń niepublicznych?

- Czy jest możliwe przeniesienie wszystkich niebezpiecznych funkcji programu obsługi zdarzeń?

- Jeśli żądanie zabezpieczeń są nakładane, to można zrobić w inny sposób?

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń od tej reguły tylko po weryfikacji zabezpieczeń zachowania ostrożność aby upewnić się, że Twój kod nie stanowi zagrożenie bezpieczeństwa.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia metodę obsługi zdarzeń, które precyzyjnego złośliwego kodu.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>