---
title: Zastępowanie i rozszerzanie wygenerowanych klas
description: Dowiedz się, jak definicja DSL to platforma, na której można utworzyć zaawansowany zestaw narzędzi opartych na języku specyficznym dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07c44e7ff7a603f339ec268b06bd78cc84cd6be2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390948"
---
# <a name="override-and-extend-the-generated-classes"></a>Zastępowanie i rozszerzanie wygenerowanych klas

Definicja DSL to platforma, na której można utworzyć zaawansowany zestaw narzędzi opartych na języku specyficznym dla domeny. Wiele rozszerzeń i adaptacji można tworzyć przez zastępowanie i rozszerzanie klas, które są generowane na podstawie definicji DSL. Te klasy obejmują nie tylko klasy domeny, które zostały jawnie zdefiniowane w diagramie definicji DSL, ale także inne klasy, które definiują przybornik, eksploratora, serializacji i tak dalej.

## <a name="extensibility-mechanisms"></a>Mechanizmy rozszerzalności

Istnieje kilka mechanizmów, które umożliwiają rozszerzenie wygenerowanego kodu.

### <a name="override-methods-in-a-partial-class"></a>Zastępowanie metod w klasie częściowej

Definicje klas częściowych umożliwiają definiowanie klasy w więcej niż jednym miejscu. Dzięki temu można oddzielić wygenerowany kod od kodu, który piszesz samodzielnie. W ręcznie napisanym kodzie można przesłonić klasy dziedziczone przez wygenerowany kod.

Jeśli na przykład w definicji DSL zdefiniujesz klasę domeny o nazwie , możesz napisać kod niestandardowy, który `Book` dodaje metody przesłonięcia:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Aby zastąpić metody w wygenerowanej klasie, zawsze zapisuj kod w pliku oddzielonym od wygenerowanych plików. Zazwyczaj plik znajduje się w folderze o nazwie CustomCode. Jeśli wprowadzasz zmiany w wygenerowanym kodzie, zostaną one utracone podczas ponownego generowania kodu z definicji DSL.

Aby dowiedzieć się, jakie metody można przesłonić, wpisz **przesłonięcie** w klasie, a następnie spację. Etykietka narzędzia IntelliSense pokaże, jakie metody można przesłonić.

### <a name="double-derived-classes"></a>Double-Derived klasy

Większość metod w wygenerowanych klasach jest dziedziczona ze stałego zestawu klas w przestrzeniach nazw modelowania. Jednak niektóre metody są zdefiniowane w wygenerowanym kodzie. Zwykle oznacza to, że nie można ich zastąpić; Nie można przesłonić w jednej częściowej klasy metod zdefiniowanych w innej częściowej definicji tej samej klasy.

Niemniej jednak można przesłonić te metody, ustawiając flagę **Generuje podwójne** pochodne dla klasy domeny. Powoduje to wygenerowanie dwóch klas, z których jedna jest abstrakcyjną klasą bazową drugiej. Wszystkie definicje metod i właściwości znajdują się w klasie bazowej, a tylko konstruktor znajduje się w klasie pochodnej.

Na przykład w przykładowym bibliotece Library.dsl klasa `CirculationBook` domeny ma `Generates``Double Derived` właściwość ustawioną na `true` . Wygenerowany kod dla tej klasy domeny zawiera dwie klasy:

- `CirculationBookBase`, który jest abstrakcją i który zawiera wszystkie metody i właściwości.

- `CirculationBook`, który pochodzi od klasy `CirculationBookBase` . Jest pusty, z wyjątkiem jego konstruktorów.

Aby zastąpić dowolną metodę, należy utworzyć częściową definicję klasy pochodnej, taką jak `CirculationBook` . Można przesłonić zarówno wygenerowane metody, jak i metody dziedziczone z struktury modelowania.

Tej metody można używać ze wszystkimi typami elementów, w tym elementami modelu, relacjami, kształtami, diagramami i łącznikami. Można również przesłonić metody innych wygenerowanych klas. Niektóre wygenerowane klasy, takie jak PrzybornikHelper, są zawsze dwupozyteczne.

### <a name="custom-constructors"></a>Konstruktory niestandardowe

Nie można przesłonić konstruktora. Nawet w klasach z podwójnymi pochodnymi konstruktor musi znajdować się w klasie pochodnej.

Jeśli chcesz podać własny konstruktor, możesz to zrobić, ustawiając dla klasy `Has Custom Constructor` domeny w definicji DSL. Po kliknięciu **przycisku Przekształć** wszystkie szablony wygenerowany kod nie będzie zawierać konstruktora dla tej klasy. Będzie on zawierać wywołanie brakującego konstruktora. Spowoduje to zgłoszenie błędu podczas kompilowania rozwiązania. Kliknij dwukrotnie raport o błędach, aby zobaczyć komentarz w wygenerowanym kodzie, który wyjaśnia, co należy podać.

Zapisz definicję klasy częściowej w pliku, który jest oddzielony od wygenerowanych plików i podaj konstruktor.

### <a name="flagged-extension-points"></a>Oflagowane punkty rozszerzeń

Oflagowany punkt rozszerzenia to miejsce w definicji DSL, w którym można ustawić właściwość lub pole wyboru, aby wskazać, że należy podać metodę niestandardową. Konstruktory niestandardowe są jednym z przykładów. Inne przykłady obejmują ustawienie właściwości domeny na Wartość obliczeniowa lub Magazyn niestandardowy albo ustawienie `Kind` flagi **Jest** niestandardowe w konstruktorze połączeń.

W każdym przypadku, gdy ustawisz flagę i ponownie wygenerujemy kod, zostanie wygenerowany błąd kompilacji. Kliknij dwukrotnie błąd, aby wyświetlić komentarz wyjaśniacy, co należy podać.

### <a name="rules"></a>Reguły

Menedżer transakcji umożliwia definiowanie reguł uruchamianych przed końcem transakcji, w którym wystąpiło wyznaczone zdarzenie, takie jak zmiana właściwości. Reguły są zwykle używane do utrzymania pomięć między różnymi elementami w magazynie. Na przykład reguły są używane w celu upewninia się, że na diagramie jest wyświetlany bieżący stan modelu.

Reguły są definiowane dla poszczególnych klas, dzięki czemu nie trzeba mieć kodu, który rejestruje regułę dla każdego obiektu. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Przechowywanie zdarzeń

Magazyn modelowania udostępnia mechanizm zdarzeń, który umożliwia nasłuchiwać określonych typów zmian w magazynie, w tym dodawanie i usuwanie elementów, zmiany wartości właściwości i tak dalej. Procedury obsługi zdarzeń są wywoływane po zamknięciu transakcji, w której zostały wprowadzone zmiany. Zazwyczaj te zdarzenia są używane do aktualizowania zasobów poza magazynem.

### <a name="net-events"></a>Zdarzenia .NET

Możesz subskrybować niektóre zdarzenia na kształtach. Na przykład możesz nasłuchiwać kliknięć myszą na kształcie. Musisz napisać kod, który subskrybuje zdarzenie dla każdego obiektu. Ten kod można zapisywać w przesłonięciu metody InitializeInstanceResources().

Niektóre zdarzenia są generowane w polach ShapeField, które są używane do rysowania dekoratorów na kształcie. Aby uzyskać przykład, zobacz [How to: Intercept a Click on a Shape (Jak przechwycić kliknięcie) lub Decorator (Dekorator).](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)

Te zdarzenia zwykle nie występują wewnątrz transakcji. Należy utworzyć transakcję, jeśli chcesz wprowadzić zmiany w magazynie.
