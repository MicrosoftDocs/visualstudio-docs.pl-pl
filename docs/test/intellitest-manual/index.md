---
title: Ręczne odwołanie do IntelliTest | Narzędzia Microsoft Developer Test Tools
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 97b28c2810b59465c6d5ac682e95e25b324a95a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653200"
---
# <a name="intellitest-reference-manual"></a>Podręcznik referencyjny IntelliTest

## <a name="contents"></a>Spis treści

* **[Przegląd IntelliTest](introduction.md)**
  - [Hello world IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Ograniczenia](introduction.md#limitations)
    * [Nieustalenia](introduction.md#nondeterminism)
    * [Współbieżność](introduction.md#concurrency)
    * [Kod natywny](introduction.md#native-code)
    * [Platformach](introduction.md#platform)
    * [Język](introduction.md#language)
    * [Powód symboliczny](introduction.md#symbolic-reasoning)
    * [Nieprawidłowe ślady stosu](introduction.md#incorrect-stack-traces)
  - [Dalsze odczytywanie](introduction.md#further-reading)

* **[Wprowadzenie do IntelliTest](getting-started.md)**
  - [Ważne atrybuty](getting-started.md#important-attributes)
  - [Ważne klasy pomocników statycznych](getting-started.md#helper-classes)

* **[Generowanie testu](test-generation.md)**
  - [Generatory testów](test-generation.md#test-generators)
  - [Sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  - [Ogólne sparametryzowane testy jednostkowe](test-generation.md#generic-parameterized)
  - [Zezwalanie na wyjątki](test-generation.md#allowing-exceptions)
  - [Testowanie typów wewnętrznych](test-generation.md#internal-types)
  - [Założenia i potwierdzenia](test-generation.md#assumptions-and-assertions)
  - [Warunek wstępny](test-generation.md#precondition)
  - [Błąd warunku końcowego](test-generation.md#postcondition)
  - [Błędy testu](test-generation.md#test-failures)
  - [Instalacja i rozbicie](test-generation.md#setup-teardown)
  - [Dalsze odczytywanie](test-generation.md#further-reading)

* **[Generowanie danych wejściowych](input-generation.md)**
  - [Funkcja ograniczeń — Solver](input-generation.md#constraint-solver)
  - [Dynamiczne pokrycie kodu](input-generation.md#dynamic-code-coverage)
  - [Liczby całkowite i zmiennoprzecinkowe](input-generation.md#integers-and-floats)
  - [Obiekty](input-generation.md#objects)
  - [Tworzenie wystąpień istniejących klas](input-generation.md#existing-classes)
  - [Propagowan](input-generation.md#visibility)
  - [Makiety sparametryzowane](input-generation.md#parameterized-mocks)
  - [Struktury](input-generation.md#structs)
  - [Tablice i ciągi](input-generation.md#arrays-and-strings)
  - [Uzyskiwanie dodatkowych danych wejściowych](input-generation.md#additional-inputs)
  - [Dalsze odczytywanie](input-generation.md#further-reading)

* **[Granice eksploracji](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Słownik atrybutów](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Ustawienia kaskadowe ustawień](settings-waterfall.md)**

* **[Statyczne klasy pomocnika](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [Funkcja PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Ostrzeżenia i błędy](warnings-and-errors.md)**
  - [Przekroczono MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [Przekroczono MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [Przekroczono MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [Przekroczono MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [Przekroczono MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [Przekroczono MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [Przekroczono MaxRunsWithoutNewTests](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nie można skonkretyzować rozwiązania](warnings-and-errors.md#cannot-concretize-solution)
  - [Potrzebna pomoc dla konstruowania obiektu](warnings-and-errors.md#help-construct)
  - [Potrzebujesz pomocy w znalezieniu typów](warnings-and-errors.md#help-types)
  - [Typ możliwych do użycia](warnings-and-errors.md#usable-type-guessed)
  - [Nieoczekiwany błąd podczas eksploracji](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException —](warnings-and-errors.md#targetinvocationexception)
  - [Wywołana metoda bez Instrumentacji](warnings-and-errors.md#uninstrumented-method-called)
  - [Wywołana metoda zewnętrzna](warnings-and-errors.md#external-method-called)
  - [Wywołana metoda bezinstrumentowa](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problem z testowaniem](warnings-and-errors.md#testability-issue)
  - [Bieg](warnings-and-errors.md#limitation)
  - [Obserwowana niezgodność wywołań](warnings-and-errors.md#observed-call-mismatch)
  - [Wartość przechowywana w polu statycznym](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Masz opinię?

Publikuj swoje pomysły i żądania funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).