---
title: Metryki kodu — głębokość dziedziczenia
ms.date: 1/8/2021
description: Dowiedz się więcej na temat głębokości metryk dziedziczenia dla metryk kodu w Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682696"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Metryki kodu — głębokość dziedziczenia (DIT)

W tym artykule poznasz jedną z metryk zaprojektowanych specjalnie na kątem analizy obiektowej: Głębokość dziedziczenia. Głębokość dziedziczenia, nazywana również głębokością drzewa dziedziczenia (DIT, depth of inheritance tree), jest definiowana jako "maksymalna długość od węzła do katalogu głównego [drzewa".](#ck) Można to zobaczyć w prostym przykładzie. Utwórz nowy projekt biblioteki klas i przed napisem jakiegokolwiek kodu oblicz metryki kodu, wybierając opcję Analizuj, > **oblicz metryki** kodu dla rozwiązania .

![Głębokość dziedziczenia , przykład 1](media/depth-of-inheritance-example-1.png)

Ponieważ wszystkie klasy dziedziczą `System.Object` z klasy , głębokość wynosi obecnie 1. Jeśli dziedziczysz z tej klasy i sprawdzasz nową klasę, możesz zobaczyć wynik:

![Głębokość dziedziczenia , przykład 2](media/depth-of-inheritance-example-2.png)

Zwróć uwagę, że im niższy węzeł w drzewie (w tym `Class2` przypadku), tym większa głębokość dziedziczenia. Możesz nadal tworzyć dzieci i spowodować, że głębokość zwiększy się tak, jak chcesz.

## <a name="assumptions"></a>Założenia

Głębokość dziedziczenia jest predykcyjna na podstawie trzech podstawowych [założeń PChN:](#ck)

1. Im głębsza klasa w hierarchii, tym większa liczba metod, które prawdopodobnie odziedziczy, co utrudnia przewidywanie jej zachowania.

2. Głębsze drzewa wymagają większej złożoności projektu, ponieważ jest zaangażowanych więcej klas i metod.

3. Bardziej głębokie klasy w drzewie mają większy potencjał ponownego ponownego wykorzystać metody dziedziczone.

Założenia 1 i 2 informują o tym, że większa liczba głębokości jest zła. Jeśli to właśnie się zakończyło, będziesz w dobrej kondycji. Jednak założenie 3 wskazuje, że większa liczba głębokości jest dobra do potencjalnego ponownego użycia kodu.

## <a name="analysis"></a>Analiza

Poniżej opisano sposób odczytywania metryki głębokości:

- Mała liczba głębokości

  Mała liczba głębokości oznacza mniejszą złożoność, ale także możliwość mniejszego ponownego użycia kodu przez dziedziczenie.

- Duża liczba głębokości

  Duża liczba głębokości oznacza większe ryzyko ponownego użycia kodu przez dziedziczenie, ale także większą złożoność z większym prawdopodobieństwem błędów w kodzie.

## <a name="code-analysis"></a>Analiza kodu

Analiza kodu obejmuje kategorię Reguł konserwacji. Aby uzyskać więcej informacji, zobacz [Reguły konserwacji](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). W przypadku korzystania ze starszej analizy kodu zestaw rozszerzonych wytycznych projektowych zawiera obszar konserwacji:

![Głębokość zestawów reguł projektowania dziedziczenia](media/depth-of-inheritance-design-guidelines.png)

W obszarze konserwacji znajduje się reguła dziedziczenia:

![Głębokość reguły utrzymania dziedziczenia](media/depth-of-inheritance-maintainability-rule.png)

Ta reguła wydaje ostrzeżenie, gdy głębokość dziedziczenia osiągnie 6 lub większą, dlatego jest dobrą regułą, która zapobiega nadmiernemu dziedziczeniu. Aby dowiedzieć się więcej na temat reguły, [zobacz CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Umieszczanie wszystkiego razem

Wysokie wartości dit oznaczają również, że ryzyko błędów jest wysokie, a niskie wartości zmniejszają ryzyko błędów. Wysokie wartości dit wskazują większe możliwości ponownego użycia kodu przez dziedziczenie, niskie wartości sugerują mniejsze ponowne użycie kodu, chociaż dziedziczenie do wykorzystania. Ze względu na brak wystarczającej ilości danych nie ma obecnie akceptowanego standardu dla wartości DIT. Nawet ostatnio wykonane badania nie znalazły wystarczających danych, aby określić realną liczbę, która mogłaby zostać użyta jako liczba standardowa dla tej metryki [Shatnawi.](#shatnawi) Chociaż nie ma żadnych empirycznych dowodów, aby to wspierać, kilka zasobów sugeruje, że wartość DIT około 5 lub 6 powinna być górnym limitem. Na przykład zobacz [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) .

## <a name="citations"></a>Cytatów

### <a name="ck"></a>Ck

Chidamber, S. R. & Kemerer, C. F. (1994). A Metrics Suite for Object Oriented Design (IEEE Transactions on Software Engineering, Tom 20, Nie. 6). Pobrane 14 maja 2011 r. z witryny internetowej Uniwersytetu Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramanyam, R. & Krishnan, M. S. (2003). Empiryczna analiza metryk PChN dla złożoności projektu Object-Oriented: Implikacje dotyczące wad oprogramowania (transakcje IEEE dotyczące inżynierii oprogramowania, tom 29, nie. 4). Pobrano ją 14 maja 2011 r., pierwotnie uzyskaną z witryny internetowej University of Massachusetts w Witrynie internetowej [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Ilościowe badanie akceptowalnych poziomów ryzyka metryk Object-Oriented w systemach Open-Source (transakcje IEEE dotyczące inżynierii oprogramowania, tom 36, nie. 2).