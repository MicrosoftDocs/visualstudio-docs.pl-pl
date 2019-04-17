---
title: Klasy Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b8312e0db76dd3ce064172116aecd82daab56e90
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664667"
---
# <a name="visual-c-classes-in-class-designer"></a>Wizualne klasy języka C++ w Projektancie klas

**Projektant klasy** obsługuje klasy języka C++ i umożliwia wizualizowanie klas natywnych języka C++ w taki sam sposób, jak Visual Basic i C# klasy kształtów, z tą różnicą, że klasy C++ może istnieć wiele relacji dziedziczenia. Można rozwinąć kształt klasy, aby wyświetlić więcej pól i metod w klasie lub Zwiń go do oszczędzania przestrzeni dyskowej.

> [!NOTE]
> **Projektant klasy** nie obsługuje Unii (specjalny typ klasy, w której pamięć przydzielona jest niezbędne dla Unii zajmuje największy element członkowski danych ilość).

## <a name="simple-inheritance"></a>Proste dziedziczenie

Przeciągnij więcej niż jednej klasy na diagramie klasy, gdy klasy mają relację dziedziczenia klasy, Strzałka łączy je. Wskazuje strzałka w kierunku klasy bazowej. Na przykład gdy następujące klasy są wyświetlane na diagramie klasy, Strzałka łączy je, wskazującą z B na A:

```cpp
class A {};
class B : A {};
```

Możesz również przeciągnąć klasy B do diagramu klas, kliknij prawym przyciskiem myszy kształt klasy B, a następnie kliknij **Pokaż klasy podstawowej**. Spowoduje to wyświetlenie jej klasa bazowa: A.

## <a name="multiple-inheritance"></a>Dziedziczenie wielokrotne

**Projektant klasy** obsługuje wizualizację relacji dziedziczenia wielu klas. *Dziedziczenie wielokrotne* jest używany, gdy klasa pochodna zawiera atrybuty więcej niż jednej klasy bazowej. Poniżej przedstawiono przykład wielokrotnego dziedziczenia:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Przeciągnij więcej niż jednej klasy na diagramie klasy, gdy klasy mają relację dziedziczenia wielu klas, Strzałka łączy je. Wskazuje strzałka w kierunku klas bazowych.

Kliknij prawym przyciskiem myszy kształt klasy, a następnie klikając polecenie **Pokaż klasy podstawowe** Wyświetla klas bazowych dla wybranej klasy.

> [!NOTE]
> **Pokaż klasy pochodne** polecenie nie jest obsługiwane dla kodu C++. Klasy pochodne można wyświetlić, przechodząc do **Widok klas**, rozwijając węzeł typu, rozszerzając **typów pochodnych** podfolder, a następnie przeciągając tych typów na diagramie klasy.

Aby uzyskać więcej informacji na temat dziedziczenia klas wielu zobacz [wielokrotne dziedziczenie](https://msdn.microsoft.com/library/6td5yws2.aspx) i [wiele klas podstawowych](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Klasy abstrakcyjne

**Projektant klasy** obsługuje abstrakcyjnej klasy (zwaną również "abstrakcyjne klasy podstawowe"). Są to klasy, która nigdy nie wystąpienia, ale z którego można uzyskać innych klas. Przy użyciu przykładu z "Wielokrotne dziedziczenie" wcześniej w tym dokumencie, może być wystąpienia `Bird` klasy jako pojedyncze obiekty w następujący sposób:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Jednak może nie zamierzasz utworzyć wystąpienie `Swimmer` klasy jako pojedyncze obiekty. Zamierzasz tylko do innych typów klas zwierząt od niej pochodzić, na przykład `Penguin`, `Whale`, i `Fish`. W takim przypadku może zadeklarować `Swimmer` klasy jako abstrakcyjna klasa bazowa.

Aby zadeklarować klasy jako abstrakcyjnej, można użyć `abstract` — słowo kluczowe. Elementy członkowskie oznaczony jako abstrakcyjny lub zawarte w klasie abstrakcyjnej, wirtualne i musi być implementowane przez klasy, które pochodzą z klasy abstrakcyjnej.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Można również zadeklarować klasy jako abstrakcyjny, przez co najmniej jedną czystą mfunkcję wirtualną:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Po wyświetleniu tych deklaracji na diagramie klasy, nazwa klasy `Swimmer` i jego czystą funkcję wirtualną `swim` w wyświetlanych kursywą kształtu klasę abstrakcyjną, wraz z notacji **klasę abstrakcyjną**. Zwróć uwagę, że kształt typu klasy abstrakcyjnej jest taka sama, jak w przypadku zwykłej klasy, z tą różnicą, że jej obramowanie jest linię kropkowaną.

Klasy pochodzącej od abstrakcyjna klasa bazowa musi przesłonić metodę każdego czystej funkcji wirtualnej w klasie bazowej lub nie można utworzyć wystąpienia klasy pochodnej. Tak więc, na przykład w przypadku klasy wyprowadzonej `Fish` klasy z `Swimmer` klasy `Fish` przesłonięcie `swim` metody:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Gdy ten kod jest wyświetlana na diagramie klasy **projektanta klas** rysuje linię dziedziczenia z `Fish` do `Swimmer`.

## <a name="anonymous-classes"></a>Klasy anonimowe

**Projektant klasy** obsługuje klasy anonimowe. *Anonimowe typy klas* klasy są deklarowane bez identyfikatora. One nie może mieć Konstruktor lub destruktor nie mogą być przekazywane jako argumenty do funkcji i nie może być zwracane jako wartości zwracane przez funkcje. Można użyć klasy anonimowe, aby zastąpić nazwę typedef, jak w poniższym przykładzie nazwa klasy:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Struktury mogą być również anonimowe. **Projektant klasy** Wyświetla anonimowe klasy i struktury takie same, jak jest wyświetlana odpowiedniego typu. Mimo że można zadeklarować i wyświetlić anonimowe klas i struktur, **projektanta klas** nie będzie używać nazwa tagu, który określisz. Nazwa która generuje widoku klasy zostanie użyty. Klasy lub struktury jest wyświetlana w widoku klas i **projektanta klas** jako element o nazwie **__unnamed**.

Aby uzyskać więcej informacji na temat klasy anonimowe, zobacz [anonimowe typy klas](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Klasy szablonów

**Projektant klasy** obsługuje wizualizacji klasy szablonu. Zagnieżdżone deklaracje są obsługiwane. W poniższej tabeli przedstawiono kilka typowych deklaracji.

| Element Code | Widok projektanta klas |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Klasa szablonu |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Klasa szablonu |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Klasa szablonu |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Klasa szablonu |

W poniższej tabeli przedstawiono kilka przykładów częściowej specjalizacji.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasa szablonu|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Klasa szablonu|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Klasa szablonu|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów dziedziczenia w składowej specjalizacji.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Klasa szablonu<br /><br /> `B`<br /><br /> Class<br /><br /> (wskazuje klasy A)<br /><br /> `C`<br /><br /> Class<br /><br /> (wskazuje klasy A)|

W poniższej tabeli przedstawiono kilka przykładów częściowa specjalizacja szablonu funkcji.

|Element Code|Widok projektanta klas|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> FUNC\<T, N > (+ przeciążenie 1)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Klasa szablonu<br /><br /> `B<T2>`<br /><br /> Klasa szablonu<br /><br /> (B znajduje się w obrębie klasy A w obszarze **typy zagnieżdżone**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Class<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów szablon dziedziczenia.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Class<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Class<br /><br /> (B znajduje się w obrębie klasy C w ramach **typy zagnieżdżone**)<br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów klas wyspecjalizowanych canonical połączenia.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Class<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Class<br /><br /> `C<T>`<br /><br /> Klasa szablonu<br /><br /> `D`<br /><br /> Class<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T >|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [Anonimowe typy klas](/cpp/cpp/anonymous-class-types)
- [Dziedziczenie wielokrotne](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Wiele klas podstawowych](/cpp/cpp/multiple-base-classes)
- [Szablony](/cpp/cpp/templates-cpp)