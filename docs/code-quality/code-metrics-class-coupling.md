---
title: Metryki kodu — sprzęganie klas
ms.date: 1/8/2021
description: Dowiedz się więcej o metryki sprzęgania klas w programie Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8320c460faf7532887364693080d38c0ff6baa6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860519"
---
# <a name="code-metrics---class-coupling"></a>Metryki kodu — sprzęganie klas

Sprzęganie klas jest również nadawany przez Sprzęganie nazw między obiektami (CBO), jak pierwotnie zdefiniowane przez [CK94](#ck94). W zasadzie sprzęganie klasowe jest miarą liczby klas używanych przez jedną klasę. Duża liczba jest zła, a niska liczba jest zazwyczaj dobrym razem z tą metryką. Sprzęganie klas zostało pokazane jako dokładne przewidywalność awarii oprogramowania, a ostatnie badania pokazują, że górny limit wartości 9 to najbardziej wydajny [S2010](#s2010).

Zgodnie z dokumentacją firmy Microsoft sprzęganie klas "mierzy sprzężenie do unikatowych klas za pomocą parametrów, zmiennych lokalnych, typów zwracanych, wywołań metod, wystąpień ogólnych lub szablonów, klas bazowych, implementacji interfejsów, pól zdefiniowanych w typach zewnętrznych i dekoracji atrybutu. Dobre projektowanie oprogramowania oznacza, że typy i metody powinny mieć wysoką spójność i niskie sprzężenie. Duże sprzężenie wskazuje, że projekt jest trudno używany i konserwowany ze względu na wiele współzależności z innymi typami ".

Koncepcje sprzężenia i spójności są wyraźnie powiązane. Aby zachować tę dyskusję w temacie, nie dowiesz się więcej o spójności, która nie zawiera krótkiej definicji z [KKLS2000](#kkls2000):

"Spójność modułu została wprowadzona przez Yourdon i Constantine jako" jak ściśle powiązane lub powiązane z wewnętrznymi elementami modułu należy do siebie nawzajem " [YC79](#yc79). Moduł ma silną spójność, jeśli reprezentuje dokładnie jedno zadanie [...], a wszystkie jego elementy współtworzą to pojedyncze zadanie. Określają one spójność jako atrybut projektu, a nie kod i atrybut, który może służyć do przewidywania wykorzystania, utrzymania i możliwości zmiany ".

## <a name="class-coupling-example"></a>Przykład sprzęgania klasy

Przyjrzyjmy się przyłączeniu klasy do działania. Najpierw utwórz nową aplikację konsolową i Utwórz nową klasę o nazwie Person z kilkoma właściwościami, a następnie natychmiast Oblicz metryki kodu:

![Przykład sprzęgu klasy 1](media/class-coupling-example-1.png)

Należy zauważyć, że sprzęganie klas ma wartość 0, ponieważ ta klasa nie używa żadnych innych klas. Teraz Utwórz inną klasę o nazwie PersonStuff z metodą, która tworzy wystąpienie osoby i ustawia wartości właściwości. Ponownie Oblicz metryki kodu:

![Przykład sprzęgu klasy 2](media/class-coupling-example-2.png)

Zobaczyć, jak działa wartość sprzęgania klasy? Zwróć również uwagę, że niezależnie od tego, jak wiele ustawionych właściwości, wartość sprzęgu klasy jest przychodząca o 1, a nie przez inną wartość. Sprzęganie klasowe mierzy każdej klasy tylko raz dla tej metryki, niezależnie od jej użycia. Ponadto, czy można zobaczyć, że `DoSomething()` ma 1, ale Konstruktor, `PersonStuff()` , ma 0 dla jego wartości? Obecnie w konstruktorze nie ma kodu, który używa innej klasy.

Co zrobić, jeśli umieścisz kod w konstruktorze, który używał innej klasy? Oto co otrzymujesz:

![Przykład sprzęgu klasy 3](media/class-coupling-example-3.png)

Teraz Konstruktor wyraźnie ma kod, który używa innej klasy, a Metryka sprzęgania klas pokazuje ten fakt. Ponownie można zobaczyć ogólne sprzężenia klasy dla `PersonStuff()` wynosi 1, a `DoSomething()` także 1, aby pokazać, że tylko jedna Klasa zewnętrzna jest używana niezależnie od tego, ile kodu wewnętrznego jest używany.

Następnie utwórz kolejną nową klasę. Nadaj tej klasie nazwę i Utwórz w niej pewne właściwości:

![Przykład sprzęgania klasy — Dodaj nową klasę](media/class-coupling-example-add-new-class.png)

Teraz Użyj klasy w naszej `DoSomething()` metodzie w `PersonStuff` klasie i ponownie Oblicz metryki kodu:

![Przykład sprzęgu klasy 4](media/class-coupling-example-4.png)

Jak widać, Sprzęganie klasy dla klasy PersonStuff przechodzi do 2 i, w przypadku przechodzenia do szczegółów klasy, można zobaczyć, że `DoSomething()` Metoda ma najwięcej sprzęgu, ale Konstruktor nadal wykorzystuje 1 klasę.  Korzystając z tych metryk, można zobaczyć ogólną maksymalną liczbę dla danej klasy i przejść do szczegółów dotyczących poszczególnych elementów członkowskich.

## <a name="the-magic-number"></a>Magiczna liczba

Podobnie jak w przypadku złożoności cyklomatyczna, nie ma żadnego limitu zgodnego ze wszystkimi organizacjami. Jednak [S2010](#s2010) wskazuje, że limit 9 jest optymalny:

"Dlatego rozważamy wartości progowe [...] najwydajniejszie. Te wartości progowe (dla pojedynczego elementu członkowskiego) to CBO = 9 [...]. (wyróżnienie dodane)

## <a name="code-analysis"></a>Analiza kodu

Analiza kodu obejmuje kategorię reguł zarządzania. Aby uzyskać więcej informacji, zobacz [zasady zarządzania](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). W przypadku korzystania ze starszej wersji analizy kodu rozszerzona reguła wytycznych projektowych zawiera obszar utrzymania:

![Rozszerzone reguły wskazówek dotyczących projektowania sprzęgania klas](media/class-coupling-extended-design-guideline-rules.png)

W obszarze łatwość utrzymania jest to reguła sprzęgania klas:

![Reguła sprzęgania klas](media/class-coupling-maintainability-area-rules.png)

Ta reguła powoduje wygenerowanie ostrzeżenia w przypadku nadmiernego sprzęgania klas. Aby uzyskać więcej informacji, zobacz [CA1506: Unikaj nadmiernego sprzęgania klas](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Aby uzyskać opis tej reguły, zobacz wpis w blogu analiza zarchiwizowanych kodów: [metryki kodu jako zasady ewidencjonowania](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) i ostrzeżenia o opisie progowym *o powyżej 80 dla klasy i powyżej 30 dla metody*.  Te wartości są nietypowe, ale co najmniej zapewnia górny limit. Po osiągnięciu tego ostrzeżenia coś jest niemal niewłaściwe.

## <a name="citations"></a>Cytowań

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Pakiet metryk dla projektowania zorientowanego obiektowo (IEEE Transactions w inżynierii oprogramowania, vol. 20, No. 6). Pobrano 14 maja 2011 z witryny sieci Web University of Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F. i Saint-Denis, G. (2000). Oglądany spójności klasy: badanie analityczne w systemach przemysłowych (postępowania warsztatów dotyczących ilościowych metod w Object-Oriented inżynieria oprogramowania). Pobrano 20 maja 2011 z witryny sieci Web Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Analiza analityczna metryk z SOCZEWKami dla Object-Oriented złożoności projektu: implikacje dla wad oprogramowania (IEEE Transactions, Tom. 29, No. 4). Pobrano 14 maja 2011 z University of Massachusetts Darmouth Web site [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Badanie ilościowe dopuszczalnych poziomów ryzyka Object-Oriented metryki w systemach Open-Source (IEEE Transactions, vol. 36, No. 2).

### <a name="yc79"></a>YC79

Edward Yourdon i Larry L. Constantine. Projektowanie strukturalne. Prentice, Englewood Cliffs, N.J., 1979.