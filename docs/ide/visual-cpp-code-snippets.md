---
title: Visual C++ fragmenty kodu
description: Dowiedz się, jak za pomocą fragmentów kodu dodać często używany kod do plików kodu języka C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: e5cde2be817c49344e02ff06030022f99790a7a2
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478812"
---
# <a name="visual-c-code-snippets"></a>Visual C++ fragmenty kodu

W programie Visual Studio można użyć fragmentów kodu, aby dodać powszechnie używany kod do plików kodu C++. Ogólnie rzecz biorąc, można użyć fragmentów kodu w taki sam sposób jak w języku C#, ale zestaw domyślnych fragmentów kodu jest inny.

Można dodać fragment kodu w określonej lokalizacji w kodzie (wstawianie) lub otoczyć fragmentem wybranego kodu kodem.

## <a name="insert-a-code-snippet"></a>Wstaw fragment kodu

Aby wstawić fragment kodu, Otwórz plik kodu C++ (*. cpp* lub *. h*), kliknij w dowolnym miejscu w pliku i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz **Wstaw fragment kodu**

- W menu **Edytuj/IntelliSense** wybierz pozycję **Wstaw fragment kodu**

- Użyj klawiszy skrótów: **Ctrl** + **K** + **X**

Powinna zostać wyświetlona lista opcji rozpoczynających się od **#if**. Po wybraniu **#if** do pliku powinien zostać wyświetlony następujący kod:

```cpp
#if 0

#endif // 0
```

Następnie można zastąpić **0** prawidłowym warunkiem.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Używanie fragmentu kodu do otaczania zaznaczonego kodu

Aby użyć fragmentu kodu do otaczania zaznaczonego kodu, wybierz wiersz (lub wiele wierszy) i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz opcję **Otocz za pomocą**

- Z menu **Edytuj**  >  **IntelliSense** wybierz opcję **Otocz z**

- Za pomocą klawiatury, naciśnij klawisze: **Ctrl** + **K** + **S**

Wybierz **#if**. Powinny zostać wyświetlone informacje podobne do następujących:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Następnie można zastąpić 0 prawidłowym warunkiem.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Gdzie mogę znaleźć kompletną listę fragmentów kodu języka C++?

Pełną listę fragmentów kodu języka C++ można znaleźć, przechodząc do **Menedżera fragmentów kodu** (w menu **Narzędzia** ) i ustawiając **Język** na **Visual C++**. W oknie poniżej rozwiń węzeł **Visual C++**. Nazwy wszystkich fragmentów kodu języka C++ powinny być widoczne w kolejności alfabetycznej.

Nazwy większości fragmentów kodu są oczywiste, ale niektóre nazwy mogą być mylące.

## <a name="class-vs-classi"></a>Klasa a identyfikator klasy

Fragment **klasy** zawiera definicję klasy o nazwie `MyClass` , z odpowiednim konstruktorem domyślnym i destruktorem, gdzie definicje konstruktora i destruktora znajdują się poza klasą:

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

Fragment kodu **identyfikatora ClassID** również zawiera definicję klasy o nazwie `MyClass` , ale Konstruktor domyślny i destruktor są zdefiniowane wewnątrz definicji klasy:

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

## <a name="for-vs-forr-vs-rfor"></a>dla programu vs. dla vs rfor

Istnieją trzy **różne fragmenty kodu** , które udostępniają różne rodzaje `for` pętli.

Fragment kodu **rfor** zawiera pętlę for (link) [opartą na zakresie](/cpp/cpp/range-based-for-statement-cpp) . Ta konstrukcja jest preferowana przez pętle oparte na indeksie `for` .

```cpp
for (auto& i : v)
{

}
```

Wstawka **na potrzeby** zawiera `for` pętlę, w której warunek jest oparty na długości (w `size_t` ) obiektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Fragment kodu **dla** zawiera pętlę odwrotną, `for` w której warunek jest oparty na długości (w postaci liczb całkowitych) obiektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment kodu destruktora (~)

Fragment kodu destruktora ( **~** ) pokazuje inne zachowanie w różnych kontekstach. Jeśli wstawię ten fragment wewnątrz klasy, zapewnia destruktor dla tej klasy. Na przykład, mając następujący kod:

```cpp
class SomeClass {

};
```

Po wstawieniu fragmentu destruktora zapewnia destruktor dla `SomeClass` :

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Jeśli spróbujesz wstawić fragment destruktora poza klasą, zapewnia destruktor z nazwą symbolu zastępczego:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)