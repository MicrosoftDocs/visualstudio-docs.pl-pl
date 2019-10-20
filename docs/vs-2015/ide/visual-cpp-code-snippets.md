---
title: Fragmenty C++ kodu wizualizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 213f4299ac71c08118563a008abe065f2c02423e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655390"
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można użyć fragmentów kodu, aby dodać powszechnie używany kod do plików C++ kodu. Ogólnie rzecz biorąc, można użyć fragmentów kodu w taki sam sposób jak w C#, ale zestaw domyślnych fragmentów kodu jest inny.

 Można dodać fragment kodu w określonej lokalizacji w kodzie (wstawianie) lub otoczyć fragmentem wybranego kodu kodem.

## <a name="inserting-a-code-snippet"></a>Wstawianie fragmentu kodu
 Aby wstawić fragment kodu, Otwórz plik C++ kodu (. cpp lub. h), kliknij w dowolnym miejscu w pliku i wykonaj jedną z następujących czynności:

- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz **Wstaw fragment kodu**

- W menu **Edytuj/IntelliSense** wybierz pozycję **Wstaw fragment kodu**

- Użyj klawiszy skrótów: **Ctrl + K + X**

  Powinna zostać wyświetlona lista opcji rozpoczynających się od **#if**. Po wybraniu **#if**do pliku powinien zostać wyświetlony następujący kod:

```cpp
#if 0

#endif // 0
```

 Następnie można zastąpić 0 prawidłowym warunkiem.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Używanie fragmentu kodu do otaczania zaznaczonego kodu
 Aby użyć fragmentu kodu do otaczania zaznaczonego kodu, wybierz wiersz (lub wiele wierszy) i wykonaj jedną z następujących czynności:

1. Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz opcję **Otocz za pomocą**

2. W menu **Edytuj/IntelliSense** wybierz opcję **Otocz z**

3. Użyj klawiszy skrótu: **Ctrl + K + S**

   Wybierz **#if**. Powinieneś wyglądać następująco:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

 Następnie można zastąpić 0 prawidłowym warunkiem.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Gdzie mogę znaleźć kompletną listę fragmentów C++ kodu?
 Pełną C++ listę fragmentów kodu można znaleźć, przechodząc do **Menedżera fragmentów kodu** (w menu **Narzędzia** ) i ustawiając **Język** na **C++wizualizację**. W oknie poniżej rozwiń pozycję **Wizualizacja C++** . Nazwy wszystkich fragmentów C++ kodu powinny być widoczne w kolejności alfabetycznej.

 Nazwy większości fragmentów kodu są oczywiste, ale niektóre nazwy mogą być mylące.

## <a name="class-vs-classi"></a>Klasa a identyfikator klasy
 Fragment **klasy** zawiera definicję klasy o nazwie MyClass z odpowiednim konstruktorem domyślnym i destruktorem, gdzie definicje konstruktora i destruktora znajdują się poza klasą:

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

 Fragment kodu identyfikatora ClassID również zawiera definicję klasy o nazwie MyClass, ale domyślny Konstruktor i destruktor są zdefiniowane wewnątrz definicji klasy:

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

## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Dla programu vs. foreach a dla vs rfor
 Istnieją cztery różne fragmenty kodu, które udostępniają różne rodzaje pętli for.

 Fragment kodu zawiera pętlę **`for`, w** której warunek jest oparty na długości (w `size_t`) obiektu:

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

 Fragment kodu **foreach** zawiera pętlę `for each`, która iteruje elementy członkowskie kolekcji:

```cpp
for each (object var in collection_to_loop)
{

}
```

 Fragment kodu **dla** zawiera pętlę odwrotną `for`, w której warunek jest oparty na długości (w liczbie całkowitej) obiektu:

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

 Fragment kodu **rfor** zawiera pętlę for [bazującą na zakresie](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) (link):

```cpp
for (auto& i : v)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment kodu destruktora (~)
 Fragment kodu destruktora ( **~** ) pokazuje inne zachowanie w różnych kontekstach. Jeśli wstawię ten fragment wewnątrz klasy, zapewnia destruktor dla tej klasy. Na przykład, mając następujący kod:

```cpp
class SomeClass {

};
```

 Po wstawieniu fragmentu destruktora zapewnia destruktor dla SomeClass:

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
