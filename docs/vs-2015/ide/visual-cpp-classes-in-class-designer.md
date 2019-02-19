---
title: Klasy Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 04392545b5b5c352a35b9a3d523f0c6ff5d98b01
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787079"
---
# <a name="visual-c-classes-in-class-designer"></a>Klasy Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje klasy języka C++ i umożliwia wizualizowanie klas natywnych języka C++ w taki sam sposób jak kształty klasy Visual Basic i Visual C#, z tą różnicą, że klasy C++ może istnieć wiele relacji dziedziczenia. Można rozwinąć kształt klasy, aby wyświetlić więcej pól i metod w klasie lub Zwiń go do oszczędzania przestrzeni dyskowej.  
  
> [!NOTE]
>  Projektant klas nie obsługuje Unii (specjalny typ klasy, w której pamięć przydzielona jest niezbędne dla Unii zajmuje największy element członkowski danych ilość).  
  
## <a name="simple-inheritance"></a>Proste dziedziczenie  
 Przeciągnij więcej niż jednej klasy na diagramie klasy, gdy klasy mają relację dziedziczenia klasy, Strzałka łączy je. Wskazuje strzałka w kierunku klasy bazowej. Na przykład gdy następujące klasy są wyświetlane na diagramie klasy, Strzałka łączy je, wskazującą z B na A:  
  
```  
class A {};  
class B : A {};  
```  
  
 Możesz również przeciągnąć klasy B do diagramu klas, kliknij prawym przyciskiem myszy kształt klasy B, a następnie kliknij **Pokaż klasy podstawowej**. Spowoduje to wyświetlenie jej klasa bazowa: A.  
  
## <a name="multiple-inheritance"></a>Dziedziczenie wielokrotne  
 Projektant klasy obsługuje wizualizację relacji dziedziczenia wielu klas. *Dziedziczenie wielokrotne* jest używany, gdy klasa pochodna zawiera atrybuty więcej niż jednej klasy bazowej. Poniżej przedstawiono przykład wielokrotnego dziedziczenia:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Przeciągnij więcej niż jednej klasy na diagramie klasy, gdy klasy mają relację dziedziczenia wielu klas, Strzałka łączy je. Wskazuje strzałka w kierunku klas bazowych.  
  
 Kliknij prawym przyciskiem myszy kształt klasy, a następnie klikając polecenie **Pokaż klasy podstawowe** Wyświetla klas bazowych dla wybranej klasy.  
  
> [!NOTE]
>  **Pokaż klasy pochodne** polecenie nie jest obsługiwane dla kodu C++. Klasy pochodne można wyświetlić, przechodząc do widoku klas, rozwijając węzeł typu, rozszerzając **typów pochodnych** podfolder, a następnie przeciągając tych typów na diagramie klasy.  
  
 Aby uzyskać więcej informacji na temat dziedziczenia klas wielu zobacz [dziedziczenie wielokrotne (NOTINBUILD)](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) i [wiele klas podstawowych](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).  
  
## <a name="abstract-classes"></a>Klasy abstrakcyjne  
 Projektant klasy obsługuje klasy abstrakcyjne (zwaną również "abstrakcyjnych klas bazowych"). Są to klasy, która nigdy nie wystąpienia, ale z którego można uzyskać innych klas. Przy użyciu przykładu z "Wielokrotne dziedziczenie" wcześniej w tym dokumencie, może być wystąpienia `Bird` klasy jako pojedyncze obiekty w następujący sposób:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Jednak może nie zamierzasz utworzyć wystąpienie `Swimmer` klasy jako pojedyncze obiekty. Zamierzasz tylko do innych typów klas zwierząt od niej pochodzić, na przykład `Penguin`, `Whale`, i `Fish`. W takim przypadku może zadeklarować `Swimmer` klasy jako abstrakcyjna klasa bazowa.  
  
 Aby zadeklarować klasy jako abstrakcyjnej, można użyć `abstract` — słowo kluczowe. Elementy członkowskie oznaczony jako abstrakcyjny lub zawarte w klasie abstrakcyjnej, wirtualne i musi być implementowane przez klasy, które pochodzą z klasy abstrakcyjnej.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 Można również zadeklarować klasy jako abstrakcyjny, przez co najmniej jedną czystą mfunkcję wirtualną:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Po wyświetleniu tych deklaracji na diagramie klasy, nazwa klasy `Swimmer` i jego czystą funkcję wirtualną `swim` w wyświetlanych kursywą kształtu klasę abstrakcyjną, wraz z notacji **klasę abstrakcyjną**. Zwróć uwagę, że kształt typu klasy abstrakcyjnej jest taka sama, jak w przypadku zwykłej klasy, z tą różnicą, że jej obramowanie jest linię kropkowaną.  
  
 Klasy pochodzącej od abstrakcyjna klasa bazowa musi przesłonić metodę każdego czystej funkcji wirtualnej w klasie bazowej lub nie można utworzyć wystąpienia klasy pochodnej. Tak więc, na przykład w przypadku klasy wyprowadzonej `Fish` klasy z `Swimmer` klasy `Fish` przesłonięcie `swim` metody:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Gdy ten kod jest wyświetlana na diagramie klasy, Projektant klas rysuje linię dziedziczenia z `Fish` do `Swimmer`.  
  
## <a name="anonymous-classes"></a>Klasy anonimowe  
 Projektant klasy obsługuje klasy anonimowe. *Anonimowe typy klas* klasy są deklarowane bez identyfikatora. One nie może mieć Konstruktor lub destruktor nie mogą być przekazywane jako argumenty do funkcji i nie może być zwracane jako wartości zwracane przez funkcje. Można użyć klasy anonimowe, aby zastąpić nazwę typedef, jak w poniższym przykładzie nazwa klasy:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Struktury mogą być również anonimowe. Projektant klas Wyświetla anonimowe klasy i struktury takie same, jak jest wyświetlana odpowiedniego typu. Mimo że można zadeklarować i wyświetlić anonimowe klas i struktur, Projektant klas nie będzie używać nazwa tagu, który określisz. Nazwa która generuje widoku klasy zostanie użyty. Klasy lub struktury jest wyświetlana w widoku klas i projektanta klas jako element o nazwie **__unnamed**.  
  
 Aby uzyskać więcej informacji na temat klasy anonimowe, zobacz [anonimowe typy klas](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).  
  
## <a name="template-classes"></a>Klasy szablonów  
 Projektant klasy obsługuje wizualizacji klasy szablonu. Zagnieżdżone deklaracje są obsługiwane. W poniższej tabeli przedstawiono kilka typowych deklaracji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Klasa szablonu|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasa szablonu|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Klasa szablonu|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasa szablonu|  
  
 W poniższej tabeli przedstawiono kilka przykładów częściowej specjalizacji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Klasa szablonu|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Klasa szablonu|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Klasa szablonu|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Klasa szablonu|  
  
 W poniższej tabeli przedstawiono kilka przykładów dziedziczenia w składowej specjalizacji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Klasa szablonu<br /><br /> `B`<br /><br /> Class<br /><br /> (wskazuje klasy A)<br /><br /> `C`<br /><br /> Class<br /><br /> (wskazuje klasy A)|  
  
 W poniższej tabeli przedstawiono kilka przykładów częściowa specjalizacja szablonu funkcji.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> FUNC\<T, N > (+ przeciążenie 1)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Klasa szablonu<br /><br /> `B<T2>`<br /><br /> Klasa szablonu<br /><br /> (B znajduje się w obrębie klasy A w obszarze **typy zagnieżdżone**)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Class<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Klasa szablonu|  
  
 W poniższej tabeli przedstawiono kilka przykładów szablon dziedziczenia.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Class<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Class<br /><br /> (B znajduje się w obrębie klasy C w ramach **typy zagnieżdżone**)<br /><br /> `C<T>`<br /><br /> Klasa szablonu|  
  
 W poniższej tabeli przedstawiono kilka przykładów klas wyspecjalizowanych canonical połączenia.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Class<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Class<br /><br /> `C<T>`<br /><br /> Klasa szablonu<br /><br /> `D`<br /><br /> Class<br /><br /> ->C\<float>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T >|  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klasy i struktury](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [Anonimowe typy klas](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)   
 [(NOTINBUILD) Dziedziczenie wielokrotne](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Wiele klas podstawowych](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)   
 [Szablony](http://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)
