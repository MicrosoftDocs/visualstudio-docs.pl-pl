---
title: Debugowanie naruszenia zasad dostępu w języku C++ | Microsoft Docs
description: Zobacz porady dotyczące rozwiązywania problemów z naruszeniem dostępu, gdy kandydatem jest więcej niż jeden wskaźnik. Ostatnie wersje Visual Studio nazwę błędnego wskaźnika.
ms.custom: SEO-VS-2020
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3689942c9db9fde3598590cf30100fc590c50753
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387037"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Jak można debugować naruszenie dostępu w języku C++?

## <a name="problem-description"></a>Opis problemu

Mój program powoduje naruszenie zasad dostępu. Jak można to debugować?

## <a name="solution"></a>Rozwiązanie

Jeśli w wierszu kodu, który wyłuska wiele wskaźników, zostanie naruszeń dostępu, znalezienie wskaźnika, który spowodował naruszenie dostępu, może być trudne. Począwszy od Visual Studio 2015 Update 1, w oknie dialogowym wyjątku jawnie nadaj wskaźnikowi nazwę, która spowodowała naruszenie dostępu.

Na przykład, biorąc pod uwagę następujący kod, powinno zostać naruszeń dostępu:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Jeśli ten kod zostanie uruchomiony w wersji Visual Studio 2015 Update 1, powinno zostać wyświetlone następujące okno dialogowe wyjątku:

![Zrzut ekranu przedstawiający Microsoft Visual Studio wyjątku dostępu do odczytu dla "A->B was nullptr". Przycisk Przerwij jest wybrany.](../debugger/media/accessviolationcplus.png)

Jeśli nie możesz ustalić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, prześledzić kod, aby upewnić się, że wskaźnik powodujący problem został prawidłowo przypisany.  Jeśli jest przekazywany jako parametr, upewnij się, że został on przekazany poprawnie [](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)i nie zostanie przypadkowo utworzenie pobie]. Następnie sprawdź, czy wartości nie są niezamierzonie zmieniane w programie, tworząc punkt przerwania danych dla wskaźnika, aby upewnić się, że nie jest on modyfikowany w innym miejscu w programie. Aby uzyskać więcej informacji na temat punktów przerwania danych, zobacz sekcję punkt przerwania danych w [tesłudze.](../debugger/using-breakpoints.md)

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)