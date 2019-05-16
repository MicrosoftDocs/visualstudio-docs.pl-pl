---
title: Konfigurowanie ostrzeżeń w języku Visual Basic | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3fb723097a3b61508d9f9023d3a2ea1dcdb5f8f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701417"
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurowanie ostrzeżeń w Visual Basic:
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Kompilator zawiera zbiór ostrzeżenia dotyczące kodu, który może powodować błędy czasu wykonywania. Można użyć tych informacji do zapis czyszcząca, szybciej, lepiej kodu za pomocą mniejszej liczby usterek. Na przykład wygenerowanie ostrzeżenia, gdy użytkownik próbuje zainicjować członka zmiennej spowodowało utworzenie nieprzypisanego obiektu zwracanego przez funkcję bez ustawienia zwracanej wartości lub wykonania przez kompilator `Try` bloku błędów w logice przechwytują wyjątki.  
  
 Czasami kompilator jest dodatkowa logika w imieniu użytkownika, dzięki czemu użytkownik może skupić się na wykonywanego zadania, a nie na przewidywanie możliwych błędów. W poprzednich wersjach [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `Option Strict` była używana do ograniczania dodatkowej logiki, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilator udostępnia. Konfigurowanie ostrzeżeń umożliwia ograniczenie tę logikę w bardziej szczegółowy sposób, na poziomie poszczególnych ostrzeżenia.  
  
 Możesz chcieć dostosować swój projekt i Wyłącz ostrzeżenia nie odpowiednie do Twojej aplikacji, włączając inne ostrzeżenia na błędy. Tej stronie wyjaśniamy, jak włączyć poszczególne ostrzeżenia, włączać i wyłączać.  
  
## <a name="turning-warnings-off-and-on"></a>Włączanie i Włącz ostrzeżenia  
 Istnieją dwa różne sposoby konfigurowania ostrzeżenia: można je skonfigurować przy użyciu **projektanta projektu**, lub użyć **/warnaserror** i **/nowarn** opcje kompilatora .  
  
 **Skompilować** karcie **projektanta projektu** strona pozwala na włączenie ostrzeżenia włączać i wyłączać. Wybierz **Wyłącz wszystkie ostrzeżenia** Sprawdź pole, aby wyłączyć wszystkie ostrzeżenia; wybierz **traktowanie wszystkich ostrzeżeń jako błędy** na traktowanie wszystkich ostrzeżeń jako błędy. Poszczególne ostrzeżenia, może być przełączane jako błąd lub ostrzeżenie zgodnie z potrzebami w tabeli.  
  
 Gdy **Option Strict** jest ustawiona na **poza**, **Option Strict** powiązane ostrzeżenia nie może być traktowany niezależnie od siebie nawzajem. Gdy **Option Strict** ustawiono **na**skojarzone ostrzeżenia są traktowane jako błędy, nie ma znaczenia, ich stan jest. Gdy **Option Strict** ustawiono **niestandardowe** , określając `/optionstrict:custom` kompilatora wiersza polecenia **Option Strict** ostrzeżenia mogą być włączane lub wyłączane niezależnie.  
  
 **/Warnaserror** opcji wiersza polecenia kompilatora może również służyć do określenia, czy ostrzeżenia są traktowane jako błędy. Rozdzielana przecinkami listy można dodać do tę opcję, aby określić, które ostrzeżenia powinny być traktowane jako błędy lub ostrzeżenia przy użyciu + lub -. W poniższej tabeli przedstawiono możliwe opcje.  
  
|Opcja wiersza polecenia|Określa|  
|--------------------------|---------------|  
|`/warnaserror+`|Traktuje wszystkie ostrzeżenia jako błędy|  
|`/warnsaserror`-|Nie należy traktować jako ostrzeżenia jako błędy. Domyślnie włączone.|  
|`/warnaserror+:<warning list``>`|Traktuj szczególne ostrzeżenia jako błędy, według ich numer identyfikacyjny błąd na liście rozdzielany przecinkami r.|  
|`/warnaserror-:<warning list>`|Nie Traktuj szczególne ostrzeżenia jako błędy, według ich numer identyfikacyjny błąd na liście rozdzielany przecinkami.|  
|`/nowarn`|Nie zgłaszaj ostrzeżenia.|  
|`/nowarn:<warning list>`|Nie zgłaszaj określone ostrzeżenia, według ich numer identyfikacyjny błąd na liście rozdzielany przecinkami.|  
  
 Lista ostrzeżenie zawiera numery identyfikatorów błędów, ostrzeżeń, które powinny być traktowane jako błędy, które mogą być używane z opcjami wiersza polecenia można włączyć określone ostrzeżenia lub wyłączyć. Jeśli na liście ostrzeżenie zawiera nieprawidłową liczbę, jest zgłaszany błąd.  
  
## <a name="examples"></a>Przykłady  
 Tej tabeli przedstawiono przykłady argumenty wiersza polecenia opisano, jak działa każdy argument.  
  
|Argument|Opis|  
|--------------|-----------------|  
|`vbc /warnaserror`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|  
|`vbc /warnaserror:42024`|Określa, że ostrzeżenie 42024 powinny być traktowane jako błąd.|  
|`vbc /warnaserror:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 powinny być traktowane jako błędy.|  
|`vbc /nowarn`|Określa, że żadne ostrzeżenia nie powinny być raportowane.|  
|`vbc /nowarn:42024`|Określa, że ostrzeżenie 42024 nie powinny być zgłaszane.|  
|`vbc /nowarn:42024,42025`|Określa, czy ostrzeżenia 42024 i 42025 nie powinny być raportowane.|  
  
## <a name="types-of-warnings"></a>Typy ostrzeżenia  
 Poniżej przedstawiono listę ostrzeżeń, które mają być traktowane jako błędy.  
  
### <a name="implicit-conversion-warning"></a>Ostrzeżenie niejawnej konwersji  
 Wygenerowany dla wystąpienia elementu niejawnej konwersji. Nie obejmują one niejawną konwersję z typu wewnętrznego dla liczbowego na ciąg przy użyciu `&` operatora. Domyślne dla nowych projektów jest wyłączona.  
  
 ID: 42016  
  
### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Rozpoznanie późnego wiązania wywołania metody i ostrzeżenie rozpoznawania przeciążenia  
 Generowane w przypadku wystąpienia z późnym wiązaniem. Domyślne dla nowych projektów jest wyłączona.  
  
 ID: 42017  
  
### <a name="operands-of-type-object-warnings"></a>Operandy typu obiektu ostrzeżenia  
 Wygenerowany, gdy argumentów operacji typu `Object` występują, utworzyć błąd `Option Strict On`. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42018 i 42019  
  
### <a name="declarations-require-as-clause-warnings"></a>Deklaracje wymagają ostrzeżenia klauzuli "As"  
 Generowane, gdy zmiennej, funkcji lub brakujących deklaracji właściwości `As` klauzuli czy utworzono błąd `Option Strict On`. Zmienne, które nie mają typu, przypisane są zakłada się, że typ `Object`. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42020 (deklaracja zmiennej), 42021 (deklaracji funkcji) i 42022 (deklaracja właściwości).  
  
### <a name="possible-null-reference-exception-warnings"></a>Ostrzeżenia dotyczące wyjątków możliwe odwołanie o wartości Null  
 Generowane, gdy zmienna jest używana, zanim została do niej przypisana wartość. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42104, 42030  
  
### <a name="unused-local-variable-warning"></a>Nieużywane ostrzeżenie zmiennych lokalnych  
 Generowane, gdy zmienna lokalna jest zadeklarowana, ale nigdy nie jest określone. Domyślna znajduje się na.  
  
 ID: 42024  
  
### <a name="access-of-shared-member-through-instance-variable-warning"></a>Dostęp do elementu członkowskiego udostępnione za pośrednictwem zmiennej ostrzeżenie wystąpienia  
 Generowane podczas uzyskiwania dostępu do udostępnionego elementu członkowskiego przez wystąpienie może mieć efekty uboczne lub podczas uzyskiwania dostępu do udostępnionego elementu członkowskiego za pośrednictwem zmiennej wystąpienia nie jest wyrażeniem po prawej stronie lub jest przekazywany jako parametr. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42025  
  
### <a name="recursive-operator-or-property-access-warnings"></a>Operator rekursywny lub ostrzeżenia dostęp do właściwości  
 Generowane, gdy treść procedury używa tego samego operatora lub właściwości, który jest zdefiniowany w. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42004 (operator), 42026 (właściwość)  
  
### <a name="function-or-operator-without-return-value-warning"></a>Funkcja lub Operator bez ostrzeżenia wartości zwracanej  
 Generowane, gdy funkcja lub operator nie jest zwracana wartość określona. W tym pominięcie `Set` do niejawnego zmiennej lokalnej o nazwie identycznej z nazwą funkcji. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42105 (funkcja), 42016 (operator)  
  
### <a name="overloads-modifier-used-in-a-module-warning"></a>Modyfikator przeciążenia używane w ostrzeżenie modułu  
 Wygenerowany, gdy `Overloads` jest używany w `Module`. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42028  
  
### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Zduplikowany lub nakładający się Catch bloki ostrzeżenia  
 Wygenerowany, gdy `Catch` bloku nigdy nie zostanie osiągnięty z powodu jej relacji z innymi `Catch` bloki, które zostały zdefiniowane. Domyślne dla nowych projektów znajduje się na.  
  
 ID: 42029, 42031  
  
## <a name="see-also"></a>Zobacz też  
 [Okno dialogowe Asystenta wyjątków](../debugger/exception-assistant-dialog-box.md)   
 [Typy błędów](https://msdn.microsoft.com/library/3048aabf-8c97-4e13-9150-853769cb5f6f)   
 [Try... CATCH... Finally — instrukcja](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b)   
 [/ nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83)   
 [/ warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1)   
 [Strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Domyślnie wyłączone ostrzeżenia kompilatora](https://msdn.microsoft.com/library/69809cfb-a38a-4035-b154-283a61938df8)
