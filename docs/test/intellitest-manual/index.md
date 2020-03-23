---
title: Podręcznik dotyczący funkcji IntelliTest | Narzędzia firmy Microsoft do testowania dla deweloperów
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b1c40412da096db63da87e04711cdc1a95b5cc84
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "75591622"
---
# <a name="intellitest-reference-manual"></a>Podręcznik dotyczący funkcji IntelliTest

## <a name="contents"></a>Spis treści

* **[Omówienie funkcji IntelliTest](introduction.md)**
  - [Przykład Witaj Świecie w funkcji IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Ograniczenia](introduction.md#limitations)
    * [Niedeterminizm](introduction.md#nondeterminism)
    * [Współbieżność](introduction.md#concurrency)
    * [Kod natywny](introduction.md#native-code)
    * [Platforma](introduction.md#platform)
    * [Język](introduction.md#language)
    * [Wnioskowanie symboliczne](introduction.md#symbolic-reasoning)
    * [Nieprawidłowe ślady stosu](introduction.md#incorrect-stack-traces)
  - [Dalsze informacje](introduction.md#further-reading)

* **[Wprowadzenie do funkcji IntelliTest](getting-started.md)**
  - [Ważne atrybuty](getting-started.md#important-attributes)
  - [Ważne statyczne klasy pomocnicze](getting-started.md#helper-classes)

* **[Generowanie testów](test-generation.md)**
  - [Generatory testów](test-generation.md#test-generators)
  - [Sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  - [Ogólne sparametryzowane testy jednostkowe](test-generation.md#generic-parameterized)
  - [Zezwalanie na wyjątki](test-generation.md#allowing-exceptions)
  - [Testowanie typów wewnętrznych](test-generation.md#internal-types)
  - [Założenia i potwierdzenia](test-generation.md#assumptions-and-assertions)
  - [Warunek wstępny](test-generation.md#precondition)
  - [Warunek końcowy](test-generation.md#postcondition)
  - [Niepowodzenia testów](test-generation.md#test-failures)
  - [Konfigurowanie i usuwanie](test-generation.md#setup-teardown)
  - [Dalsze informacje](test-generation.md#further-reading)

* **[Generowanie danych wejściowych](input-generation.md)**
  - [Narzędzie do rozwiązywania ograniczeń](input-generation.md#constraint-solver)
  - [Dynamiczne pokrycie kodu](input-generation.md#dynamic-code-coverage)
  - [Wartości całkowite i zmiennoprzecinkowe](input-generation.md#integers-and-floats)
  - [Obiekty](input-generation.md#objects)
  - [Tworzenie wystąpień istniejących klas](input-generation.md#existing-classes)
  - [Widoczność](input-generation.md#visibility)
  - [Sparametryzowane makiety](input-generation.md#parameterized-mocks)
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

* **[Statyczne klasy pomocnicze](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Ostrzeżenia i błędy](warnings-and-errors.md)**
  - [Przekroczono wartość MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [Przekroczono wartość MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [Przekroczono wartość MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [Przekroczono wartość MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [Przekroczono wartość MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [Przekroczono wartość MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [Przekroczono wartość MaxRunsWithoutNewTests](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nie można skonkretyzować rozwiązania](warnings-and-errors.md#cannot-concretize-solution)
  - [Potrzebna jest pomoc przy konstruowaniu obiektu](warnings-and-errors.md#help-construct)
  - [Potrzebna jest pomoc przy znajdowaniu typów](warnings-and-errors.md#help-types)
  - [Odgadnięto typ, którego można użyć](warnings-and-errors.md#usable-type-guessed)
  - [Nieoczekiwany błąd podczas eksploracji](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Wywołano niezinstrumentowaną metodę](warnings-and-errors.md#uninstrumented-method-called)
  - [Wywołano metodę zewnętrzną](warnings-and-errors.md#external-method-called)
  - [Wywołano metodę bez możliwości instrumentacji](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problem z testowalnością](warnings-and-errors.md#testability-issue)
  - [Ograniczenie](warnings-and-errors.md#limitation)
  - [Zaobserwowano niezgodność wywołań](warnings-and-errors.md#observed-call-mismatch)
  - [Wartość przechowywana w polu statycznym](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
