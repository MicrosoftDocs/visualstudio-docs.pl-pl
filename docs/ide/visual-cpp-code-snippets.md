---
title: Fragmenty kodu języka Visual C++
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: db6ea1e233d32872322926a4d75b847ee6a49ba3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77277831"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kodu języka Visual C++

W programie Visual Studio można użyć fragmentów kodu, aby dodać często używany kod do plików kodu języka C++. Ogólnie rzecz biorąc można użyć fragmentów kodu w taki sam sposób, jak w języku C#, ale zestaw domyślnych fragmentów kodu jest inny.

Można dodać fragment kodu w określonej lokalizacji w kodzie (wstawianie) lub otoczyć wybrany kod fragmentem kodu.

## <a name="insert-a-code-snippet"></a>Wstawianie fragmentu kodu

Aby wstawić fragment kodu, otwórz plik kodu języka C++*(.cpp* lub *.h),* kliknij gdzieś wewnątrz pliku i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz polecenie **Wstaw fragment kodu**

- W menu **Edycja / IntelliSense** wybierz polecenie **Wstaw fragment kodu**

- Korzystanie z skrótów klawiszowych: **Ctrl**+**K**+**X**

Powinna zostać wyświetlona lista opcji, począwszy od **#if**. Po wybraniu **#if**powinien zostać dodany następujący kod do pliku:

```cpp
#if 0

#endif // 0
```

Następnie można zastąpić **0** właściwym warunkiem.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Używanie fragmentu kodu do otaczania wybranego kodu

Aby użyć fragmentu kodu do otoczyć wybrany kod, wybierz linię (lub wiele wierszy) i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz polecenie **Surround With**

- Z menu **Edytuj** > **intellisense** wybierz polecenie **Surround with**

- Za pomocą klawiatury naciśnij: **Ctrl**+**K**+**S**

Wybierz **#if**. Powinny zostać wyświetlone informacje podobne do następujących:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Następnie można zastąpić 0 właściwym warunkiem.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Gdzie można znaleźć pełną listę fragmentów kodu języka C++?

Pełną listę fragmentów kodu języka C++ można znaleźć, przechodząc do **Menedżera urywków kodu** (w menu **Narzędzia)** i ustawiając **język** na **Visual C++**. W oknie poniżej rozwiń pozycję **Visual C++**. Powinny być widoczne nazwy wszystkich fragmentów kodu Języka C++ w kolejności alfabetycznej.

Nazwy większości fragmentów kodu są oczywiste, ale niektóre nazwy mogą być mylące.

## <a name="class-vs-classi"></a>Klasa vs. classi

Urywek **klasy** zawiera definicję klasy `MyClass`o nazwie, z odpowiednim domyślnym konstruktorem i destruktorem, gdzie definicje konstruktora i destruktora znajdują się poza klasą:

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

Fragment kodu **classi** zawiera również definicję klasy `MyClass`o nazwie , ale domyślny konstruktor i destruktor są zdefiniowane wewnątrz definicji klasy:

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

## <a name="for-vs-forr-vs-rfor"></a>dla vs. forr vs rfor

Istnieją trzy różne **dla** urywki, `for` które zapewniają różne rodzaje pętli.

**Urywek rfor** zapewnia [zakres oparty](/cpp/cpp/range-based-for-statement-cpp) na pętli (łącze). Ta konstrukcja jest preferowana `for` w stosunku do pętli opartych na indeksie.

```cpp
for (auto& i : v)
{

}
```

**Fragment for** zapewnia pętlę, `for` w której warunek jest oparty `size_t`na długości (w) obiektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Fragment kodu **forr** zapewnia odwrotną `for` pętlę, w której warunek jest oparty na długości (w liczbach całkowitych) obiektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment kodu destruktora (~)

Fragment kodu destruktora**~**( ) pokazuje różne zachowanie w różnych kontekstach. Jeśli wstawisz ten fragment kodu wewnątrz klasy, zapewnia destruktor dla tej klasy. Na przykład, biorąc pod uwagę następujący kod:

```cpp
class SomeClass {

};
```

Jeśli wstawisz fragment destruktora, zapewnia on `SomeClass`destruktor dla:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Jeśli spróbujesz wstawić fragment kodu destruktora poza klasą, udostępnia destruktora z nazwą symbolu zastępczego:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)