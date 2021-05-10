---
title: Metryki kodu — sprzężenie klas
ms.date: 1/8/2021
description: Dowiedz się więcej na temat metryk sprzężenia klas dla metryk kodu w Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666812"
---
# <a name="code-metrics---class-coupling"></a>Metryki kodu — sprzężenie klas

Sprzężenie klas jest również określane przez nazwę Sprzężenie między obiektami (CBO) zgodnie z pierwotnie zdefiniowaną przez [klasę CK94](#ck94). Zasadniczo sprzężenie klas jest miarą, ilu klas używa pojedyncza klasa. Duża liczba jest zła, a niska liczba jest zazwyczaj dobra w przypadku tej metryki. Sprzężenie klas było dokładnym predyktorem awarii oprogramowania, a ostatnie badania wykazały, że wartość górnego limitu 9 jest najbardziej wydajną wartością [W2010.](#s2010)

Zgodnie z dokumentacją firmy Microsoft sprzężenie klas "mierzy sprzężenie z unikatowymi klasami za pomocą parametrów, zmiennych lokalnych, typów zwracanych, wywołań metod, wystąpienia ogólnych lub szablonów, klas bazowych, implementacji interfejsów, pól zdefiniowanych na typach zewnętrznych i dekoracji atrybutów. Dobry projekt oprogramowania określa, że typy i metody powinny mieć wysoką spójność i niskie sprzężenie. Wysokie sprzężenie oznacza projekt, który jest trudny do ponownego użycia i utrzymania ze względu na wiele współzależności od innych typów".

Pojęcia sprzężenia i spójności są wyraźnie powiązane. Aby zachować tę dyskusję na ten temat, nie będziemy szczegółowo zagłębiać się w spójność inną niż w celu uzyskania krótkiej definicji z [KKLS2000:](#kkls2000)

"Spójność modułów została wprowadzona przez Wasz i Constantine jako 'jak ściśle powiązane lub powiązane wewnętrzne elementy modułu są ze sobą' [YC79.](#yc79) Moduł ma silną spójność, jeśli reprezentuje dokładnie jedno zadanie [...], a wszystkie jego elementy przyczyniają się do tego pojedynczego zadania. Opisują one spójność jako atrybut projektu, a nie kod, oraz atrybut, który może służyć do przewidywania możliwości ponownego użyteczności, możliwości konserwacji i możliwości zmiany".

## <a name="class-coupling-example"></a>Przykład sprzężenia klas

Przyjrzyjmy się sprzężenia klasom w działaniu. Najpierw utwórz nową aplikację konsolową i utwórz nową klasę o nazwie Person z pewnymi właściwościami, a następnie natychmiast oblicz metryki kodu:

![Przykład sprzężenia klas 1](media/class-coupling-example-1.png)

Zwróć uwagę, że sprzężenie klasy ma 0, ponieważ ta klasa nie używa żadnych innych klas. Teraz utwórz kolejną klasę o nazwie PersonStuff przy użyciu metody , która tworzy wystąpienie klasy Person i ustawia wartości właściwości. Oblicz ponownie metryki kodu:

![Przykład sprzężenia klas 2](media/class-coupling-example-2.png)

Zobacz, jak wartość sprzężenia klasy podniesie się? Zauważ również, że niezależnie od tego, ile właściwości ustawisz, wartość sprzężenia klasy po prostu podniesie się o 1, a nie o jakąś inną wartość. Sprzężenie klas mierzy każdą klasę tylko raz dla tej metryki niezależnie od tego, ile jest używana. Ponadto, czy widzisz, że ma on wartość 1, ale konstruktor , , ma `DoSomething()` `PersonStuff()` wartość 0 dla swojej wartości? Obecnie w konstruktorze nie ma kodu, który używa innej klasy.

Co zrobić, jeśli umieścisz kod w konstruktorze, który używa innej klasy? Oto, co możesz uzyskać:

![Przykład sprzężenia klas 3](media/class-coupling-example-3.png)

Teraz konstruktor wyraźnie zawiera kod, który używa innej klasy, a metryka sprzężenia klasy pokazuje ten fakt. Ponownie można zobaczyć, że ogólny sprzężenie klas dla jest 1, a także 1, aby pokazać, że używana jest tylko jedna klasa zewnętrzna niezależnie od tego, ile kodu wewnętrznego z `PersonStuff()` `DoSomething()` niego korzysta.

Następnie utwórz kolejną nową klasę. Nadaj tej klasie nazwę i utwórz w jej obrębie kilka właściwości:

![Przykład sprzężenia klas — dodawanie nowej klasy](media/class-coupling-example-add-new-class.png)

Teraz zużyj klasę w `DoSomething()` naszej metodzie w klasie i ponownie oblicz `PersonStuff` metryki kodu:

![Przykład sprzężenia klas 4](media/class-coupling-example-4.png)

Jak widać, sprzężenie klas dla klasy PersonStuff wynosi do 2, a jeśli przejdziesz do szczegółów klasy, zobaczysz, że metoda zawiera najwięcej sprzężeń, ale konstruktor nadal zużywa tylko `DoSomething()` 1 klasę.  Korzystając z tych metryk, można wyświetlić ogólną maksymalną liczbę dla danej klasy i przejść do szczegółów dla poszczególnych członków.

## <a name="the-magic-number"></a>Magiczny numer

Podobnie jak w przypadku skomplikowanej złożoności, nie ma żadnego limitu, który pasuje do wszystkich organizacji. Jednak [S2010](#s2010) wskazuje, że limit 9 jest optymalny:

"W związku z tym uwzględniamy wartości progowe [...] najskuteczniejszy. Te wartości progowe (dla pojedynczego członka) to CBO = 9[...]". (dodano wyróżnienie)

## <a name="code-analysis"></a>Analiza kodu

Analiza kodu obejmuje kategorię Reguł konserwacji. Aby uzyskać więcej informacji, zobacz [Reguły konserwacji](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). W przypadku korzystania ze starszej analizy kodu zestaw rozszerzonych wytycznych projektowych zawiera obszar konserwacji:

![Rozszerzone reguły wywłaszcze projektu sprzężenia klas](media/class-coupling-extended-design-guideline-rules.png)

Wewnątrz obszaru konserwacji znajduje się reguła sprzężenia klas:

![Reguła sprzężenia klas](media/class-coupling-maintainability-area-rules.png)

Ta reguła wydaje ostrzeżenie, gdy sprzężenie klas jest nadmierne. Aby uzyskać więcej informacji, zobacz [CA1506: Unikaj nadmiernego sprzężenia klas](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

## <a name="citations"></a>Cytatów

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Pakiet metryk dla projektowania obiektowego (transakcje IEEE dotyczące inżynierii oprogramowania, tom 20, nie. 6). Pobrana 14 maja 2011 r. z witryny internetowej Uniwersytetu Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

);aili, H., Keller, R.,Cznaman, F. i Saint-Czna, G. (2000). Zmiana klas ponownie: Badanie empiryczne dotyczące systemów przemysłowych (Proceedings of the Workshop on Quantitative Approaches in Object-Oriented Software Engineering). Pobrano 20 maja 2011 r. z witryny internetowej w Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Empiryczna analiza metryk PChN dla złożoności projektu Object-Oriented: Implikacje dotyczące wad oprogramowania (transakcje IEEE dotyczące inżynierii oprogramowania, tom 29, nie. 4). Pobrano 14 maja 2011 r., z witryny internetowej Uniwersytetu w Chicago [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Ilościowe badanie akceptowalnych poziomów ryzyka metryk Object-Oriented w systemach Open-Source (transakcje IEEE dotyczące inżynierii oprogramowania, tom 36, nie. 2).

### <a name="yc79"></a>YC79

Paul Yourdon i Larry L. Constantine. Structured Design (Projekt strukturalny). Prentice Hall, Englewood Cliffs, N.J., 1979.