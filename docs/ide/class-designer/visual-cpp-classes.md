---
title: Klasy języka C++ w projektancie klas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d68391bbd4c6c873940bbc2714ee41db8309b629
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590738"
---
# <a name="c-classes-in-class-designer"></a>Klasy języka C++ w projektancie klas

**Projektant klas** obsługuje klasy C++ i wizualizuje natywne klasy C++ w taki sam sposób, jak kształty klas Visual Basic i C#, z tą różnicą, że klasy C++ mogą mieć wiele relacji dziedziczenia. Można rozwinąć kształt klasy, aby wyświetlić więcej pól i metod w klasie lub zwinąć go, aby zaoszczędzić miejsce.

> [!NOTE]
> **Projektant klas** nie obsługuje związków (specjalny typ klasy, w którym przydzielona pamięć jest tylko kwotą niezbędną dla największego elementu członkowskiego danych unii).

## <a name="simple-inheritance"></a>Proste dziedziczenie

Podczas przeciągania więcej niż jednej klasy na diagram klasy, a klasy mają relację dziedziczenia klasy, strzałka łączy je. Strzałka wskazuje kierunek klasy podstawowej. Na przykład, gdy na diagramie klasy są wyświetlane następujące klasy, łączy je strzałka, wskazując od B do A:

```cpp
class A {};
class B : A {};
```

Można również przeciągnąć tylko klasę B do diagramu klas, kliknąć prawym przyciskiem myszy kształt klasy dla B, a następnie kliknąć polecenie **Pokaż klasy podstawowe**. Spowoduje to wyświetlenie jego klasy podstawowej: A.

## <a name="multiple-inheritance"></a>Wielokrotne dziedziczenie

**Projektant klas** obsługuje wizualizację relacji dziedziczenia wielu klas. *Wielokrotne dziedziczenie* jest używane, gdy klasa pochodna ma atrybuty więcej niż jednej klasy podstawowej. Poniżej znajduje się przykład wielokrotnego dziedziczenia:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Po przeciągnięciu więcej niż jednej klasy na diagram klas, a klasy mają relację dziedziczenia wielu klas, strzałka łączy je. Strzałka wskazuje kierunek klas podstawowych.

Kliknięcie prawym przyciskiem myszy kształtu klasy, a następnie kliknięcie przycisku **Pokaż klasy podstawowe** powoduje wyświetlenie klas podstawowych dla wybranej klasy.

> [!NOTE]
> Polecenie **Pokaż klasy pochodne** nie jest obsługiwane dla kodu C++. Klasy pochodne można wyświetlić, przechodząc do **widoku klasy,** rozwijając węzeł typu, rozwijając podfolder **Typy pochodne,** a następnie przeciągając te typy na diagram klas.

Aby uzyskać więcej informacji na temat dziedziczenia wielu klas, zobacz [Wiele dziedziczenia](https://msdn.microsoft.com/library/6td5yws2.aspx) i [Wiele klas podstawowych](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Klasy abstrakcyjne

**Projektant klas** obsługuje klasy abstrakcyjne (nazywane również "abstrakcyjnymi klasami podstawowymi"). Są to klasy, które nigdy nie występują, ale z których można wyprowadzić inne klasy. Przy pomocy an przykład z " wielokrotny dziedziczenie" `Bird` wcześniej w ten udokumentować, możesz utworzyć wystąpienia ten klasyfikować równie pojedynczy przedmioty równie następujący:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Jednak nie zamierzasz utworzyć wystąpienia `Swimmer` klasy jako poszczególne obiekty. Można mieć zamiar tylko wyprowadzić z niego inne rodzaje `Penguin` `Whale`klas `Fish`zwierząt, na przykład , i . W takim przypadku należy `Swimmer` zadeklarować klasę jako abstrakcyjną klasę podstawową.

Aby zadeklarować klasę jako abstrakcyjną, można użyć słowa kluczowego. `abstract` Elementy członkowskie oznaczone jako abstrakcyjne lub zawarte w klasie abstrakcyjnej są wirtualne i muszą być implementowane przez klasy, które pochodzą z klasy abstrakcyjnej.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Można również zadeklarować klasę jako abstrakcyjną, dołączając co najmniej jedną czystą funkcję wirtualną:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Podczas wyświetlania tych deklaracji na diagramie `Swimmer` klas, nazwa `swim` klasy i jej czysta funkcja wirtualna są wyświetlane kursywą w abstrakcyjnym kształcie klasy, wraz z notacją **Klasa abstrakcyjna**. Należy zauważyć, że kształt typu klasy abstrakcyjnej jest taki sam jak w klasie regularnej, z tą różnicą, że jego obramowanie jest linią kropkowana.

Klasa pochodząca z abstrakcyjnej klasy podstawowej musi zastąpić każdą czystą funkcję wirtualną w klasie podstawowej lub nie można utworzyć wystąpienia klasy pochodnej. Tak więc, na przykład, `Fish` jeśli pochodzisz klasy z `Swimmer` klasy, `Fish` należy zastąpić `swim` metodę:

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

Po wyświetleniu tego kodu na diagramie klas projektant `Fish` `Swimmer` **klas** rysuje linię dziedziczenia od do .

## <a name="anonymous-classes"></a>Klasy anonimowe

**Projektant klas** obsługuje klasy anonimowe. *Typy klas anonimowych* są klasy zadeklarowane bez identyfikatora. Nie mogą mieć konstruktora lub destruktora, nie mogą być przekazywane jako argumenty do funkcji i nie mogą być zwracane jako wartości zwracane z funkcji. Klasy anonimowej można użyć do zastąpienia nazwy klasy nazwą typedef, jak w poniższym przykładzie:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Struktury mogą być również anonimowe. **Projektant klas** wyświetla anonimowe klasy i struktury takie same, jak wyświetla odpowiedni typ. Chociaż można deklarować i wyświetlać anonimowe klasy i struktury, **Projektant klas** nie będzie używać nazwy znacznika, który określisz. Użyje nazwy, którą generuje widok klasy. Klasa lub struktura pojawia się w widoku klasy i **projektancie klas** jako element o nazwie **__unnamed**.

Aby uzyskać więcej informacji na temat klas anonimowych, zobacz [Typy klas anonimowych](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Klasy szablonów

**Projektant klas** obsługuje wizualizację klas szablonów. Obsługiwane są deklaracje zagnieżdżone. W poniższej tabeli przedstawiono niektóre typowe deklaracje.

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

W poniższej tabeli przedstawiono kilka przykładów dziedziczenia w częściowej specjalizacji.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Klasa szablonu<br /><br /> `B`<br /><br /> Klasa<br /><br /> (punkty klasy A)<br /><br /> `C`<br /><br /> Klasa<br /><br /> (punkty klasy A)|

W poniższej tabeli przedstawiono kilka przykładów funkcji szablonu specjalizacji częściowej.

|Element Code|Widok projektanta klas|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 przeciążenie)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Klasa szablonu<br /><br /> `B<T2>`<br /><br /> Klasa szablonu<br /><br /> (B znajduje się w klasie A w obszarze **Typy zagnieżdżone)**|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Klasa<br /><br /> ->> C\<int<br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów dziedziczenia szablonu.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Klasa<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Klasa<br /><br /> (B znajduje się w klasie C w obszarze **Typy zagnieżdżone)**<br /><br /> `C<T>`<br /><br /> Klasa szablonu|

W poniższej tabeli przedstawiono kilka przykładów kanonicznego połączenia klasy specjalistycznej.

|Element Code|Widok projektanta klas|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Klasa<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Klasa<br /><br /> `C<T>`<br /><br /> Klasa szablonu<br /><br /> `D`<br /><br /> Klasa<br /><br /> ->> pływakowe C\<|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>Zobacz też

- [Praca z kodem C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [Anonimowe typy klas](/cpp/cpp/anonymous-class-types)
- [Dziedziczenie wielokrotne](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Wiele klas podstawowych](/cpp/cpp/multiple-base-classes)
- [Szablony](/cpp/cpp/templates-cpp)
