---
title: Dynamiczne wykonywanie symboliczne | Narzędzie testowe dla deweloperów Microsoft IntelliTest
description: Dowiedz się, jak IntelliTest generuje dane wejściowe dla sparametryzowanych testów jednostkowych przez analizowanie warunków gałęzi w programie.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 1ae12d6b7465e7b0542c987aae9fb849f232fce3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916519"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Generowanie danych wejściowych przy użyciu dynamicznego wykonywania symbolicznego

IntelliTest generuje dane wejściowe dla [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) przez analizowanie warunków gałęzi w programie. Dane wejściowe testów są wybierane na podstawie tego, czy mogą wyzwalać nowe zachowania rozgałęzienia programu. Analiza jest procesem przyrostowym. Uściślenie predykatu `q: I -> {true, false}` przez formalne parametry wejściowe testu `I` . `q` reprezentuje zestaw zachowań, które IntelliTest już zaobserwowane. Początkowo, `q := false` ponieważ nic nie zostało jeszcze zaobserwowane.

Kroki pętli to:

1. IntelliTest określa dane wejściowe `i` , takie jak `q(i)=false` użycie [funkcji ograniczenia](#constraint-solver). Przez konstrukcję, dane wejściowe `i` będą mieć niewidocznyą ścieżkę wykonywania. Początkowo oznacza to, że `i` może to być dowolny dane wejściowe, ponieważ nie odnaleziono jeszcze ścieżki wykonywania.

1. IntelliTest wykonuje test z wybranymi danymi wejściowymi `i` i monitoruje wykonywanie testu i testowanego programu.

1. Podczas wykonywania program pobiera konkretną ścieżkę, która jest określana przez wszystkie uwarunkowane gałęzie programu. Zestaw wszystkich warunków określających wykonanie jest nazywany *warunkiem ścieżki*, zapisanym jako predykat `p: I -> {true, false}` nad formalnymi parametrami wejściowymi. IntelliTest oblicza reprezentację tego predykatu.

1. Zestawy IntelliTest `q := (q or p)` . Inaczej mówiąc, rejestruje fakt, że pojawił się ścieżka reprezentowana przez `p` .

1. Przejdź do kroku 1.

Funkcja [ograniczeń](#constraint-solver) IntelliTest może odnosić się do wartości wszystkich typów, które mogą być wyświetlane w programach .NET:

* [Liczby całkowite](#integers-and-floats) i [zmiennoprzecinkowe](#integers-and-floats)
* [Obiekty](#objects)
* [Struktury](#structs)
* [Tablice](#arrays-and-strings) i [ciągi](#arrays-and-strings)

IntelliTest filtruje dane wejściowe, które naruszają określone założenia.

Oprócz bezpośrednich wejść (argumentów do [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)) test może narysować dalsze wartości wejściowe z klasy statycznej [PexChoose](static-helper-classes.md#pexchoose) . Opcje te określają również zachowanie [makiet sparametryzowanych](#parameterized-mocks).

## <a name="constraint-solver"></a>Narzędzie do rozwiązywania ograniczeń

IntelliTest używa ograniczenia Solver do określenia odpowiednich wartości wejściowych testu i testowanego programu.

IntelliTest używa funkcji ograniczenia [Z3](https://github.com/Z3Prover/z3/wiki) .

## <a name="dynamic-code-coverage"></a>Dynamiczne pokrycie kodu

Jako efekt uboczny monitorowania środowiska uruchomieniowego IntelliTest zbiera dane dynamicznego pokrycia kodu.
Ta metoda jest nazywana *dynamiczną* , ponieważ IntelliTest wie tylko o kodzie, który został wykonany, dlatego nie może dawać wartości bezwzględnych dla pokrycia w taki sam sposób jak w przypadku innych narzędzi pokrycia.

Na przykład gdy IntelliTest zgłasza dynamiczne pokrycie jako bloki podstawowe 5/10, oznacza to, że pięć bloków z dziesięciu zostało pokrytych, gdzie łączna liczba bloków we wszystkich metodach, które zostały osiągnięte do tej pory przez analizę (w przeciwieństwie do wszystkich metod, które istnieją w badanym zestawie) to dziesięć.
W dalszej części analizy, jak bardziej osiągalne metody są odnajdywane, może wzrosnąć zarówno licznik (5 w tym przykładzie), jak i mianownik (10).

## <a name="integers-and-floats"></a>Wartości całkowite i zmiennoprzecinkowe

Funkcja IntelliTest [Constraint](#constraint-solver) określa testowe wartości wejściowe typów pierwotnych, takich jak **Byte**, **int**, **float** i others, aby wyzwolić różne ścieżki wykonywania dla testu i testowanego programu.

## <a name="objects"></a>Obiekty

IntelliTest może [utworzyć wystąpienia istniejących klas .NET](#existing-classes)lub użyć IntelliTest do automatycznego [tworzenia obiektów](#parameterized-mocks) , które implementują określony interfejs i zachowują się na różne sposoby w zależności od użycia.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Tworzenie wystąpień istniejących klas

**Jaki jest problem?**

IntelliTest monitoruje wykonywane instrukcje, gdy uruchamia test i program w teście. W szczególności monitoruje cały dostęp do pól. Następnie korzysta z [ograniczenia Solver](#constraint-solver) , aby określić nowe dane wejściowe testu, w tym obiekty i ich wartości pól, w taki sposób, że test i program objęty testem zadziałają w inny sposób.

Oznacza to, że IntelliTest musi utworzyć obiekty niektórych typów i ustawić ich wartości pól. Jeśli klasa jest [widoczna](#visibility) i ma [widoczny](#visibility) Konstruktor domyślny, IntelliTest może utworzyć wystąpienie klasy.
Jeśli wszystkie pola klasy są [widoczne](#visibility), IntelliTest może automatycznie ustawiać pola.

Jeśli typ nie jest widoczny lub pola nie są [widoczne](#visibility), IntelliTest potrzebuje pomocy przy tworzeniu obiektów i przeniesieniu ich do interesujących stanów w celu osiągnięcia maksymalnego pokrycia kodu. IntelliTest może używać odbicia do tworzenia i inicjowania wystąpień w dowolny sposób, ale zazwyczaj nie jest to pożądane, ponieważ może spowodować przeniesienie obiektu do stanu, który nigdy nie wystąpi podczas normalnego wykonywania programu. Zamiast tego IntelliTest opiera się na wskazówkach od użytkownika.

## <a name="visibility"></a>Widoczność

Platforma .NET ma rozbudowany model widoczności: typy, metody, pola i inne elementy członkowskie mogą być **prywatne**, **publiczne**, **wewnętrzne** i inne.

Gdy IntelliTest generuje testy, podejmie próbę wykonania tylko akcji (takich jak konstruktory wywoływania, metody i pola ustawień), które są dozwolone w odniesieniu do reguł widoczności .NET z poziomu kontekstu wygenerowanych testów.

Reguły są następujące:

* **Widoczność wewnętrznych elementów członkowskich**
  * IntelliTest zakłada, że wygenerowane testy będą miały dostęp do wewnętrznych elementów członkowskich, które były widoczne dla otaczającego [PexClass](attribute-glossary.md#pexclass).
  Platforma .NET ma **InternalsVisibleToAttribute** , aby zwiększyć widoczność wewnętrznych elementów członkowskich do innych zestawów.

* **Widoczność elementów prywatnych i rodzinnych (chronionych w języku C#) [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest zawsze umieszcza wygenerowane testy bezpośrednio w [PexClass](attribute-glossary.md#pexclass) lub w podklasie. W związku z tym IntelliTest zakłada, że może korzystać z wszystkich widocznych członków rodziny (**chronionych** w języku C#).
  * Jeśli wygenerowane testy są umieszczane bezpośrednio w [PexClass](attribute-glossary.md#pexclass) (zazwyczaj przy użyciu klas częściowych), IntelliTest zakłada, że mogą również używać wszystkich prywatnych członków [PexClass](attribute-glossary.md#pexclass).

* **Widoczność publicznych członków**
  * IntelliTest zakłada, że może korzystać ze wszystkich wyeksportowanych elementów członkowskich widocznych w kontekście [PexClass](attribute-glossary.md#pexclass).

## <a name="parameterized-mocks"></a>Sparametryzowane makiety

Jak przetestować metodę, która ma parametr typu interfejs? Lub klasy niezapieczętowanej? IntelliTest nie wie, które implementacje będą później używane, gdy ta metoda zostanie wywołana. A być może nie istnieje nawet rzeczywista implementacja dostępna w czasie testu.

Tradycyjna odpowiedź polega na użyciu *obiektów imitacji* z jawnym zachowaniem.

Obiekt makiety implementuje interfejs (lub rozszerza klasę niesealną). Nie reprezentuje rzeczywistej implementacji, ale tylko skrót, który umożliwia wykonywanie testów przy użyciu obiektu makiety. Jego zachowanie jest definiowane ręcznie jako część każdego przypadku testowego, w którym jest używana. Istnieje wiele narzędzi, które ułatwiają Definiowanie obiektów makiety i ich oczekiwane zachowanie, ale takie zachowanie musi być zdefiniowane ręcznie.

Zamiast zakodowanych wartości w obiektach makiet, IntelliTest może generować wartości. Tak jak umożliwia to [sparametryzowane testowanie jednostkowe](test-generation.md#parameterized-unit-testing), IntelliTest również włącza makiety sparametryzowane.

Makiety sparametryzowane mają dwa różne tryby wykonywania:

* **wybór**: podczas eksplorowania kodu, makiety sparametryzowane są źródłem dodatkowych testów wejściowych, a IntelliTest podejmie próbę wybrania interesujących wartości
* **powtarzanie**: podczas wykonywania poprzednio wygenerowanego testu, imitacje sparametryzowane zachowują się jak podciągi z zachowaniem (innymi słowy, wstępnie zdefiniowane zachowanie).

Użyj [PexChoose](static-helper-classes.md#pexchoose) , aby uzyskać wartości dla makiet sparametryzowanych.

## <a name="structs"></a>Struktury

IntelliTest o wartości **struktury** są podobne do sposobu, w jaki zajmuje się [obiektami](#objects).

## <a name="arrays-and-strings"></a>Tablice i ciągi

IntelliTest monitoruje wykonywane instrukcje w miarę uruchomienia testu i testowanego programu. W szczególności, gdy program jest zależny od długości ciągu lub tablicy (oraz dolnych granic i długości tablicy wielowymiarowej).
Zaobserwuje także, jak program używa różnych elementów ciągu lub tablicy. Następnie używa [funkcji ograniczającej ograniczenia](#constraint-solver) , aby określić, które długości i wartości elementów mogą spowodować, że test i program w ramach testu zadziałają w interesujący sposób.

IntelliTest podejmuje próbę zminimalizowania rozmiaru tablic i ciągów wymaganych do wyzwolenia interesujących zachowań programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Uzyskaj dodatkowe dane wejściowe

Klasa statyczna [PexChoose](static-helper-classes.md#pexchoose) może służyć do uzyskania dodatkowych wejść do testu i może służyć do implementowania [makiet sparametryzowanych](#parameterized-mocks).

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8).

## <a name="further-reading"></a>Dodatkowe informacje

* [Jak to działa?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
