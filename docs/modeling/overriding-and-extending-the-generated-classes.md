---
title: Zastępowanie i rozszerzanie wygenerowanych klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3374f67f4fba11543e3dbbca47fef621dd2e714
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595894"
---
# <a name="override-and-extend-the-generated-classes"></a>Przesłoń i rozwiń wygenerowane klasy

Definicja DSL jest platformą, na której można utworzyć zaawansowany zestaw narzędzi opartych na języku specyficznym dla domeny. Wiele rozszerzeń i adaptacji można wprowadzać przez zastępowanie i rozszerzanie klas, które są generowane na podstawie definicji DSL. Klasy te zawierają nie tylko klasy domeny, które zostały jawnie zdefiniowane w diagramie definicji DSL, ale również inne klasy, które definiują Przybornik, Eksploratora, serializacji i tak dalej.

## <a name="extensibility-mechanisms"></a>Mechanizmy rozszerzalności

Dostępnych jest kilka mechanizmów umożliwiających rozbudowanie wygenerowanego kodu.

### <a name="override-methods-in-a-partial-class"></a>Przesłoń metody w klasie częściowej

Częściowe definicje klas umożliwiają zdefiniowanie klasy w więcej niż jednym miejscu. Dzięki temu możesz oddzielić wygenerowany kod od kodu, który napiszesz samodzielnie. W kodzie ręcznym, można przesłonić klasy dziedziczone przez wygenerowany kod.

Na przykład, jeśli w definicji DSL definiujesz klasę domeny o nazwie `Book` , można napisać niestandardowy kod, który dodaje metody zastąpień:

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
> Aby przesłonić metody w generowanej klasie, należy zawsze pisać kod w pliku, który jest oddzielony od wygenerowanych plików. Zazwyczaj plik jest zawarty w folderze o nazwie atrybut CustomCode. Jeśli wprowadzisz zmiany w wygenerowanym kodzie, zostaną one utracone w przypadku ponownego wygenerowania kodu z definicji DSL.

Aby poznać metody, które można przesłonić, wpisz **przesłonięcie** w klasie, po którym następuje spacja. Etykietka narzędzia IntelliSense informuje, jakie metody można przesłaniać.

### <a name="double-derived-classes"></a>Klasy pochodne podwójnie

Większość metod w wygenerowanych klasach jest dziedziczona ze stałego zestawu klas w przestrzeni nazw modelowania. Jednak niektóre metody są zdefiniowane w wygenerowanym kodzie. Zwykle oznacza to, że nie można ich zastąpić; nie można przesłonić w jednej częściowej klasie metod, które są zdefiniowane w innej częściowej definicji tej samej klasy.

Niemniej jednak można zastąpić te metody przez ustawienie opcji **Generuj podwójną flagę pochodną** dla klasy domeny. Powoduje to wygenerowanie dwóch klas, jedną z nich jest abstrakcyjną klasą bazową drugiej. Wszystkie definicje metody i właściwości znajdują się w klasie bazowej, a tylko Konstruktor znajduje się w klasie pochodnej.

Na przykład w bibliotece Sample. DSL `CirculationBook` Klasa domeny ma `Generates``Double Derived` ustawioną właściwość `true` . Wygenerowany kod dla tej klasy domeny zawiera dwie klasy:

- `CirculationBookBase`, który jest abstrakcyjny i zawiera wszystkie metody i właściwości.

- `CirculationBook`, który pochodzi od `CirculationBookBase` . Jest ona pusta, z wyjątkiem konstruktorów.

Aby zastąpić każdą metodę, należy utworzyć częściową definicję klasy pochodnej, na przykład `CirculationBook` . Można zastąpić zarówno wygenerowane metody, jak i metody dziedziczone z struktury modelowania.

Tej metody można użyć z wszystkimi typami elementów, w tym elementami modelu, relacjami, kształtami, diagramami i łącznikami. Można również przesłonić metody innych wygenerowanych klas. Niektóre wygenerowane klasy, takie jak ToolboxHelper, są zawsze wyprowadzane podwójnie.

### <a name="custom-constructors"></a>Konstruktory niestandardowe

Nie można zastąpić konstruktora. Nawet w przypadku klas o podwójnej pochodnej Konstruktor musi znajdować się w klasie pochodnej.

Aby zapewnić własny Konstruktor, można to zrobić przez ustawienie `Has Custom Constructor` klasy domeny w definicji DSL. Po kliknięciu przycisku **Przekształć wszystkie szablony**, wygenerowany kod nie będzie zawierać konstruktora dla tej klasy. Będzie zawierać wywołanie brakującego konstruktora. Powoduje to raport o błędach podczas kompilowania rozwiązania. Kliknij dwukrotnie raport o błędach, aby wyświetlić komentarz w wygenerowanym kodzie, który wyjaśnia, co należy podać.

Napisz częściową definicję klasy w pliku, który jest oddzielony od wygenerowanych plików, i podaj konstruktora.

### <a name="flagged-extension-points"></a>Oflagowane punkty rozszerzenia

Oflagowany punkt rozszerzenia to miejsce w definicji DSL, w którym można ustawić właściwość lub pole wyboru, aby wskazać, że zostanie określona metoda niestandardowa. Konstruktory niestandardowe są jednym przykładem. Inne przykłady obejmują ustawienie `Kind` właściwości domeny na obliczeniową lub niestandardową magazyn lub ustawienie flagi **is Custom** w konstruktorze połączenia.

W każdym przypadku, gdy ustawisz flagę i wygenerujesz ponownie kod, zostanie zwrócony błąd kompilacji. Kliknij dwukrotnie błąd, aby wyświetlić komentarz wyjaśniający, co należy podać.

### <a name="rules"></a>Reguły

Menedżer transakcji umożliwia definiowanie reguł, które są uruchamiane przed końcem transakcji, w której wystąpiło określone zdarzenie, takie jak zmiana właściwości. Reguły są zwykle używane do obsługi synchronism między różnymi elementami w sklepie. Na przykład reguły są używane do upewnienia się, że na diagramie jest wyświetlany bieżący stan modelu.

Reguły są definiowane dla poszczególnych klas, dzięki czemu nie trzeba mieć kodu, który rejestruje regułę dla każdego obiektu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Zdarzenia ze sklepu

Magazyn modelowania udostępnia mechanizm zdarzeń, którego można użyć do nasłuchiwania określonych typów zmian w magazynie, w tym dodawania i usuwania elementów, zmiany wartości właściwości i tak dalej. Procedury obsługi zdarzeń są wywoływane po zamknięciu transakcji, w której zostały wprowadzone zmiany. Zwykle te zdarzenia są używane do aktualizowania zasobów poza magazynem.

### <a name="net-events"></a>Zdarzenia platformy .NET

Możesz subskrybować niektóre zdarzenia na kształtach. Na przykład można nasłuchiwać kliknięć myszą na kształcie. Musisz napisać kod, który subskrybuje zdarzenie dla każdego obiektu. Ten kod można napisać w przesłonięciu InitializeInstanceResources ().

Niektóre zdarzenia są generowane w ShapeFields, które są używane do rysowania dekoratory na kształcie. Aby zapoznać się z przykładem, zobacz [How to: przechwycenie kliknięcia kształtu lub dekoratora](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Te zdarzenia zazwyczaj nie występują w obrębie transakcji. Jeśli chcesz wprowadzić zmiany w sklepie, należy utworzyć transakcję.
