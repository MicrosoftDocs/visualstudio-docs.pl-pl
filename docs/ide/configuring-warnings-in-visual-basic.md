---
title: 'Konfigurowanie ostrzeżeń w Visual Basic:'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33302a4a686d80621cc64ee018371a2d03ea30ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114730"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurowanie ostrzeżeń w języku Visual Basic

Kompilator [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zawiera zestaw ostrzeżeń dotyczących kodu, które mogą powodować błędy w czasie wykonywania. Możesz użyć tych informacji do pisania czystszego, szybszego i lepszego kodu z mniejszą liczbą błędów. Na przykład kompilator wyda ostrzeżenie, gdy użytkownik próbuje wywołać element członkowski nieprzypisanego zmiennej obiektu, `Try` powrócić z funkcji bez ustawiania wartości zwracanej lub wykonać blok z błędami w logice, aby wychwytać wyjątki.

Czasami kompilator zapewnia dodatkową logikę w imieniu użytkownika, dzięki czemu użytkownik może skupić się na zadaniu, a nie na przewidywanie możliwych błędów. W poprzednich [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]wersjach programu **Option Strict** użyto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ograniczenia dodatkowej logiki, którą zapewnia kompilator. Konfigurowanie ostrzeżeń umożliwia ograniczenie tej logiki w sposób bardziej szczegółowy, na poziomie poszczególnych ostrzeżeń.

Można dostosować projekt i wyłączyć niektóre ostrzeżenia nie istotne dla aplikacji podczas przekształcania innych ostrzeżeń w błędy. Na tej stronie wyjaśniono, jak włączać i wyłączać poszczególne ostrzeżenia.

## <a name="turning-warnings-off-and-on"></a>Wyłączanie i włączanie ostrzeżeń
Istnieją dwa różne sposoby konfigurowania ostrzeżeń: można je skonfigurować za pomocą **projektanta projektu**lub można użyć opcji kompilatora **/warnaserror** i **/nowarn.**

Karta **Kompilacja** strony **projektanta projektu** umożliwia włączanie i wyłączanie ostrzeżeń. Zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia,** aby wyłączyć wszystkie ostrzeżenia; wybierz **opcję Traktuj wszystkie ostrzeżenia jako błędy,** aby traktować wszystkie ostrzeżenia jako błędy. Niektóre pojedyncze ostrzeżenia można przełączać jako błąd lub ostrzeżenie zgodnie z potrzebami w wyświetlanej tabeli.

Gdy **opcja Strict** jest **ustawiona**na Off , **opcja ścisłe** związane ostrzeżenia nie mogą być traktowane niezależnie od siebie. Gdy **opcja Ścisła** jest ustawiona **na Włączone,** skojarzone ostrzeżenia są traktowane jako błędy, bez względu na ich stan. Gdy **opcja Strict** jest ustawiona na **Niestandardowa,** określając `/optionstrict:custom` w kompilatorze wiersza polecenia, ostrzeżenia Option **Strict** mogą być włączane lub wyłączane niezależnie.

Opcja wiersza polecenia **/warnaserror** kompilatora może również służyć do określenia, czy ostrzeżenia są traktowane jako błędy. Do tej opcji można dodać listę rozdzielanych przecinkami, aby określić, które ostrzeżenia powinny być traktowane jako błędy lub ostrzeżenia za pomocą + lub -. W poniższej tabeli przedstawiono możliwe opcje.

|Opcja wiersza polecenia|Określa|
| - |---------------|
|`/warnaserror+`|Traktuj wszystkie ostrzeżenia jako błędy|
|`/warnsaserror`-|Nie należy traktować jako ostrzeżenia jako błędy. Domyślnie włączone.|
|`/warnaserror+:<warning list` `>`|Traktuj określone ostrzeżenia jako błędy, wymienione przez ich numer identyfikatora błędu na liście rozdzielanych przecinkami r.|
|`/warnaserror-:<warning list>`|Nie należy traktować określonych ostrzeżeń jako błędów, wymienionych przez ich numer identyfikatora błędu na liście rozdzielanych przecinkami.|
|`/nowarn`|Nie zgłaszaj ostrzeżeń.|
|`/nowarn:<warning list>`|Nie zgłaszaj określonych ostrzeżeń, wymienionych przez ich numer identyfikatora błędu na liście rozdzielanych przecinkami.|

Lista ostrzeżeń zawiera numery identyfikatorów błędów ostrzeżeń, które powinny być traktowane jako błędy, które mogą być używane z opcjami wiersza polecenia, aby włączyć lub wyłączyć określone ostrzeżenia. Jeśli lista ostrzeżeń zawiera nieprawidłowy numer, zgłaszany jest błąd.

## <a name="examples"></a>Przykłady
W tej tabeli przykładów argumentów wiersza polecenia opisano, co robi każdy argument.

|Argument|Opis|
|--------------|-----------------|
|`vbc /warnaserror`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|
|`vbc /warnaserror:42024`|Określa, że ostrzeżenie 42024 powinno być traktowane jako błąd.|
|`vbc /warnaserror:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 powinny być traktowane jako błędy.|
|`vbc /nowarn`|Określa, że nie należy zgłaszać żadnych ostrzeżeń.|
|`vbc /nowarn:42024`|Określa, że ostrzeżenie 42024 nie powinno być zgłaszane.|
|`vbc /nowarn:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 nie powinny być zgłaszane.|

## <a name="types-of-warnings"></a>Rodzaje ostrzeżeń
Poniżej znajduje się lista ostrzeżeń, które można traktować jako błędy.

### <a name="implicit-conversion-warning"></a>Ostrzeżenie o konwersji niejawnej
Generowane dla wystąpień konwersji niejawnej. Nie obejmują one konwersji niejawnych z wewnętrznego typu liczbowego `&` do ciągu podczas korzystania z operatora. Domyślnie dla nowych projektów jest wyłączony.

Identyfikator: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Ostrzeżenie o wywołaniu metody późnego wiązania i rozpoznawaniu przeciążenia
Generowane dla wystąpień późnego wiązania. Domyślnie dla nowych projektów jest wyłączony.

Identyfikator: 42017

### <a name="operands-of-type-object-warnings"></a>Argumenty ostrzeżenia typu "Obiekt"
Generowane w przypadku wystąpienia `Object` argumentów typu, które powodowałyby błąd z **opcją Opcja Ścisła wł.** Domyślnie dla nowych projektów jest włączony.

ID: 42018 i 42019

### <a name="declarations-require-as-clause-warnings"></a>Deklaracje wymagają ostrzeżeń klauzuli "As"
Generowane, gdy zmienna, funkcja lub `As` deklaracja właściwości bez klauzuli spowodowałaby błąd z **opcją Ścisłe włączone**. Przyjmuje się, że zmienne, które nie mają `Object`przypisanego typu, są typu . Domyślnie dla nowych projektów jest włączony.

Identyfikator: 42020 (deklaracja zmienna), 42021 (deklaracja funkcji) i 42022 (deklaracja właściwości).

### <a name="possible-null-reference-exception-warnings"></a>Możliwe ostrzeżenia o wyjątku odwołania zerowego
Generowane, gdy zmienna jest używana przed przypisaniem jej wartości. Domyślnie dla nowych projektów jest włączony.

Identyfikator: 42104, 42030

### <a name="unused-local-variable-warning"></a>Ostrzeżenie o nieużywanych zmiennych lokalnych
Generowane, gdy zmienna lokalna jest zadeklarowana, ale nigdy nie jest mowa. Wartość domyślna jest włączona.

Identyfikator: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Dostęp współdzielonego elementu członkowskiego za pomocą ostrzeżenia zmiennej wystąpienia
Generowane podczas uzyskiwania dostępu do udostępnionego elementu członkowskiego za pośrednictwem wystąpienia może mieć skutki uboczne lub podczas uzyskiwania dostępu do udostępnionego elementu członkowskiego za pośrednictwem zmiennej wystąpienia nie jest po prawej stronie wyrażenia lub jest przekazywany jako parametr. Domyślnie dla nowych projektów jest włączony.

Identyfikator: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Ostrzeżenia dotyczące operatora cyklicznego lub dostępu do właściwości
Generowane, gdy treść rutynowych używa tego samego operatora lub właściwości, w której jest zdefiniowana. Domyślnie dla nowych projektów jest włączony.

ID: 42004 (operator), 42026 (właściwość)

### <a name="function-or-operator-without-return-value-warning"></a>Funkcja lub operator bez ostrzeżenia o wartości zwracanej
Generowane, gdy funkcja lub operator nie ma określonej wartości zwracanej. Obejmuje to pominięcie `Set` do niejawnej zmiennej lokalnej o takiej samej nazwie jak funkcja. Domyślnie dla nowych projektów jest włączony.

ID: 42105 (funkcja), 42016 (operator)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modyfikator przeciążeń używany w ostrzeżeniu modułu
Generowane, `Overloads` gdy jest `Module`używany w . Domyślnie dla nowych projektów jest włączony.

Identyfikator: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Ostrzeżenia o zduplikowanych lub nakładających się blokach połowowych
Generowane, `Catch` gdy blok nigdy nie zostanie `Catch` osiągnięty ze względu na jego związek z innymi blokami, które zostały zdefiniowane. Domyślnie dla nowych projektów jest włączony.

ID: 42029, 42031

## <a name="see-also"></a>Zobacz też

- [Typy błędów](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Spróbuj... Złapać... Wreszcie oświadczenie](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Strona kompilacji, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Ostrzeżenia kompilatora, które są domyślnie wyłączone](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
