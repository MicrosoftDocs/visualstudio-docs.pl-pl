---
title: Debugowanie naruszenie zasad dostępu C++ | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 02/05/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2be6c13e2a3c83d31540399dd3387addb08e8686
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895133"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>W jaki sposób można debugować naruszenie zasad dostępu C++?

## <a name="problem-description"></a>Opis problemu

Program powoduje naruszenie zasad dostępu. W jaki sposób można to debugować?

## <a name="solution"></a>Rozwiązanie

Jeśli w wierszu kodu, który wyłuskań wielu wskaźników naruszenie zasad dostępu, może być trudne dowiedzieć się, wskaźnika, który spowodował naruszenie zasad dostępu. Począwszy od programu Visual Studio 2015 Update 1, okno dialogowe wyjątku teraz jawnie nazwy wskaźnika, który spowodował naruszenie zasad dostępu.

Na przykład biorąc pod uwagę następujący kod, należy uzyskać naruszenie zasad dostępu:

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

Jeśli uruchomisz ten kod w Visual Studio 2015 Update 1, powinny zostać wyświetlone następujące okno dialogowe wyjątku:

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

Jeśli nie można ustalić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, prześledzi kod, aby upewnić się, że wskaźnik przyczyną problemu jest poprawnie przypisany.  Jeśli został przekazany jako parametr, upewnij się, że jest prawidłowo przekazane i nie są przypadkowe tworzenie [skrócona kopiowania](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Następnie sprawdź, czy wartości są nie przypadkowo zmieniane gdzieś w programie, tworząc upewnij się, że nie są modyfikowane w innym miejscu w programie dany punkt przerwania danych zostanie wskaźnika. Aby uzyskać więcej informacji na temat punkty przerwania danych, zobacz sekcję punktu przerwania danych w [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)