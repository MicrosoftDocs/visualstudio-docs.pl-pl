---
title: W języku C++ podstawowych wytycznych dotyczących sprawdzania odwołania
ms.date: 03/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: c11386dcd742e64737a4b06f2db9f55145f535d7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053389"
---
# <a name="c-core-guidelines-checker-reference"></a>W języku C++ podstawowych wytycznych dotyczących sprawdzania odwołania

W tej sekcji przedstawiono podstawowe sprawdzanie wytyczne dotyczące języka C++ ostrzeżenia. Aby uzyskać informacje o analizie kodu, zobacz [/ analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis) i [— Szybki Start: analiza kodu C/c++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Ostrzeżenia należeć do więcej niż jednej grupy, a nie wszystkie ostrzeżenia mają temat pełną dokumentację.

## <a name="ownerpointer-group"></a>Grupa OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) zwracaj obiekt o określonym zakresie, a nie przydzielony w stercie, jeśli ma on konstruktora przenoszenia. Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) Zresetuj lub jawnie Usuń właściciela\<T > wskaźnik "% Zmienna %". Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) nie usuwaj elementu owner\<T > może to być w nieprawidłowym stanie. Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) nie przypisuj do elementu owner\<T > może to być w nieprawidłowym stanie. Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) nie przypisuj wskaźnika podstawowego do elementu owner\<T >. Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Preferuj obiekty w zakresie, nie przydzielaj niepotrzebnie w stercie. Zobacz [C++ w podstawowych wytycznych dotyczących R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol "% symbolu %" nigdy nie jest testowany pod kątem, może być oznaczony jako not_null. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% symbolu %" nie jest testowany dla pod we wszystkich ścieżkach. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ wyrażenia "% wyrażenie %" jest już gsl::not_null. Nie Testuj go pod kątem. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>Grupa RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) nie przypisuj wyniku alokacji lub wywołania funkcji z właścicielem\<T > zwraca wartość do wskaźnika podstawowego; Użyj właściciela\<T > zamiast tego. Zobacz [C++ w podstawowych wytycznych dotyczących I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) nie usuwaj wskaźnika pierwotnego, który nie jest właścicielem\<T >. Zobacz [C++ w podstawowych wytycznych dotyczących I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   zwracaj obiekt o określonym zakresie, a nie przydzielony w stercie, jeśli ma on konstruktora przenoszenia. Zobacz [C++ w podstawowych wytycznych dotyczących R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) uniknięcie malloc() i free(), preferowana wersja nothrow nowe za pomocą usuwania. Zobacz [C++ w podstawowych wytycznych dotyczących R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) unikać wywoływania nowych i Usuń jawnie, użyj opcji std::make_unique\<T > zamiast tego. Zobacz [C++ w podstawowych wytycznych dotyczących R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol "% symbolu %" nigdy nie jest testowany pod kątem, może być oznaczony jako not_null. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% symbolu %" nie jest testowany dla pod we wszystkich ścieżkach. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ wyrażenia "% wyrażenie %" jest już gsl::not_null. Nie Testuj go pod kątem. Zobacz [C++ w podstawowych wytycznych dotyczących F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) nie używaj arytmetyki wskaźnika. W zamian użyj zakresu. Zobacz [C++ podstawowe wytyczne Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Wyrażenie "% wyrażenie %": nie zanikania tablicy do wskaźnika. Zobacz [C++ podstawowe wytyczne Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>Grupa UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) parametru "% parametr %" jest odwołaniem do `const` unikatowego wskaźnika elementu const T * lub const T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) parametr "% parametr %" jest odwołanie do unikatowego wskaźnika i nigdy nie jest on ponownie przypisywany ani resetowany, użyj T * lub T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) przenoszenie, kopiowanie, ponowne przypisanie lub Resetuj lokalny wskaźnik inteligentny "% symbolu %". Zobacz [C++ w podstawowych wytycznych dotyczących R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parametr wskaźnika inteligentnego "% symbolu %" umożliwia tylko dostęp do zawartych wskaźnika. Użyj T * lub T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>Grupa SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) przenoszenie, kopiowanie, ponowne przypisanie lub Resetuj lokalny wskaźnik inteligentny "% symbolu %". Zobacz [C++ w podstawowych wytycznych dotyczących R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parametr wskaźnika inteligentnego "% symbolu %" umożliwia tylko dostęp do zawartych wskaźnika. Użyj T * lub T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parametru wskaźnika Shared "% symbolu %" jest przekazywany przez odwołanie rvalue. Zamiast tego Przekaż przez wartość. Zobacz [C++ w podstawowych wytycznych dotyczących R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parametru wskaźnika Shared "% symbolu %" jest przekazywany przez odwołanie i nie zresetować lub ponownie przypisać. Użyj T * lub T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parametru wskaźnika Shared "% symbolu %" nie jest kopiowane lub przeniesiony. Użyj T * lub T &. Zobacz [C++ w podstawowych wytycznych dotyczących R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Grupy deklaracji

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) innicjator globalny wywołuje funkcję-constexpr "% symbolu %". Zobacz [C++ w podstawowych wytycznych dotyczących I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inicjator globalny uzyskuje dostęp do obiektu extern "% symbolu %". Zobacz [C++ w podstawowych wytycznych dotyczących I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Unikaj nienazwanych obiektów z niestandardowym konstruowaniem i niszczeniem. Zobacz [ES.84: nie (należy próbować) zadeklarować zmienną lokalną bez nazwy](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Klasa grupy

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) zdefiniuj lub usuń wszelkich operacji domyślną w typie "% symbolu %", zdefiniuj lub usunąć je wszystkie. Zobacz [C++ w podstawowych wytycznych dotyczących C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) funkcji "% % symbol" powinien być oznaczony przez "override". Zobacz [C.128: funkcji wirtualnych powinna określać dokładnie jeden wirtualny, zastąpienie, lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) funkcji "% symbol_1%" ukrywa funkcję niewirtualną "% symbol_2%". Zobacz [C++ w podstawowych wytycznych dotyczących C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funkcji "% % symbol" powinna określać dokładnie jeden "virtual", "override" lub "final". Zobacz [C.128: funkcji wirtualnych powinna określać dokładnie jeden wirtualny, zastąpienie, lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) typ "% symbolu %" z funkcją wirtualną wymaga obu publicznego lub chronionego destruktora niewirtualne. Zobacz [C++ w podstawowych wytycznych dotyczących C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) przesłanianie destruktora nie należy używać jawnych "override" ani "virtual" specyfikatorów. Zobacz [C.128: funkcji wirtualnych powinna określać dokładnie jeden wirtualny, zastąpienie, lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Typ grupy

[C26437 DONT_SLICE](C26437.md) nie używaj wycinków. Zobacz [C++ w podstawowych wytycznych dotyczących ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Styl grupy

[C26438 NO_GOTO](C26438.md) uniknąć `goto`. Zobacz [C++ w podstawowych wytycznych dotyczących ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupy — funkcja

[C26439 SPECIAL_NOEXCEPT](C26439.md) ten rodzaj funkcji może nie zgłaszać. Zadeklaruj go `noexcept`. Zobacz [C++ w podstawowych wytycznych dotyczących F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) funkcji "% % symbol" mogą być deklarowane `noexcept`. Zobacz [C++ w podstawowych wytycznych dotyczących F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) zadeklarowano funkcję **noexcept** , ale wywołuje funkcję, która może zgłaszać wyjątki.
Zobacz [podstawowych wytycznych dotyczących języka C++: F.6: Jeśli Twoja funkcja nie może zgłaszać, Zadeklaruj go noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupa WSPÓŁBIEŻNOŚCI

[C26441 NO_UNNAMED_GUARDS](C26441.md) obiekty Guard musi mieć nazwę. Zobacz [C++ podstawowe wytyczne cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST grupy

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) argument odwołania "% argumentu %" dla funkcji "% funkcji %" może być oznaczony jako `const`. Zobacz [C++ podstawowe wytyczne con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): argument wskaźnika "% argumentu %" dla funkcji "% funkcji %" może być oznaczony jako wskaźnik do `const`. Zobacz [C++ podstawowe wytyczne con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) wartość wskazywana przez "% Zmienna %" jest przypisywana tylko raz, oznacz ją jako wskaźnik do `const`. Zobacz [C++ podstawowe wytyczne con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) elementów tablicy "% tablicy %" są przypisywane tylko raz; Oznacz elementy `const`. Zobacz [C++ podstawowe wytyczne con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) wartości wskazywane przez elementy tablicy "% tablicy %" są przypisywane tylko raz; Oznacz elementy jako wskaźnik do `const`. Zobacz [C++ podstawowe wytyczne con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) zmiennej "% Zmienna %" jest przypisywana tylko raz, oznacz ją jako `const`. Zobacz [C++ podstawowe wytyczne con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) tej funkcji % funkcję można oznaczyć `constexpr` jeśli pożądane jest szacowanie czasu kompilacji. Zobacz [C++ w podstawowych wytycznych dotyczących F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) można użyć tej funkcji wywołanie % funkcji `constexpr` jeśli pożądane jest szacowanie czasu kompilacji. Zobacz [C++ podstawowe wytyczne con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ grupy

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) nie używaj `const_cast` do oddać `const`. `const_cast` nie jest wymagana. Ta konwersja nie powoduje usunięcia stałości ani zmienności. Zobacz [C++ podstawowe wytyczne Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) nie używaj `static_cast` rzutowań. Rzutowanie z poziomu typu polimorficznego powinno używać elementu dynamic_cast. Zobacz [C++ podstawowe wytyczne Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) nie używaj `reinterpret_cast`. Rzutowanie z elementu void * może korzystać `static_cast`. Zobacz [C++ podstawowe wytyczne Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) nie używaj `static_cast` dla konwersji arytmetycznych. Użyj nawiasów klamrowych, gsl::narrow_cast lub gsl::narow. Zobacz [C++ podstawowe wytyczne Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) nie wykonuj rzutowania między typami wskaźnika, gdy typ źródłowy i typ docelowy są takie same. Zobacz [C++ podstawowe wytyczne Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) nie wykonuj rzutowania między typami wskaźnika, gdy przekształcenie mogłoby być niejawne. Zobacz [C++ podstawowe wytyczne Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) nie należy używać funkcji stylu C rzutowania. Zobacz [C++ w podstawowych wytycznych dotyczących ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) nie używaj `reinterpret_cast`. Zobacz [C++ podstawowe wytyczne Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) nie używaj `static_cast` rzutowań. Zobacz [C++ podstawowe wytyczne Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) nie używaj `const_cast` do oddać `const`. Zobacz [C++ podstawowe wytyczne Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) nie używaj rzutowań w stylu języka C. Zobacz [C++ podstawowe wytyczne Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) zmiennej "% Zmienna %" nie został zainicjowany. Zawsze Inicjuj obiekt. Zobacz [C++ podstawowe wytyczne Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) zmiennej "% Zmienna %" nie został zainicjowany. Zawsze Inicjuj zmienną elementu członkowskiego. Zobacz [C++ podstawowe wytyczne Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupy granic

[C26446 USE_GSL_AT](c26446.md) wolą używać `gsl::at()` zamiast niesprawdzonego operatora. Zobacz [podstawowych wytycznych dotyczących języka C++: Bounds.4: nie należy używać funkcji w standardowej bibliotece oraz typy, które nie są sprawdzane przez granice](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Nie używaj arytmetyki wskaźnika. W zamian użyj zakresu. Zobacz [Bounds.1 wytyczne dotyczące podstawowych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) tylko Indeksuj do tablic przy użyciu wyrażeń stałych. Zobacz [Bounds.2 wytyczne dotyczące podstawowych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) wartość % wartość znajduje się poza granicami (0, powiązanej %) zmiennej "% Zmienna %". Tylko Indeksuj do tablic przy użyciu wyrażeń stałych, które znajdują się w granicach tablicy. Zobacz [Bounds.2 wytyczne dotyczące podstawowych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) wyrażenie "% wyrażenie %": nie zanikania tablicy do wskaźnika. Zobacz [Bounds.3 wytyczne dotyczące podstawowych języka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupa GSL

[C26445 NO_SPAN_REF](c26445.md) odwołanie do `gsl::span` lub `std::string_view` może wskazywać na problem z okresem istnienia.
Zobacz [C++ podstawowe wytyczne GSL.view: widoków](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) wolą używać `gsl::at()` zamiast niesprawdzonego operatora. Zobacz [podstawowych wytycznych dotyczących języka C++: Bounds.4: nie należy używać funkcji w standardowej bibliotece oraz typy, które nie są sprawdzane przez granice](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) rozważ `gsl::finally` gdy ostateczna akcja jest przeznaczony. Zobacz [C++ podstawowych wytycznych dotyczących języka: GSL.util: narzędzia](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` lub `std::string_view` utworzony na podstawie będą nieprawidłowe gdy zostaje unieważniony tymczasowy. Zobacz [C++ podstawowych wytycznych dotyczących języka: GSL.view: widoki](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Przestarzałe ostrzeżenia

Następujące ostrzeżenia są obecne w wczesnych zestaw reguł eksperymentalne modułu sprawdzania podstawowych wytycznych, ale są one przestarzałe i można bezpiecznie zignorować. W przypadku ostrzeżenia są ostrzeżenia na powyższej liście.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Zobacz też
[Za pomocą wytycznych dotyczących języka C++ podstawowe](using-the-cpp-core-guidelines-checkers.md)
