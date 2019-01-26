---
title: Dynamiczne symboliczne wykonywanie | Narzędzie Test Microsoft IntelliTest dla deweloperów
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b210248a9ac27945ee6eb1e2f1d5219c6dd62117
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936622"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Generowanie danych wejściowych, za pomocą dynamiczne symboliczne wykonywanie

Funkcja IntelliTest generuje dane wejściowe dla [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing) , analizując warunków gałęzi w programie.
Dane wejściowe testu są wybierane w zależności od tego, czy można uruchomić nowego zachowania rozgałęziania programu.
Analiza jest procesem przyrostowe. Udoskonalanie predykat **Pyt.: Czy mogę -> {true lub false}** za pośrednictwem formalnych testu parametry wejściowe **I**. **q** reprezentuje zestaw zachowań, które ma zaobserwowane IntelliTest.
Początkowo **q: = false**, ponieważ nic nie został jeszcze zaobserwowany.

Procedura pętli jest następująca:

1. IntelliTest Określa dane wejściowe **i** tak, aby **funkcji pytania i odpowiedzi (i) = false** przy użyciu [moduł rozwiązywania ograniczeń](#constraint-solver).
   Wynikające z konstrukcji, dane wejściowe **i** zajmie ścieżką wykonywania nie zauważony. Oznacza to, że początkowo **i** może być dowolnych danych wejściowych, ponieważ wykryto jeszcze żadnej ścieżki wykonywania.

1. IntelliTest wykonuje test przy użyciu wybrane dane wejściowe **i**oraz monitoruje wykonanie testu i program w ramach testu.

1. Podczas wykonywania program pobiera określoną ścieżką, która jest określana przez wszystkie gałęzie warunkowego programu. Zestaw wszystkie warunki, które określają wykonywania jest nazywany *warunku ścieżki*, napisana jako predykat **p: Czy mogę -> {true lub false}** za pośrednictwem formalnych parametrów wejściowych. Funkcja IntelliTest oblicza reprezentację ten predykat.

1. Zestawy testów funkcji IntelliTest **q: = (q lub p)**. Innymi słowy, rejestruje fakt, że jego obserwowała, jak ścieżki, reprezentowane przez **p**.

1. Przejdź do kroku 1.

W funkcji IntelliTest [moduł rozwiązywania ograniczeń](#constraint-solver) poradzenie sobie z wartości wszystkich typów, które mogą się pojawić w programach .NET:

* [Liczby całkowite](#integers-and-floats) i [liczby zmiennoprzecinkowe](#integers-and-floats)
* [Obiekty](#objects)
* [Struktury](#structs)
* [Tablice](#arrays-and-strings) i [ciągów](#arrays-and-strings)

Funkcja IntelliTest odfiltrowuje danych wejściowych, które naruszają podane założeń.

Oprócz natychmiastowego danych wejściowych (argumenty [parametryzowane testy jednostki](test-generation.md#parameterized-unit-testing)), test można narysować dalsze wartości wejściowe z [PexChoose](static-helper-classes.md#pexchoose) klasy statycznej. Opcje określają również zachowanie [sparametryzowane mocks](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Moduł rozwiązywania ograniczeń

IntelliTest używa moduł rozwiązywania ograniczeń w celu ustalenia odpowiednich wartości wejściowe testu, a program w ramach testu.

Używa funkcji IntelliTest [Z3](https://github.com/Z3Prover/z3/wiki) moduł rozwiązywania ograniczeń.

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Pokrycie kodu dynamiczne

Jako efekt uboczny środowiska uruchomieniowego, monitorowanie program IntelliTest zbiera dane pokrycia kodu dynamicznych.
Jest to nazywane *dynamiczne* ponieważ IntelliTest tylko zna kod, który został wykonany, w związku z tym go nie można nadać wartości bezwzględne dla pokrycia w taki sam sposób jak inne narzędzie pokrycia zwykle.

Na przykład, gdy program IntelliTest zgłasza pokrycie dynamiczne jako 5/10 podstawowe bloki, oznacza to, że pięć bloków z 10 zostały pokryte, gdzie całkowita liczba bloków w wszystkie metody, które zostały osiągnięte do tej pory w analizie (w przeciwieństwie do wszystkich metod, które istnieją w zestawu w ramach testu) wynosi dziesięć.
W dalszej części analizy, ponieważ więcej metod dostępne są odnajdywane licznika (5, w tym przykładzie) i może zwiększyć mianownik (10).

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Liczby całkowite i wartości zmiennoprzecinkowe

W funkcji IntelliTest [moduł rozwiązywania ograniczeń](#constraint-solver) określa wartości wejściowe testu typów podstawowych, takich jak **bajtów**, **int**, **float**wraz z innymi w kolejność, aby wyzwolić wykonywanie różnych ścieżek dla testu i program w ramach testu.

<a name="objects"></a>
## <a name="objects"></a>Obiekty

IntelliTest mogą [tworzenia wystąpień klas .NET istniejących](#existing-classes), lub skorzystać z funkcją IntelliTest, aby automatycznie [tworzenia obiektów makiety](#parameterized-mocks) implementowania określonego interfejsu i zachowują się na różne sposoby w zależności od użycia.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Utwórz wystąpienie istniejących klas

**Na czym polega problem?**

IntelliTest monitoruje instrukcje wykonany po uruchomieniu testu i program w ramach testu. W szczególności monitoruje wszelki dostęp do pola. Następnie używa [moduł rozwiązywania ograniczeń](#constraint-solver) ustalenie nowe dane wejściowe testu, tym obiekty i ich wartości pól w taki sposób, że test i programu w trakcie testu będzie się odbywać na innych interesujących sposobów.

Oznacza to, że program IntelliTest muszą do tworzenia obiektów określonego typu i ustaw ich wartości pól. Jeśli klasa jest [widoczne](#visibility) i ma [widoczne](#visibility) domyślnego konstruktora IntelliTest można utworzyć wystąpienia klasy.
W przypadku wszystkich pól klasy [widoczne](#visibility), IntelliTest można ustawić pola automatycznie.

Typ nie jest widoczny, czy pola nie są [widoczne](#visibility), IntelliTest potrzebuje pomocy, aby utworzyć obiekty i ich dostosowania do Państwa interesujące do osiągnięcia pokrycia kodu maksymalny. IntelliTest można używać odbicia do tworzenia i inicjowania wystąpień w dowolny sposób, ale nie jest to zazwyczaj pożądane, ponieważ może ona Przenieś obiekt w stan, który nigdy nie mogą wystąpić podczas normalnego działania programu. Zamiast tego program IntelliTest opiera się na wskazówki od użytkownika.

<a name="visibility"></a>
## <a name="visibility"></a>Widoczność

.NET Framework zawiera model wgląd w rozbudowane: typy, metody, pola i inne elementy Członkowskie mogą być **prywatnej**, **publicznych**, **wewnętrzny**i nie tylko.

IntelliTest, generując testy, podejmie próbę wykonania tylko te akcje (na przykład podczas wywoływania konstruktorów, metod i ustawianie pól), które są dopuszczalne w odniesieniu do reguły widoczności .NET z w kontekście wygenerowane testy.

Dostępne są następujące reguły:

* **Widoczność składowe wewnętrzne**
  * IntelliTest przyjęto założenie, że wygenerowane testy będą mieć dostęp do wewnętrznych składowych, które były widoczne dla otaczający [PexClass](attribute-glossary.md#pexclass).
  .NET dotyczą **InternalsVisibleToAttribute** rozszerzeniu widoczności wewnętrznych składowych dla innych zestawów.<p />

* **Widoczność prywatne i członków rodziny (chroniony w języku C#) [PexClass](attribute-glossary.md#pexclass)**
  * Funkcja IntelliTest zawsze umieszcza wygenerowane testy bezpośrednio w [PexClass](attribute-glossary.md#pexclass) lub podklasę. W związku z tym, IntelliTest zakłada, że mogą używać w niej wszystkich członków rodziny widoczne (**chronione** w języku C#).
  * Jeśli wygenerowane testy są umieszczane bezpośrednio w [PexClass](attribute-glossary.md#pexclass) (zazwyczaj przy użyciu klas częściowych), program IntelliTest zakłada, że mogą również używać wszystkim członkom prywatnej [PexClass](attribute-glossary.md#pexclass).<p />

* **Widoczność publiczne elementy członkowskie**
  * Funkcja IntelliTest przyjęto założenie, może użyć wyeksportowanego wszystkie elementy członkowskie, które są widoczne w kontekście [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Mocks sparametryzowane

Jak przetestować metodę, która ma parametr typu interfejsu? Lub klasą niezapieczętowaną? Funkcja IntelliTest nie zna implementacji, które zostaną użyte później, gdy ta metoda jest wywoływana. I prawdopodobnie nie ma jeszcze rzeczywistej implementacji dostępne w czasie testu.

Konwencjonalne odpowiedzi jest użycie *testowanie obiektów* z zachowaniem jawnego.

Makiety obiektu implementuje interfejs (lub rozszerza klasą niezapieczętowaną). Nie odpowiada on rzeczywistej implementacji, ale po prostu skrót, który zezwala na wykonywanie testów przy użyciu makiety obiektu. Jego zachowanie jest definiowane ręcznie w ramach każdego przypadku testowego, w którym jest używana. Istnieje wiele narzędzi, ułatwiających zdefiniowanie makiety obiektów i ich oczekiwane zachowanie, ale nadal należy ręcznie zdefiniować to zachowanie.

Zamiast zakodowanych wartości w obiektach makiety funkcji IntelliTest mogą generować wartości. Tak samo jak umożliwia [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing), IntelliTest umożliwia również mocks sparametryzowanych.

Sparametryzowany mocks mają dwa tryby wykonywania różnych:

* **Wybieranie**: podczas analizowania kodu, sparametryzowane mocks są źródłem dane wejściowe testu dodatkowe, a IntelliTest podejmie próbę wybierz interesujące wartości
* **oparte na metodzie powtórzeń**: podczas wykonywania wcześniej wygenerowany test, sparametryzowane mocks zachowują się jak wycinków z zachowaniem (innymi słowy, wstępnie zdefiniowanych zachowanie).

Użyj [PexChoose](static-helper-classes.md#pexchoose) można uzyskać wartości mocks sparametryzowanych.

<a name="structs"></a>
## <a name="structs"></a>Struktury

Program IntelliTest w wnioskowania o **struktury** wartości jest podobny sposób, ponieważ dotyczy on [obiektów](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Tablice i ciągi

IntelliTest monitoruje instrukcje wykonanych podczas wykonywania testu, a program w ramach testu. W szczególności przestrzega, gdy program jest zależny od długość ciągu lub tablicy (i dolne granice i długości tablicy wielowymiarowej).
Przestrzega również, jak program używa różnych elementów, string lub tablicy. Następnie używa [moduł rozwiązywania ograniczeń](#constraint-solver) Aby określić długości i element wartości, które mogą powodować testu i programu w trakcie testu będzie działać w różny sposób.

IntelliTest próbuje zminimalizować rozmiar macierzy i ciągi wymaganym do wyzwolenia interesujące zachowania programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Uzyskaj dodatkowe dane wejściowe

[PexChoose](static-helper-classes.md#pexchoose) klasy statycznej może służyć do uzyskiwania dodatkowych danych wejściowych do testu i może służyć do implementowania [sparametryzowane mocks](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Dalsze informacje

* [Jak to działa?](https://blogs.msdn.microsoft.com/devops/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Czy chcesz przesłać opinię?

Opublikuj swoje pomysły i funkcji żądania na [społeczności deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).