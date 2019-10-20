---
title: 'CA1065: nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4b49ea9c293128efd400a1aa22d78ae4ee945092
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663597"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Nie należy wyrzucać wyjątków w nieoczekiwanych lokalizacjach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda, od której nie oczekiwano zgłaszania wyjątków, zgłasza wyjątek.

## <a name="rule-description"></a>Opis reguły
 Metody, które nie są oczekiwane na wygenerowanie wyjątków, można podzielić w następujący sposób:

- Metody get właściwości

- Metody dostępu do zdarzeń

- Equals — metody

- Metody GetHashCode

- Metody ToString

- Konstruktory statyczne

- Finalizatory

- Metody Dispose

- Operatory równości

- Operatory rzutowania niejawnego

  W poniższych sekcjach omówiono te typy metod.

### <a name="property-get-methods"></a>Metody get właściwości
 Właściwości są zasadniczo polami inteligentnymi. W związku z tym powinny one zachowywać się jak najwięcej pola. Pola nie generują wyjątków i nie powinny mieć właściwości. Jeśli masz właściwość, która zgłasza wyjątek, rozważ utworzenie jej jako metody.

 Następujące wyjątki mogą być zgłaszane z metody get właściwości:

- <xref:System.InvalidOperationException?displayProperty=fullName> i wszystkie pochodne (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> i wszystkie pochodne

- <xref:System.ArgumentException?displayProperty=fullName> (tylko ze indeksowanych Get)

- <xref:System.Collections.Generic.KeyNotFoundException> (tylko ze indeksowanych Get)

### <a name="event-accessor-methods"></a>Metody dostępu do zdarzeń
 Metody dostępu zdarzeń powinny być prostymi operacjami, które nie generują wyjątków. Zdarzenie nie powinno zgłosić wyjątku podczas próby dodania lub usunięcia programu obsługi zdarzeń.

 Następujące wyjątki mogą zostać zgłoszone przez obiekt dostępu do zdarzeń:

- <xref:System.InvalidOperationException?displayProperty=fullName> i wszystkie pochodne (w tym <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> i wszystkie pochodne

- <xref:System.ArgumentException> i pochodne

### <a name="equals-methods"></a>Equals — metody
 Następujące metody **równości** nie powinny generować wyjątków:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

  Metoda **Equals** powinna zwracać `true` lub `false` zamiast zgłaszać wyjątek. Na przykład jeśli wartość Equals jest przenoszona dwa niezgodne typy, należy po prostu zwrócić `false` zamiast zgłaszać <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metody GetHashCode
 Następujące metody **GetHashCode** zazwyczaj nie generują wyjątków:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode (T)](http://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** zawsze powinna zwracać wartość. W przeciwnym razie można utracić elementy w tabeli skrótów.

  Wersje **GetHashCode** , które przyjmują argument mogą zgłosić <xref:System.ArgumentException>. Jednak **obiekt. GetHashCode** nigdy nie powinien zgłosić wyjątku.

### <a name="tostring-methods"></a>Metody ToString
 Debuger używa <xref:System.Object.ToString%2A?displayProperty=fullName>, aby wyświetlić informacje o obiektach w formacie ciągu. W związku z tym **ToString** nie powinien zmieniać stanu obiektu i nie powinien generować wyjątków.

### <a name="static-constructors"></a>Konstruktory statyczne
 Wyrzucanie wyjątków od konstruktora statycznego powoduje, że typ nie będzie bezużyteczny w bieżącej domenie aplikacji. Aby zgłaszać wyjątek z konstruktora statycznego, należy mieć bardzo dobry powód (na przykład problem z zabezpieczeniami).

### <a name="finalizers"></a>Finalizatory
 Zgłaszanie wyjątku od finalizatora powoduje, że środowisko CLR może szybko zakończyć pracę, co spowoduje rozbicie procesu. W związku z tym, należy zawsze unikać zgłaszania wyjątków w finalizatorze.

### <a name="dispose-methods"></a>Metody Dispose
 Metoda <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nie powinna zgłosić wyjątku. Metoda Dispose jest często wywoływana jako część logiki oczyszczania w klauzuli `finally`. W związku z tym jawne zgłaszanie wyjątku z metody Dispose wymusza, aby użytkownik dodał obsługę wyjątków wewnątrz klauzuli `finally`.

 Ścieżka kodu **Dispose (false)** nigdy nie powinna zgłaszać wyjątków, ponieważ jest prawie zawsze wywoływana z finalizatora.

### <a name="equality-operators--"></a>Operatory równości (= =,! =)
 Podobnie jak metody Equals, operatory równości powinny zwracać `true` lub `false` i nie powinny zgłaszać wyjątków.

### <a name="implicit-cast-operators"></a>Operatory rzutowania niejawnego
 Ponieważ użytkownik często nie jest świadomy, że wywołano operator rzutowania niejawnego, wyjątek zgłoszony przez niejawnego operatora rzutowania jest całkowicie nieoczekiwany. W związku z tym nie należy zgłaszać wyjątków z niejawnych operatorów rzutowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 W przypadku metod pobierających właściwości Zmień logikę, tak aby nie było już konieczne zgłaszanie wyjątku, lub zmień właściwość na metodę.

 Dla wszystkich innych typów metod wymienionych wcześniej Zmień logikę, tak aby nie musiała już zgłosić wyjątku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli naruszenie zostało spowodowane przez deklarację wyjątku zamiast zgłoszonego wyjątku.

## <a name="related-rules"></a>Powiązane reguły
 [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątku](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)
