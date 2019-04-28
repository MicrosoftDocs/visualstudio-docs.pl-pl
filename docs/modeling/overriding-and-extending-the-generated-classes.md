---
title: Zastępowanie i rozszerzanie wygenerowanych klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa4f39fb54617ae1dbf048a1e13f009c8df5185
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814240"
---
# <a name="override-and-extend-the-generated-classes"></a>Przesłanianie i rozszerzanie wygenerowanych klas

Definicji DSL jest platformy, na której można budować z zaawansowanego zestawu narzędzi, które są oparte na języka specyficznego dla domeny. Wiele rozszerzeń i dostosowania można wybierać, zastępowanie i rozszerzanie klas, które są generowane na podstawie definicji DSL. W ramach tych zajęć, obejmują nie tylko klasy domeny, które jawnie zdefiniowane w diagramem definicji DSL, ale także innych klas, które definiują przybornika, Eksplorator, serializacja i tak dalej.

## <a name="extensibility-mechanisms"></a>Mechanizmy rozszerzalności

Podano kilka mechanizmów pozwalają rozszerzyć wygenerowanego kodu.

### <a name="override-methods-in-a-partial-class"></a>Przesłaniaj metody w klasie częściowej

Częściowych definicji klasy umożliwiają klas zdefiniowanych w więcej niż jednego miejsca. Dzięki temu można oddzielić wygenerowany kod od kodu, który można napisać samodzielnie. W kodzie napisanych ręcznie można zastąpić klasy dziedziczone przez wygenerowany kod.

Na przykład, jeśli w definicji DSL zdefiniujesz klasę domeny o nazwie `Book`, można napisać kod niestandardowy, który dodaje zastąpienie metody:

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
> Aby zastąpić metody w generowanej klasie, należy zawsze pisanie kodu w pliku, który jest oddzielony od wygenerowanych plików. Zazwyczaj plik znajduje się w folderze, który jest nazwany atrybut CustomCode. Jeśli wprowadzisz zmiany w wygenerowanym kodzie mogą zostaną utracone podczas ponownego generowania kodu z definicji DSL.

Aby dowiedzieć się, jakie metody, można zastąpić, wpisz **zastąpienia** w klasie, następuje spacja. Etykietka funkcji IntelliSense poinformuje, jakie metody może zostać zastąpiona.

### <a name="double-derived-classes"></a>Klasy pochodne podwójnej precyzji

Większość metod w wygenerowanych klas są dziedziczone z stały zestaw klas w przestrzeniach nazw modelowania. Jednak niektóre metody są zdefiniowane w wygenerowanym kodzie. Zwykle oznacza to, że nie można przesłonić. na jednych zajęciach częściowych nie można zastąpić metody, które są zdefiniowane w innej definicji częściowej tej samej klasy.

Niemniej jednak można zastąpić tych metod, ustawiając **Generates Double Derived** flagi dla klasy domeny. To powoduje, że dwie klasy do wygenerowania, jest abstrakcyjna klasa bazowa innych. Wszystkie definicje metod i właściwości są w klasie bazowej, a tylko Konstruktor znajduje się w klasie pochodnej.

Na przykład, na przykład Library.dsl `CirculationBook` klasa domeny ma `Generates``Double Derived` właściwością `true`. Kod generowany dla tej klasy domeny zawiera dwie klasy:

- `CirculationBookBase`, która jest abstrakcyjny i który zawiera wszystkie metody i właściwości.

- `CirculationBook`, który pochodzi od `CirculationBookBase`. Jest pusta, z wyjątkiem jego konstruktorów.

Aby zastąpić dowolną metodę, tworzysz częściową definicję klasy pochodnej, takich jak `CirculationBook`. Można zastąpić wygenerowane metody i metod odziedziczone framework modelowania.

Metoda ta jest przydatna ze wszystkimi typami elementu, w tym elementy modelu, relacje, kształty, diagramy i łączniki. Można również zastąpić metod innych wygenerowanych klas. Niektóre generowane klasy, takie jak ToolboxHelper są zawsze pochodzi podwójnej precyzji.

### <a name="custom-constructors"></a>Konstruktory niestandardowe

Nie można zastąpić konstruktora. Nawet w przypadku klas pochodnych podwójnej precyzji Konstruktor musi być w klasie pochodnej.

Jeśli chcesz podać własne konstruktora, możesz to zrobić, ustawiając `Has Custom Constructor` dla klasy domeny w definicji DSL. Po kliknięciu **Przekształć wszystkie szablony**, wygenerowany kod nie będzie zawierać konstruktor dla tej klasy. Będzie on zawierał wywołanie konstruktora brakuje. To powoduje, że raport o błędach podczas kompilowania rozwiązania. Kliknij dwukrotnie raport o błędach, aby wyświetlić komentarze w wygenerowanym kodzie, który objaśnia, należy podać.

Zapisywanie definicji częściowej klasy w pliku, który jest oddzielony od wygenerowanych plików, a następnie podaj konstruktora.

### <a name="flagged-extension-points"></a>Oflagowane punkty rozszerzenia

Punkt rozszerzenia oflagowanych to miejsce w definicji DSL, w którym można ustawić właściwość lub pole wyboru, aby wskazać, zapewni niestandardowej metody. Niestandardowe konstruktory są jednym z przykładów. To ustawienie `Kind` właściwości domena obliczeniowa, Magazyn niestandardowy lub ustawienie **jest niestandardowa** Flaga konstruktora połączeń.

W każdym przypadku, gdy należy ustawić flagę i ponownie wygenerować kod, spowoduje wystąpienie błędu kompilacji. Kliknij dwukrotnie błąd, aby wyświetlić komentarz, który wyjaśnia, co trzeba podać.

### <a name="rules"></a>reguły

Menedżer transakcji umożliwia definiowanie reguł, które uruchamiane przed zakończeniem transakcji, w którym wystąpiło zdarzenie wyznaczonym, takie jak zmiany właściwości. Reguły są zwykle używane do obsługi synchronism między różne elementy w magazynie. Na przykład reguły są używane, aby upewnić się, że diagram przedstawia bieżący stan modelu.

Reguły są definiowane na podstawie klasy, tak, aby nie trzeba mieć kod, który rejestruje reguły dla każdego obiektu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Zdarzenia Store

Magazyn modelowania udostępnia mechanizm zdarzeń, który można użyć do nasłuchiwania pod kątem określonych rodzajów zmian w magazynie, w tym dodawania i usuwania elementów zmiany wartości właściwości i tak dalej. Programy obsługi zdarzeń są nazywane po zamknięciu transakcji, w którym zostały wprowadzone zmiany. Zazwyczaj te zdarzenia są używane do zaktualizowania zasobów spoza sklepu.

### <a name="net-events"></a>Zdarzenia platformy .NET

Można subskrybować niektóre zdarzenia w kształtach. Na przykład możesz nasłuchiwać kliknięć myszą na kształcie. Trzeba napisać kod, która ją subskrybuje zdarzenia dla każdego obiektu. Ten kod można pisać w zastąpieniu obiektu InitializeInstanceResources().

Niektóre zdarzenia są generowane na ShapeFields, które są używane do rysowania dekoratory na kształcie. Aby uzyskać przykład, zobacz [jak: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Te zdarzenia nie występują zwykle wewnątrz transakcji. Należy utworzyć transakcji, jeśli chcesz wprowadzić zmiany w magazynie.