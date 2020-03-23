---
title: Dynamiczne wykonanie symboliczne | Narzędzie testowe Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e5a3248d3f081bcab08c08110d305f0aa6235817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302624"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Generowanie danych wejściowych przy użyciu dynamicznego wykonania symbolicznego

IntelliTest generuje dane wejściowe dla [sparametryzowanych testów jednostkowych,](test-generation.md#parameterized-unit-testing) analizując warunki gałęzi w programie. Dane wejściowe testowe są wybierane na podstawie tego, czy mogą one wyzwalać nowe zachowania rozgałęziania programu. Analiza jest procesem przyrostowym. Udoskonala predykat `q: I -> {true, false}` nad formalnymi parametrami `I`wejściowymi testu . `q`reprezentuje zestaw zachowań, które IntelliTest już zaobserwował. Początkowo `q := false`, ponieważ nic nie zostało jeszcze zaobserwowane.

Kroki pętli są następujące:

1. IntelliTest określa dane `i` wejściowe w taki sposób, że `q(i)=false` przy użyciu [solvera ograniczeń](#constraint-solver). Przez budowę, `i` dane wejściowe zajmie ścieżkę wykonania nie widziałem wcześniej. Początkowo oznacza to, że `i` może być dowolne dane wejściowe, ponieważ nie ścieżka wykonywania została jeszcze odnaleziona.

1. IntelliTest wykonuje test z wybranym `i`wejściem i monitoruje wykonanie testu i testowany program.

1. Podczas wykonywania program przyjmuje określoną ścieżkę, która jest określana przez wszystkie gałęzie warunkowe programu. Zestaw wszystkich warunków, które określają wykonanie jest nazywany *warunek ścieżki,* `p: I -> {true, false}` napisany jako predykat dla formalnych parametrów wejściowych. IntelliTest oblicza reprezentację tego predykatu.

1. IntelliTest `q := (q or p)`zestawy . Innymi słowy, rejestruje fakt, że widział ścieżkę `p`reprezentowaną przez .

1. Przejdź do kroku 1.

[Solver ograniczenia](#constraint-solver) IntelliTest może zajmować się wartościami wszystkich typów, które mogą pojawić się w programach .NET:

* [Liczby całkowite](#integers-and-floats) i [pływaki](#integers-and-floats)
* [Obiekty](#objects)
* [Struktury](#structs)
* [Tablice](#arrays-and-strings) i [ciągi](#arrays-and-strings)

IntelliTest filtruje dane wejściowe, które naruszają określone założenia.

Oprócz natychmiastowych danych wejściowych (argumenty do [sparametryzowanych testów jednostkowych),](test-generation.md#parameterized-unit-testing)test może pobierać dalsze wartości wejściowe z klasy statycznej [PexChoose.](static-helper-classes.md#pexchoose) Wybory określają również zachowanie [sparametryzowanych makiet](#parameterized-mocks).

## <a name="constraint-solver"></a>Narzędzie do rozwiązywania ograniczeń

IntelliTest używa solver ograniczenia do określenia odpowiednich wartości wejściowych testu i programu w ramach testu.

IntelliTest używa solver ograniczenia [Z3.](https://github.com/Z3Prover/z3/wiki)

## <a name="dynamic-code-coverage"></a>Dynamiczne pokrycie kodu

Jako efekt uboczny monitorowania środowiska uruchomieniowego IntelliTest zbiera dane dynamicznego pokrycia kodu.
Jest to nazywane *dynamiczny,* ponieważ IntelliTest wie tylko o kod, który został wykonany, w związku z tym nie może dać wartości bezwzględne dla pokrycia w taki sam sposób, jak inne narzędzie pokrycia zwykle zrobić.

Na przykład, gdy IntelliTest zgłasza dynamiczne pokrycie jako 5/10 podstawowych bloków, oznacza to, że pięć bloków na dziesięć zostały objęte, gdzie całkowita liczba bloków we wszystkich metodach, które zostały osiągnięte do tej pory przez analizę (w przeciwieństwie do wszystkich metod, które istnieją w zestawie w fazie testów) jest dziesięć.
W dalszej części analizy, w miarę odnajdowania bardziej osiągalnych metod, licznik (5 w tym przykładzie) i mianownik (10) mogą wzrosnąć.

## <a name="integers-and-floats"></a>Wartości całkowite i zmiennoprzecinkowe

[Solver ograniczenia](#constraint-solver) IntelliTest określa wartości wejściowe testu typów pierwotnych, takich jak **bajt**, **int**, **float**i innych w celu wyzwolenia różnych ścieżek wykonywania dla testu i programu w ramach testu.

## <a name="objects"></a>Obiekty

IntelliTest można [utworzyć wystąpienia istniejących klas .NET,](#existing-classes)lub można użyć IntelliTest automatycznie [utworzyć makiety obiektów,](#parameterized-mocks) które implementują określonego interfejsu i zachowują się na różne sposoby w zależności od użycia.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Tworzenie wystąpienia istniejących klas

**W czym tkwi problem?**

IntelliTest monitoruje wykonane instrukcje podczas uruchamiania testu i testowany program. W szczególności monitoruje cały dostęp do pól. Następnie używa [solver ograniczenia](#constraint-solver) do określenia nowych danych wejściowych testu, w tym obiektów i ich wartości pola, tak, że test i program w ramach testu będzie zachowywać się w inny interesujący sposób.

Oznacza to, że IntelliTest musi tworzyć obiekty niektórych typów i ustawić ich wartości pola. Jeśli klasa jest [widoczna](#visibility) i ma [widoczny](#visibility) konstruktor domyślny, IntelliTest można utworzyć wystąpienie klasy.
Jeśli wszystkie pola klasy są [widoczne,](#visibility)IntelliTest można ustawić pola automatycznie.

Jeśli typ nie jest widoczny lub pola nie są [widoczne,](#visibility)IntelliTest potrzebuje pomocy w tworzeniu obiektów i doprowadzać ich do interesujących stanów w celu osiągnięcia maksymalnego pokrycia kodu. IntelliTest może używać odbicia do tworzenia i inicjowania wystąpień w dowolny sposób, ale zwykle nie jest to pożądane, ponieważ może doprowadzić obiekt do stanu, który nigdy nie może wystąpić podczas normalnego wykonywania programu. Zamiast tego IntelliTest opiera się na wskazówek od użytkownika.

## <a name="visibility"></a>Widoczność

.NET ma rozbudowany model widoczności: typy, metody, pola i inne elementy członkowskie mogą być **prywatne,** **publiczne,** **wewnętrzne**i inne.

Gdy IntelliTest generuje testy, podejmie próbę wykonania tylko akcje (takie jak wywoływanie konstruktorów, metod i pól ustawień), które są legalne w odniesieniu do reguł widoczności platformy .NET w kontekście wygenerowanych testów.

Zasady są następujące:

* **Widoczność członków wewnętrznych**
  * IntelliTest zakłada, że wygenerowane testy będą miały dostęp do wewnętrznych elementów członkowskich, które były widoczne dla otaczającej [PexClass](attribute-glossary.md#pexclass).
  .NET ma **InternalsVisibleToAttribute** rozszerzyć widoczność wewnętrznych elementów członkowskich do innych zestawów.

* **Widoczność członków [rodziny](attribute-glossary.md#pexclass) prywatnej i rodzinnej (chronionej w języku C#)**
  * IntelliTest zawsze umieszcza wygenerowane testy bezpośrednio w [PexClass](attribute-glossary.md#pexclass) lub do podklasy. W związku z tym IntelliTest zakłada, że może używać wszystkich widocznych członków rodziny **(chronione** w języku C#).
  * Jeśli wygenerowane testy są umieszczane bezpośrednio w [PexClass](attribute-glossary.md#pexclass) (zwykle przy użyciu klas częściowych), IntelliTest zakłada, że może również używać wszystkich prywatnych członków [PexClass](attribute-glossary.md#pexclass).

* **Widoczność członków publicznych**
  * IntelliTest zakłada, że może używać wszystkich wyeksportowanych elementów członkowskich widocznych w kontekście [PexClass](attribute-glossary.md#pexclass).

## <a name="parameterized-mocks"></a>Sparametryzowane makiety

Jak przetestować metodę, która ma parametr typu interfejsu? Lub klasy nie zapieczętowanej? IntelliTest nie wie, które implementacje będą później używane, gdy ta metoda jest wywoływana. I być może nie ma nawet prawdziwej implementacji dostępnej w czasie testu.

Konwencjonalną odpowiedzią jest użycie *makiety obiektów* z jawnym zachowaniem.

Makieta obiektu implementuje interfejs (lub rozszerza nie zapieczętowane klasy). Nie reprezentuje rzeczywistej implementacji, ale tylko skrót, który umożliwia wykonywanie testów przy użyciu obiektu makiety. Jego zachowanie jest definiowane ręcznie jako część każdego przypadku testowego, w którym jest używany. Istnieje wiele narzędzi, które ułatwiają definiowanie makiety obiektów i ich oczekiwane zachowanie, ale to zachowanie musi być nadal zdefiniowane ręcznie.

Zamiast wartości zakodowanych na twardo w obiektach makiety IntelliTest może generować wartości. Podobnie jak umożliwia [sparametryzowane testowanie jednostek,](test-generation.md#parameterized-unit-testing)IntelliTest umożliwia również sparametryzowane kpiny.

Parametryzowane makiety mają dwa różne tryby wykonywania:

* **wybór**: podczas eksplorowania kodu, sparametryzowane makiety są źródłem dodatkowych danych wejściowych testowych, a IntelliTest spróbuje wybrać interesujące wartości
* **replay**: podczas wykonywania wcześniej wygenerowanego testu, sparametryzowane kpiny zachowują się jak wycinki z zachowaniem (innymi słowy, wstępnie zdefiniowane zachowanie).

Użyj [PexChoose,](static-helper-classes.md#pexchoose) aby uzyskać wartości dla sparametryzowanych makiet.

## <a name="structs"></a>Struktury

Rozumowanie IntelliTest na temat wartości **struktury** jest podobne do sposobu, w jaki zajmuje się [obiektami.](#objects)

## <a name="arrays-and-strings"></a>Tablice i ciągi

IntelliTest monitoruje wykonane instrukcje podczas uruchamiania testu i testowany program. W szczególności obserwuje, kiedy program zależy od długości ciągu lub tablicy (i dolnej granicy i długości tablicy wielowymiarowej).
Obserwuje również, jak program używa różnych elementów ciągu lub tablicy. Następnie używa [solver ograniczenia](#constraint-solver) do określenia, które długości i wartości elementu może spowodować test i program w fazie testów zachowywać się w interesujący sposób.

IntelliTest próbuje zminimalizować rozmiar tablic i ciągów wymaganych do wyzwalania interesujących zachowań programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Uzyskiwanie dodatkowych danych wejściowych

Klasa statyczna [PexChoose](static-helper-classes.md#pexchoose) może służyć do uzyskania dodatkowych danych wejściowych do testu i może służyć do implementowania [sparametryzowanych makiet.](#parameterized-mocks)

## <a name="got-feedback"></a>Chcesz przesłać opinię?

Opublikuj swoje pomysły i sugestie funkcji w [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="further-reading"></a>Dodatkowe informacje

* [Jak to działa?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
