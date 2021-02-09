---
title: Debugowanie naruszenia dostępu w języku C++ | Microsoft Docs
description: Zobacz Porady dotyczące rozwiązywania problemów z naruszeniem dostępu, gdy więcej niż jeden wskaźnik jest kandydatem. Najnowsze wersje programu Visual Studio mają nazwę wskaźnik errant.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 9f7e33ff34357dc0aa258f179f55d379bdf05636
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904314"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Jak debugować naruszenie zasad dostępu w języku C++?

## <a name="problem-description"></a>Opis problemu

Mój program powoduje naruszenie zasad dostępu. Jak można debugować ten program?

## <a name="solution"></a>Rozwiązanie

W przypadku naruszenia zasad dostępu w wierszu kodu, który odwołuje się do wielu wskaźników, może być trudne, aby dowiedzieć się, który wskaźnik spowodował naruszenie zasad dostępu. Począwszy od programu Visual Studio 2015 Update 1, okno dialogowe wyjątku jawnie odwołuje się do wskaźnika, który spowodował naruszenie zasad dostępu.

Na przykład, uwzględniając Poniższy kod, należy uzyskać naruszenie zasad dostępu:

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

W przypadku uruchomienia tego kodu w programie Visual Studio 2015 Update 1 powinno zostać wyświetlone następujące okno dialogowe wyjątku:

![Zrzut ekranu przedstawiający okno dialogowe wyjątku Microsoft Visual Studio, w którym podano naruszenie dostępu do odczytu dla elementu "A->B nullptr". Wybrano przycisk Przerwij.](../debugger/media/accessviolationcplus.png)

Jeśli nie możesz określić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, śledź kod, aby upewnić się, że wskaźnik powodujący problem został poprawnie przypisany.  Jeśli jest ona przenoszona jako parametr, upewnij się, że jest prawidłowo przenoszona i nie utworzysz przypadkowo [kopii płytki](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Następnie sprawdź, czy wartości nie są przypadkowo zmieniane w programie, tworząc punkt przerwania danych dla danego wskaźnika, aby upewnić się, że nie jest on modyfikowany w innym miejscu programu. Aby uzyskać więcej informacji na temat punktów przerwania danych, zobacz sekcję punkt przerwania danych w temacie [Używanie punktów przerwania](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)