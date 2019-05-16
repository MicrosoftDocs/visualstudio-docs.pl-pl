---
title: Fragmenty kodu Visual C++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 884ec6cc25fd2ef415dc71055361344d79021d5e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696377"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kodu Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio umożliwia fragmenty kodu Dodaj kod często używane w plikach kodu języka C++. Ogólnie rzecz biorąc fragmenty kodu można użyć w podobny sposób jak w języku C#, ale zbiór fragmentów kodu domyślna jest inna.  
  
 Możesz dodać fragment kodu w danej lokalizacji w kodzie (wstawiania) lub przestrzenny zaznaczonego kodu przy użyciu fragmentu kodu.  
  
## <a name="inserting-a-code-snippet"></a>Wstawianie fragmentu kodu  
 Aby wstawić fragment kodu, otwórz plik kodu C++ (.cpp i .h), kliknij dowolne miejsce wewnątrz pliku i wykonaj jedną z następujących czynności:  
  
- Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **Wstaw fragment kodu**  
  
- W **Edytuj / IntelliSense** menu, wybierz opcję **Wstaw fragment kodu**  
  
- Użyj klawiszy dostępu: **CTRL + K + X**  
  
  Powinien zostać wyświetlony listę opcji, począwszy od **#if**. Po wybraniu **#if**, powinien zostać wyświetlony następujący kod, które są dodawane do pliku:  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 Następnie można zastąpić 0 z warunkiem poprawne.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Przy użyciu fragmentu kodu można otoczyć zaznaczony kod  
 Na potrzeby wstawki kodu programu Otocz zaznaczony kod, wybierz linię (lub wiele wierszy), a następnie wykonaj jedną z następujących czynności:  
  
1. Kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe i wybierz **z funkcji Otocz przez**  
  
2. W **Edytuj / IntelliSense** menu, wybierz opcję **z funkcji Otocz przez**  
  
3. Użyj klawiszy dostępu: **CTRL + K + S**  
  
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
 **Klasy** fragment kodu zawiera definicję klasy o nazwie MyClass, z odpowiednimi domyślnymi Konstruktor i destruktor, gdzie definicje Konstruktor i destruktor znajdują się poza klasy:  
  
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
  
 Fragment kodu classi udostępnia również definicję klasy o nazwie MyClass, ale domyślny konstruktor i destruktor, które są zdefiniowane wewnątrz definicji klasy:  
  
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
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Aby uzyskać a foreach a rfor programu vs lepiej wykorzystać możliwości  
 Istnieją cztery różne fragmenty, które zapewniają różnego rodzaju z pętli for.  
  
 **Dla** fragment kodu zawiera `for` pętli, w której warunek opiera się na długość (w `size_t`) obiektu:  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 **Foreach** fragment kodu zawiera `for each` pętli, który iteruje po elementach członkowskich kolekcji:  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 **Lepiej wykorzystać możliwości** fragment kodu zawiera odwróconej `for` pętli, w której warunek opiera się na długość (w postaci liczb całkowitych) obiektu:  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 **Rfor** fragment kodu zawiera [opartej na zakresie](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) dla pętli (link):  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>Fragment kodu — destruktor (~)  
 Fragment kodu — destruktor (**~**) zawiera różne zachowanie w różnych kontekstach. Podczas wstawiania tego fragmentu kodu wewnątrz klasy, zawiera destruktor dla tej klasy. Na przykład biorąc pod uwagę następujący kod:  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Po wstawieniu fragmentu kodu destruktora, zapewnia destruktora SomeClass:  
  
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
