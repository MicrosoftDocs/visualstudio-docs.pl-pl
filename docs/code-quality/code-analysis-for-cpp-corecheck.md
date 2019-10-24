---
title: C++Informacje dotyczące najważniejszych wskazówek dotyczących sprawdzania
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5fe14c1bcb2b375a104a928513134b1789d437
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745965"
---
# <a name="c-core-guidelines-checker-reference"></a>C++Informacje dotyczące najważniejszych wskazówek dotyczących sprawdzania

Ta sekcja zawiera C++ listę najważniejszych wskazówek dotyczących sprawdzania. Aby uzyskać informacje na temat analizy kodu, zobacz [/analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis) i [Szybki Start: Analiza kodu CC++/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Niektóre ostrzeżenia należy do więcej niż jednej grupy, a nie wszystkie ostrzeżenia zawierają kompletny temat odwołania.

## <a name="owner_pointer-group"></a>Grupa OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) Zwracaj obiekt w zakresie, a nie przydzielono sterty, jeśli ma on konstruktora przenoszenia. Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) Zresetuj lub jawnie Usuń właściciela \<T > wskaźnik "% variable%". Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) Nie usuwaj \<T właściciela >, które mogą być w nieprawidłowym stanie. Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) Nie przypisuj do elementu Owner \<T >, który może być w prawidłowym stanie. Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) Nie przypisuj wskaźnika pierwotnego do elementu Owner \<T >. Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Preferuj obiekty w zakresie, nie należy niepotrzebnie przydzielać sterty. Zobacz [ C++ podstawowe wytyczne R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol "% symbol%" nigdy nie jest testowany pod kątem wartości null, może być oznaczony jako NOT_NULL. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% symbol%" nie jest testowany pod kątem wartości null we wszystkich ścieżkach. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Typ wyrażenia "% Expr%" jest już GSL:: NOT_NULL. Nie sprawdzaj go pod kątem wartości null. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Grupa RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) Nie przypisuj wyniku alokacji lub wywołania funkcji z właścicielem \<T > wartości zwracanej do wskaźnika pierwotnego; Zamiast tego użyj \<T właściciela >. Zobacz [ C++ podstawowe wytyczne I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) Nie usuwaj wskaźnika pierwotnego, który nie jest właścicielem \<T >. Zobacz [ C++ podstawowe wytyczne I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   zwracać obiektu w zakresie, a nie przydziału sterty, jeśli ma Konstruktor przenoszenia. Zobacz [ C++ podstawowe wytyczne R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) Unikaj opcji malloc () i Free (), Preferuj metodę nothrow New with Delete. Zobacz [ C++ podstawowe wytyczne R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Unikaj jawnego wywoływania funkcji New i DELETE, zamiast tego użyj std:: make_unique \<T >. Zobacz [ C++ podstawowe wytyczne R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol "% symbol%" nigdy nie jest testowany pod kątem wartości null, może być oznaczony jako NOT_NULL. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% symbol%" nie jest testowany pod kątem wartości null we wszystkich ścieżkach. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Typ wyrażenia "% Expr%" jest już GSL:: NOT_NULL. Nie sprawdzaj go pod kątem wartości null. Zobacz [ C++ podstawowe wytyczne F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) Nie używaj arytmetyki wskaźnika. Zamiast tego użyj zakresu. Zobacz [ C++ podstawowe wytyczne dotyczące zakresu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Wyrażenie "% Expr%": brak tablicy do wskaźnika. Zobacz [ C++ granice podstawowych wytycznych. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Grupa UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) Parametr "% parameter%" jest odwołaniem do `const` unikatowego wskaźnika, zamiast tego należy użyć const T * lub const & T. Zobacz [ C++ podstawowe wytyczne R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) Parametr "% parameter%" jest odwołaniem do unikatowego wskaźnika i nigdy nie jest ponownie przypisywany ani resetowany, zamiast tego należy użyć T * lub T &. Zobacz [ C++ podstawowe wytyczne R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Przenieś, skopiuj, ponownie Przypisz lub zresetuj lokalny wskaźnik inteligentny "% symbol%". Zobacz [ C++ podstawowe wytyczne R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parametr inteligentnego wskaźnika "% symbol%" jest używany tylko w celu uzyskania dostępu do zawartego wskaźnika. Zamiast tego należy użyć T * lub T &. Zobacz [ C++ podstawowe wytyczne R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Grupa SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Przenieś, skopiuj, ponownie Przypisz lub zresetuj lokalny wskaźnik inteligentny "% symbol%". Zobacz [ C++ podstawowe wytyczne R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parametr inteligentnego wskaźnika "% symbol%" jest używany tylko w celu uzyskania dostępu do zawartego wskaźnika. Zamiast tego należy użyć T * lub T &. Zobacz [ C++ podstawowe wytyczne R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) Parametr udostępnionego wskaźnika "% symbol%" jest przenoszona przez odwołanie rvalue. Zamiast tego należy przekazać wartość. Zobacz [ C++ podstawowe wytyczne R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) Parametr udostępnionego wskaźnika "% symbol%" jest przenoszona przez odwołanie i nie jest resetowany ani ponownie przypisany. Zamiast tego należy użyć T * lub T &. Zobacz [ C++ podstawowe wytyczne R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Parametr wspólnego wskaźnika "% symbol%" nie został skopiowany ani przeniesiony. Zamiast tego należy użyć T * lub T &. Zobacz [ C++ podstawowe wytyczne R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Grupa deklaracji

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) Inicjator globalny wywołuje funkcję non-constexpr "% symbol%". Zobacz [ C++ podstawowe wytyczne I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) Globalny inicjator uzyskuje dostęp do obiektu zewnętrznego "% symbol%". Zobacz [ C++ podstawowe wytyczne I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Unikaj nienazwanych obiektów z niestandardowym konstruowaniem i zniszczeniem. Zobacz [es. 84: nie (spróbuj) zadeklarować zmienną lokalną bez nazwy](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Grupa klas

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Jeśli zdefiniujesz lub usuwasz operację domyślną w typie "% symbol%", Zdefiniuj lub usuń je wszystkie. Zobacz [ C++ podstawowe wytyczne C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) Funkcja "% symbol%" powinna być oznaczona przy użyciu elementu "override". Zobacz [C. 128: funkcje wirtualne powinny określać dokładnie jeden z elementów wirtualnych, przesłonięcia lub Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) Funkcja "% symbol_1%" ukrywa niewirtualną funkcję "% symbol_2%". Zobacz [ C++ podstawowe wytyczne C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) Funkcja "% symbol%" powinna określać dokładnie jeden z elementów "Virtual", "override" lub "Final". Zobacz [C. 128: funkcje wirtualne powinny określać dokładnie jeden z elementów wirtualnych, przesłonięcia lub Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md) Typ "% symbol%" z funkcją wirtualną wymaga publicznego destruktora wirtualnego lub chronionego. Zobacz [ C++ podstawowe wytyczne C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) W celu przesłaniania destruktora nie należy używać jawnych specyfikatorów "override" ani "Virtual". Zobacz [C. 128: funkcje wirtualne powinny określać dokładnie jeden z elementów wirtualnych, przesłonięcia lub Final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>Grupa typów

[C26437 DONT_SLICE](C26437.md) Nie używaj wycinków. Zobacz [ C++ podstawowe wytyczne es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Grupa stylów

[C26438 NO_GOTO](C26438.md) Należy unikać `goto`. Zobacz [ C++ podstawowe wytyczne es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupa funkcji

[C26439 SPECIAL_NOEXCEPT](C26439.md) Ten rodzaj funkcji może nie zostać zgłoszony. Zadeklaruj `noexcept`. Zobacz [ C++ podstawowe wytyczne F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) Funkcja "% symbol%" może być zadeklarowana `noexcept`. Zobacz [ C++ podstawowe wytyczne F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) Funkcja jest zadeklarowana **noexcept** , ale wywołuje funkcję, która może zgłaszać wyjątki.
Zobacz [ C++ podstawowe wytyczne: F. 6: Jeśli funkcja nie może zgłosić, zadeklaruj ją noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupa WSPÓŁBIEŻNości

[C26441 NO_UNNAMED_GUARDS](C26441.md) Obiekty Guard muszą mieć nazwę. Zobacz [ C++ podstawowe wytyczne CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Stała Grupa

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) Argument odwołania "% argument%" dla funkcji "% Function%" można oznaczyć jako `const`. Zobacz [ C++ podstawowe wytyczne con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): argument wskaźnika "% argument%" dla funkcji "% Function%" może być oznaczony jako wskaźnik do `const`. Zobacz [ C++ podstawowe wytyczne con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) Wartość wskazywana przez "% variable%" jest przypisywana tylko raz, oznacz ją jako wskaźnik do `const`. Zobacz [ C++ podstawowe wytyczne con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) Elementy tablicy "% Array%" są przypisywane tylko raz, Oznacz elementy `const`. Zobacz [ C++ podstawowe wytyczne con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) Wartości wskazywane przez elementy tablicy "% Array%" są przypisywane tylko raz, Oznacz elementy jako wskaźnik do `const`. Zobacz [ C++ podstawowe wytyczne con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) Zmienna "% variable%" jest przypisywana tylko raz, oznacz ją jako `const`. Zobacz [ C++ podstawowe wytyczne con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) Ta funkcja% Function% może być oznaczona `constexpr`, jeśli pożądane jest Szacowanie czasu kompilacji. Zobacz [ C++ podstawowe wytyczne F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) To wywołanie funkcji% Function% może używać `constexpr`, jeśli pożądane jest Szacowanie czasu kompilacji. Zobacz [ C++ podstawowe wytyczne con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Grupa typów

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) Nie używaj `const_cast` do rzutowania `const`. `const_cast` nie jest wymagana; nie jest usuwana stała lub lotna w ramach tej konwersji. Zobacz [ C++ podstawowe wytyczne typu. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) Nie używaj `static_cast` rzutowań. Rzutowanie z typu polimorficznego powinno używać dynamic_cast. Zobacz [ C++ podstawowe zasady typu. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) Nie używaj `reinterpret_cast`. Rzutowanie z wartości void * może używać `static_cast`. Zobacz [ C++ podstawowe zasady typu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) Nie należy używać `static_cast` do konwersji arytmetycznych. Użyj inicjowania nawiasów klamrowych, GSL:: narrow_cast lub GSL:: narow. Zobacz [ C++ podstawowe zasady typu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) Nie wykonuj rzutowania między typami wskaźnika, w których typ źródłowy i typ docelowy są takie same. Zobacz [ C++ podstawowe zasady typu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) Nie wykonuj rzutowania między typami wskaźnika, gdy konwersja może być niejawna. Zobacz [ C++ podstawowe zasady typu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) Nie należy używać funkcji rzutowania w stylu języka C. Zobacz [ C++ podstawowe wytyczne es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) Nie używaj `reinterpret_cast`. Zobacz [ C++ podstawowe zasady typu. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) Nie używaj `static_cast` rzutowań. Zobacz [ C++ podstawowe zasady typu. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) Nie używaj `const_cast` do rzutowania `const`. Zobacz [ C++ podstawowe wytyczne typu. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) Nie używaj rzutowania w stylu języka C. Zobacz [ C++ podstawowe wytyczne typu. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Zmienna "% variable%" jest niezainicjowana. Zawsze Inicjuj obiekt. Zobacz [ C++ podstawowe zasady typu. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Zmienna "% variable%" jest niezainicjowana. Zawsze Inicjuj zmienną członkowską. Zobacz [ C++ podstawowe wytyczne typu. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupa granic

[C26446 USE_GSL_AT](c26446.md) Wolisz używać `gsl::at()` zamiast niesprawdzonego operatora indeksu. Zobacz [ C++ podstawowe wytyczne: bounds. 4: nie używaj funkcji i typów, które nie są powiązane z biblioteką standardową](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Nie używaj arytmetyki wskaźnika. Zamiast tego użyj zakresu. Zobacz [ C++ granice podstawowych wytycznych. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) Indeksuj do tablic przy użyciu wyrażeń stałych. Zobacz [ C++ granice podstawowych wytycznych. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) Wartość% Value% jest poza granicami (0,% powiązano%) zmiennej "% variable%". Indeksuj do tablic przy użyciu wyrażeń stałych, które znajdują się w granicach tablicy. Zobacz [ C++ granice podstawowych wytycznych. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Wyrażenie "% Expr%": brak tablicy do wskaźnika. Zobacz [ C++ granice podstawowych wytycznych. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupa GSL

[C26445 NO_SPAN_REF](c26445.md) Odwołanie do `gsl::span` lub `std::string_view` może wskazywać na problem z okresem istnienia.
Zobacz [ C++ podstawowe wytyczne GSL. View: widoki](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) Wolisz używać `gsl::at()` zamiast niesprawdzonego operatora indeksu. Zobacz [ C++ podstawowe wytyczne: bounds. 4: nie używaj funkcji i typów, które nie są powiązane z biblioteką standardową](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md) Rozważ użycie `gsl::finally`, jeśli ostateczna akcja jest zamierzona. Zobacz [ C++ podstawowe wytyczne: GSL. util: Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) `gsl::span` 
 lub `std::string_view` utworzony na podstawie elementu tymczasowego będzie nieprawidłowy, gdy tymczasowe jest unieważnione. Zobacz [ C++ podstawowe wytyczne: GSL. View: views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Przestarzałe ostrzeżenia

Następujące ostrzeżenia są obecne w wczesnej fazie z zestawem najważniejszych wytycznych, ale są teraz przestarzałe i można je bezpiecznie zignorować. Ostrzeżenia są zastąpione ostrzeżeniami z powyższej listy.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Zobacz także
[Korzystanie z C++ funkcji sprawdzania podstawowych wytycznych](using-the-cpp-core-guidelines-checkers.md)
