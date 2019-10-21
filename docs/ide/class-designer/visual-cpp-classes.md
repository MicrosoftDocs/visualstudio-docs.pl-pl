---
title: Klasy Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 596d7a41b9f63179a0469840d948430ed0294b56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647639"
---
# <a name="visual-c-classes-in-class-designer"></a>Klasy C++ wizualne w Projektant klas

**Projektant klas** obsługuje C++ klasy i wizualizacje klas C++ macierzystych w taki sam sposób jak w C# przypadku Visual Basic i kształtów klas C++ , z wyjątkiem tego, że klasy mogą mieć wiele relacji dziedziczenia. Można rozwinąć kształt klasy, aby wyświetlić więcej pól i metod w klasie, lub zwinąć go, aby zaoszczędzić miejsce.

> [!NOTE]
> **Projektant klas** nie obsługuje Unii (specjalny typ klasy, w której przydzielono pamięć jest tylko ilością potrzebną dla największego elementu członkowskiego danych Unii).

## <a name="simple-inheritance"></a>Dziedziczenie proste

Po przeciągnięciu więcej niż jednej klasy na Diagram klas, a klasy mają relację dziedziczenia klasy, strzałka łączy je. Strzałka wskazuje kierunek klasy bazowej. Na przykład gdy następujące klasy są wyświetlane na diagramie klas, strzałka łączy je, wskazując od B do A:

```cpp
class A {};
class B : A {};
```

Możesz również przeciągnąć tylko klasę B do diagramu klasy, kliknij prawym przyciskiem myszy kształt klasy dla B, a następnie kliknij polecenie **Pokaż klasy bazowe**. Spowoduje to wyświetlenie klasy podstawowej: A.

## <a name="multiple-inheritance"></a>Wielokrotne dziedziczenie

**Projektant klas** obsługuje wizualizację relacji dziedziczenia z wieloma klasami. *Wielokrotne dziedziczenie* jest używane, gdy Klasa pochodna ma atrybuty więcej niż jednej klasy bazowej. Poniżej przedstawiono przykład dziedziczenia wielokrotnego:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Po przeciągnięciu więcej niż jednej klasy na Diagram klas, a klasy mają relację dziedziczenia z wieloma klasami, strzałka łączy je. Strzałka wskazuje kierunek klas bazowych.

Kliknięcie prawym przyciskiem myszy kształtu klasy, a następnie kliknięcie pozycji **Pokaż klasy podstawowe** powoduje wyświetlenie klas bazowych dla wybranej klasy.

> [!NOTE]
> Polecenie **Pokaż klasy pochodne** nie jest obsługiwane dla C++ kodu. Klasy pochodne można wyświetlić, przechodząc do **Widok klasy**, rozszerzając węzeł typu, rozwijając podfolder **Typy pochodne** , a następnie przeciągając te typy na Diagram klas.

Aby uzyskać więcej informacji na temat dziedziczenia z wieloma klasami, zobacz [wielokrotne dziedziczenie](https://msdn.microsoft.com/library/6td5yws2.aspx) i [wiele klas podstawowych](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Klasy abstrakcyjne

**Projektant klas** obsługuje klasy abstrakcyjne (nazywane również "abstrakcyjnymi klasami podstawowymi"). Są to klasy, które nigdy nie występują, ale z których można utworzyć inne klasy. Korzystając z przykładu z "wielokrotne dziedziczenie" wcześniej w tym dokumencie, można utworzyć wystąpienie klasy `Bird` jako pojedyncze obiekty w następujący sposób:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Nie można jednak utworzyć wystąpienia klasy `Swimmer` jako pojedynczych obiektów. Można jedynie utworzyć inne typy klas zwierzęcia, na przykład `Penguin`, `Whale` i `Fish`. W takim przypadku należy zadeklarować klasę `Swimmer` jako abstrakcyjną klasę bazową.

Aby zadeklarować klasę jako abstrakcyjną, można użyć słowa kluczowego `abstract`. Elementy członkowskie oznaczone jako abstrakcyjne lub zawarte w klasie abstrakcyjnej są wirtualne i muszą być zaimplementowane przez klasy pochodne od klasy abstrakcyjnej.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Można również zadeklarować klasę jako abstrakcyjną poprzez dołączenie co najmniej jednej czystej funkcji wirtualnej:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Po wyświetleniu tych deklaracji w diagramie klas nazwa klasy `Swimmer` i jej czysta funkcja wirtualna `swim` są wyświetlane kursywnie w kształcie klasy abstrakcyjnej, wraz z **klasą abstrakcyjną**notacji. Zwróć uwagę, że kształt typu klasy abstrakcyjnej jest taki sam jak w przypadku zwykłej klasy, z tą różnicą, że jej obramowanie jest linią kropkowaną.

Klasa pochodna z abstrakcyjnej klasy bazowej musi przesłonić każdą czystą funkcję wirtualną w klasie podstawowej lub nie można utworzyć wystąpienia klasy pochodnej. Aby na przykład utworzyć klasę `Fish` z klasy `Swimmer`, `Fish` musi zastąpić metodę `swim`:

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

Po wyświetleniu tego kodu w diagramie klas **Projektant klas** rysuje linię dziedziczenia z `Fish` do `Swimmer`.

## <a name="anonymous-classes"></a>Klasy anonimowe

**Projektant klas** obsługuje klasy anonimowe. *Anonimowe typy klas* to klasy zadeklarowane bez identyfikatora. Nie mogą one mieć konstruktora ani destruktora, nie mogą być przekazane jako argumenty do funkcji i nie mogą być zwracane jako wartości zwracane z funkcji. Można użyć anonimowej klasy, aby zastąpić nazwę klasy nazwą typedef, jak w poniższym przykładzie:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Struktury mogą być również anonimowe. **Projektant klas** wyświetla anonimowe klasy i struktury tak samo, jak w przypadku wyświetlania odpowiedniego typu. Chociaż można zadeklarować i wyświetlić anonimowe klasy i struktury, **Projektant klas** nie użyje nazwy tagu, którą określisz. Zostanie użyta nazwa generowana Widok klasy. Klasa lub struktura pojawia się w Widok klasy i **Projektant klas** jako element o nazwie **__unnamed**.

Aby uzyskać więcej informacji na temat klas anonimowych, zobacz [anonimowe typy klas](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Klasy szablonów

**Projektant klas** obsługuje wizualizację klas szablonów. Deklaracje zagnieżdżone są obsługiwane. W poniższej tabeli przedstawiono niektóre typowe deklaracje.

| Element Code | Widok Projektant klas |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Klasa szablonu |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Klasa szablonu |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Klasa szablonu |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Klasa szablonu |

W poniższej tabeli przedstawiono kilka przykładów częściowej specjalizacji.

|Element Code|Widok Projektant klas|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasa szablonu|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Klasa szablonu|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Klasa szablonu|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów dziedziczenia w częściowej specjalizacji.

|Element Code|Widok Projektant klas|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Klasa szablonu<br /><br /> `B`<br /><br /> Class<br /><br /> (wskazuje klasę A)<br /><br /> `C`<br /><br /> Class<br /><br /> (wskazuje klasę A)|

W poniższej tabeli przedstawiono kilka przykładów funkcji szablonu częściowej specjalizacji.

|Element Code|Widok Projektant klas|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U > (przeciążanie + 1)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Klasa szablonu<br /><br /> `B<T2>`<br /><br /> Klasa szablonu<br /><br /> (B jest zawarty w klasie A w **zagnieżdżonych typach**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Class<br /><br /> -> C \<int ><br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów dziedziczenia szablonów.

|Element Code|Widok Projektant klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Class<br /><br /> -> B<br /><br /> `C<int>`<br /><br /> Class<br /><br /> (B jest zawarty w klasie C w **zagnieżdżonych typach**)<br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów kanonicznych, wyspecjalizowanych połączeń klas.

|Element Code|Widok Projektant klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Class<br /><br /> -> C \<int ><br /><br /> `C<int>`<br /><br /> Class<br /><br /> `C<T>`<br /><br /> Klasa szablonu<br /><br /> `D`<br /><br /> Class<br /><br /> -> C \<float >|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Minimalna \<T >|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [Anonimowe typy klas](/cpp/cpp/anonymous-class-types)
- [Wielokrotne dziedziczenie](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Wiele klas podstawowych](/cpp/cpp/multiple-base-classes)
- [Szablony](/cpp/cpp/templates-cpp)