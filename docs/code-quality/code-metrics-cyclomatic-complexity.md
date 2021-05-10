---
title: Metryki kodu — złożoność kierunkowa
ms.date: 5/7/2021
description: Dowiedz się więcej na temat metryki złożoności poziomej dla metryk kodu w Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682690"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Metryki kodu — złożoność kierunkowa

Podczas pracy z metrykami kodu jeden z najmniej zrozumiałych elementów wydaje się być skomplikowany. Zasadniczo ze względu na złożoność tyczną wyższe liczby są złe, a niższe liczby są dobre. Możesz użyć złożonej złożoności, aby dowiedzieć się, jak trudny może być dowolny kod do testowania, konserwacji lub rozwiązywania problemów, a także wskazanie prawdopodobieństwo, że kod będzie tworzyć błędy. Na wysokim poziomie określamy wartość złożoności poziomowej, zliczamy liczbę decyzji podejmowanych w kodzie źródłowym. W tym artykule zaczniesz od prostego przykładu złożonej złożoności, aby szybko zrozumieć koncepcję, a następnie przyjrzysz się dodatkowym informacjom na temat rzeczywistego użycia i sugerowanych limitów. Na koniec znajduje się sekcja cytowań, których można użyć, aby zagłębić się w ten temat.

## <a name="example"></a>Przykład

Złożoność ostateczna jest definiowana jako mierzenie "ilości logiki decyzyjnej w funkcji kodu źródłowego" [NIST235.](#nist235) Mówiąc prościej, im więcej decyzji należy podejmować w kodzie, tym bardziej złożone.

Zobaczmy, jak to jest w działaniu. Utwórz nową aplikację konsoli i natychmiast oblicz metryki kodu, przechodząc do > **Analizowanie** metryk kodu dla rozwiązania .

![Przykład złożoności złożonej 1](media/cyclomatic-complexity-example-1.png)

Zwróć uwagę, że złożoność poziomowa wynosi 2 (najniższa możliwa wartość). Jeśli dodasz kod bez podejmowania decyzji, zwróć uwagę, że złożoność nie zmienia się:

![Przykład złożoności złożonej 2](media/cyclomatic-complexity-example-2.png)

Jeśli dodasz decyzję, wartość złożoności poziomej zwiększa się o 1:

![Przykład złożonej złożoności 3](media/cyclomatic-complexity-example-3.png)

Po zmianie instrukcji if na instrukcje switch z 4 decyzjami, które mają zostać podjęte, przechodzi ona z oryginalnej wartości 2 do 6:

![Przykład złożoności 4](media/cyclomatic-complexity-example-4.png)

Przyjrzyjmy się (hipotetycznie) większej bazie kodu.

![Przykład złożoności 5](media/cyclomatic-complexity-example-5.png)

Zwróć uwagę, że większość elementów podczas przechodzenia do Products_Related klasy ma wartość 1, ale kilka z nich ma złożoność 5. Sama w sobie może nie być dużą zaletą, ale biorąc pod uwagę, że większość innych składowych ma 1 w tej samej klasie, zdecydowanie należy przyjrzeć się bliżej tym dwóch elementom i zobaczyć, co się w nich znajduje. Możesz to zrobić, klikając prawym przyciskiem myszy element i wybierając pozycję Przejdź do **kodu źródłowego** z menu kontekstowego. Przyjrzyj się bliżej `Product.set(Product)` :

![Przykład złożoności 6](media/cyclomatic-complexity-example-6.png)

Biorąc pod uwagę wszystkie instrukcje if, można zobaczyć, dlaczego złożoność systemu wynosi 5. Na tym etapie możesz zdecydować, że jest to akceptowalny poziom złożoności, lub refaktoryzować, aby zmniejszyć złożoność.

## <a name="the-magic-number"></a>Magiczny numer

Podobnie jak w przypadku wielu metryk w tej branży, nie ma dokładnego limitu złożoności, który pasuje do wszystkich organizacji. Jednak [NIST235](#nist235) wskazuje, że limit 10 jest dobrym punktem początkowym:

"Dokładna liczba, która ma być limitem, pozostaje jednak nieco niesłabna. Oryginalny limit 10 zgodnie z propozycją firmy McCabe ma znaczące dowody potwierdzające, ale pomyślnie wykorzystano również limity do 15. Limity powyżej 10 powinny być zarezerwowane dla projektów, które mają kilka korzyści operacyjnych w powyżej typowych projektów, na przykład dla doświadczonego personelu, formalnego projektu, nowoczesnego języka programowania, programowania strukturalnego, przewodników po kodzie i kompleksowego planu testowania. Innymi słowy, organizacja może wybrać limit złożoności większy niż 10, ale tylko wtedy, gdy ma pewność, że wie, co robi, i chce przeznaczyć dodatkowe nakłady na testowanie wymagane przez bardziej złożone moduły". [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Skomplikowana złożoność i numery linii

Samo przyglądanie się liczbie wierszy kodu jest w najlepszym przypadku bardzo szerokim predyktorem jakości kodu. Istnieje podstawowa prawda o tym, że im więcej wierszy kodu w funkcji, tym większe prawdopodobieństwo, że występują błędy. Jednak połączenie złożonej złożoności z liniami kodu pozwala uzyskać znacznie bardziej przejrzysty obraz potencjalnych błędów.

Zgodnie z opisem w pakiet Software Assurance Technology Center (SATC) na NASA:

"SatC stwierdził, że najbardziej efektywną oceną jest kombinacja złożoności rozmiaru i (Procesumatic). Moduły o dużej złożoności i dużym rozmiarze mają zwykle najmniejszą niezawodność. Moduły o niskim rozmiarze i wysokiej złożoności są również ryzykiem niezawodności, ponieważ zwykle są bardzo skomplikowanym kodem, który jest trudny do zmiany lub zmodyfikowania". [SATC](#satc)

## <a name="code-analysis"></a>Analiza kodu

Analiza kodu obejmuje kategorię Reguł konserwacji. Aby uzyskać więcej informacji, zobacz [Reguły konserwacji](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). W przypadku korzystania ze starszej analizy kodu zestaw reguł rozszerzonych wytycznych projektowych zawiera obszar konserwacji:

![Zestawy reguł wytycznych dotyczących projektowania złożonej złożoności](media/cyclomatic-complexity-design-guidelines.png)

W obszarze konserwacji znajduje się reguła złożoności:

![Reguła konserwacji złożonej](media/cyclomatic-complexity-maintainability-rule.png)

Ta reguła wydaje ostrzeżenie, gdy złożoność poziomowa osiągnie 25, więc może pomóc uniknąć nadmiernej złożoności. Aby dowiedzieć się więcej na temat reguły, zobacz [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Umieszczanie wszystkiego razem

W dolnej części jest to, że duża liczba złożoności oznacza większe prawdopodobieństwo błędów ze zwiększonym czasem na konserwację i rozwiązywanie problemów. Przyjrzyj się bliżej dowolnym funkcjiom, które mają wysoką złożoność, i zdecyduj, czy należy je refaktoryzować, aby były mniej złożone.

## <a name="citations"></a>Cytatów

### <a name="mccabe5"></a>MCCABE5

McCabe, T. i A. Watson (1994), Software Complexity (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Testowanie strukturalne: metodologia testowania korzystająca z metryki złożoności strukturalnej (specjalna publikacja NIST 500-235). Pobrana 14 maja 2011 r. z witryny internetowej firmy McCabe Software: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Przemysł, T., Rik, J. (1998). Metryki i niezawodność oprogramowania (proceedings of IEEE International Symposium on Software Reliability Engineering). Pobrano go 14 maja 2011 r. z witryny internetowej Penn State University: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)