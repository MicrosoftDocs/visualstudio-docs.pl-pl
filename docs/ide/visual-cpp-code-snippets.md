---
title: Fragmenty kodu w usłudze Visual C++
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: de27b201dadb23bb8209ebee24b34386f8fa5127
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581763"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kodu w usłudze Visual C++

W programie Visual Studio umożliwia fragmenty kodu Dodaj kod często używane w plikach kodu języka C++. Ogólnie rzecz biorąc fragmenty kodu można użyć w podobny sposób jak w języku C#, ale zbiór fragmentów kodu domyślna jest inna.

Możesz dodać fragment kodu w danej lokalizacji w kodzie (wstawiania) lub przestrzenny zaznaczonego kodu przy użyciu fragmentu kodu.

## <a name="insert-a-code-snippet"></a>Wstaw fragment kodu

Aby wstawić fragment kodu, otwórz plik kodu C++ (*.cpp* lub *.h*), a następnie kliknij dowolne miejsce wewnątrz pliku i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **Wstaw fragment kodu**

- W **Edytuj / IntelliSense** menu, wybierz opcję **Wstaw fragment kodu**

- Użyj klawiszy dostępu: **Ctrl**+**K**+**X**

Powinien zostać wyświetlony listę opcji, począwszy od **#if**. Po wybraniu **#if**, powinien zostać wyświetlony następujący kod, które są dodawane do pliku:

```cpp
#if 0

#endif // 0
```

Następnie można zastąpić **0** z warunkiem poprawne.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Fragment kodu umożliwia przestrzenny, zaznaczony kod

Na potrzeby wstawki kodu programu Otocz zaznaczony kod, wybierz linię (lub wiele wierszy), a następnie wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **z funkcji Otocz przez**

- Z **Edytuj** > **IntelliSense** menu, wybierz opcję **z funkcji Otocz przez**

- Przy użyciu klawiatury, naciśnij przycisk: **Ctrl**+**K**+**S**

Wybierz **#if**. Powinien zostać wyświetlony podobny do poniższego:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Następnie można zastąpić 0 z warunkiem poprawne.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Gdzie mogę znaleźć listę wszystkich fragmentów kodu C++

Pełną listę fragmentów kodu C++ można znaleźć, przechodząc do **Menedżera wstawek kodu** (na **narzędzia** menu) i ustawienie **języka** do **Visual C++** . W poniższym oknie rozwiń **Visual C++**. Należy wyświetlić nazwy wszystkich fragmentów kodu C++ w kolejności alfabetycznej.

Nazwy większości fragmenty kodu są oczywiste, ale niektóre nazwy mogą być mylące.

## <a name="class-vs-classi"></a>Klasa a classi

**Klasy** fragment kodu zawiera definicję klasy o nazwie `MyClass`oraz odpowiedni konstruktor domyślny i destruktor, których definicje Konstruktor i destruktor znajdują się poza klasy:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

**Classi** fragment kodu udostępnia również definicję klasy o nazwie `MyClass`, ale domyślny konstruktor i destruktor, które są zdefiniowane wewnątrz definicji klasy:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>Aby uzyskać a rfor programu vs lepiej wykorzystać możliwości

Istnieją trzy różne **dla** fragmentów, które zapewniają różnego rodzaju elementu `for` pętli.

**Rfor** fragment kodu zawiera [opartej na zakresie](/cpp/cpp/range-based-for-statement-cpp) dla pętli (link). Ta konstrukcja jest preferowany w porównaniu opartego na indeksie `for` pętli.

```cpp
for (auto& i : v)
{

}
```

**Dla** fragment kodu zawiera `for` pętli, w której warunek opiera się na długość (w `size_t`) obiektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Lepiej wykorzystać możliwości** fragment kodu zawiera odwróconej `for` pętli, w której warunek opiera się na długość (w postaci liczb całkowitych) obiektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment kodu — destruktor (~)

Fragment kodu — destruktor (**~**) zawiera różne zachowanie w różnych kontekstach. Podczas wstawiania tego fragmentu kodu wewnątrz klasy, zawiera destruktor dla tej klasy. Na przykład biorąc pod uwagę następujący kod:

```cpp
class SomeClass {

};
```

Po wstawieniu fragmentu kodu destruktora, zapewnia destruktor `SomeClass`:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Jeśli zostanie podjęta próba Wstaw fragment kodu destruktor poza klasą, zawiera destruktor przy użyciu nazwy symbolu zastępczego:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)