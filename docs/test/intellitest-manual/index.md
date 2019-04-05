---
title: Funkcja IntelliTest Reference Manual | Narzędzia do testów firmy Microsoft dla deweloperów
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d7258549b242091737e14e00980447eb48d5e78b
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324802"
---
# <a name="intellitest-reference-manual"></a>Funkcja IntelliTest Reference Manual

## <a name="contents"></a>Spis treści

* **[Omówienie programu IntelliTest](introduction.md)**
  - [Hello World programu IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Ograniczenia](introduction.md#limitations)
    * [Nondeterminism](introduction.md#nondeterminism)
    * [Współbieżność](introduction.md#concurrency)
    * [Kod natywny](introduction.md#native-code)
    * [Platforma](introduction.md#platform)
    * [Język](introduction.md#language)
    * [Symbolicznych](introduction.md#symbolic-reasoning)
    * [Ślady stosu niepoprawne](introduction.md#incorrect-stack-traces)
  - [Dalsze informacje](introduction.md#further-reading)

* **[Rozpoczynanie pracy z funkcją IntelliTest](getting-started.md)**
  - [Ważnych atrybutów](getting-started.md#important-attributes)
  - [Ważne statyczne klasy pomocy](getting-started.md#helper-classes)

* **[Generowanie testu](test-generation.md)**
  - [Generatory testu](test-generation.md#test-generators)
  - [Sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  - [Ogólny sparametryzowanych testów jednostkowych](test-generation.md#generic-parameterized)
  - [Zezwalanie na wyjątki](test-generation.md#allowing-exceptions)
  - [Testowanie typy wewnętrzne](test-generation.md#internal-types)
  - [Założenia i potwierdzeń](test-generation.md#assumptions-and-assertions)
  - [Warunek wstępny](test-generation.md#precondition)
  - [Postcondition](test-generation.md#postcondition)
  - [Niepowodzenia testu](test-generation.md#test-failures)
  - [Konfigurowanie i zatrzymywania](test-generation.md#setup-teardown)
  - [Dalsze informacje](test-generation.md#further-reading)

* **[Generowanie danych wejściowych](input-generation.md)**
  - [Moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver)
  - [Pokrycie kodu dynamiczne](input-generation.md#dynamic-code-coverage)
  - [Liczby całkowite i wartości zmiennoprzecinkowe](input-generation.md#integers-and-floats)
  - [Obiekty](input-generation.md#objects)
  - [Utworzenie wystąpienia istniejących klas](input-generation.md#existing-classes)
  - [Widoczność](input-generation.md#visibility)
  - [Mocks sparametryzowane](input-generation.md#parameterized-mocks)
  - [Struktury](input-generation.md#structs)
  - [Tablice i ciągi](input-generation.md#arrays-and-strings)
  - [Uzyskiwanie dodatkowych danych wejściowych](input-generation.md#additional-inputs)
  - [Dalsze informacje](input-generation.md#further-reading)

* **[Wiązania eksploracji](exploration-bounds.md)**
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

* **[Kaskadowy model ustawień](settings-waterfall.md)**

* **[Statyczne klasy pomocy](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Ostrzeżenia i błędy](warnings-and-errors.md)**
  - [Przekroczono MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [Przekroczono MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [Przekroczono MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [Przekroczono MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [Przekroczono MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [Przekroczono MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests exceeded](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nie można skonkretyzować rozwiązania](warnings-and-errors.md#cannot-concretize-solution)
  - [Potrzebna pomoc do konstruowania obiektu](warnings-and-errors.md#help-construct)
  - [Potrzebujesz pomocy w celu odnalezienia typów](warnings-and-errors.md#help-types)
  - [Można używać typu złamać](warnings-and-errors.md#usable-type-guessed)
  - [Nieoczekiwany błąd podczas eksploracji](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Niezinstrumentowanej metody o nazwie](warnings-and-errors.md#uninstrumented-method-called)
  - [Zewnętrzne metodę o nazwie](warnings-and-errors.md#external-method-called)
  - [Niemożliwy do Instrumentacji metodę o nazwie](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problem z testowalnością](warnings-and-errors.md#testability-issue)
  - [Ograniczenie](warnings-and-errors.md#limitation)
  - [Zaobserwowana niezgodność wywołań](warnings-and-errors.md#observed-call-mismatch)
  - [Wartość przechowywana w polu statycznym](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).