---
title: Jak można debugować naruszenia zasad dostępu? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297317"
---
# <a name="how-can-i-debug-an-access-violation"></a>Jak można debugować naruszenia zasad dostępu?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Program powoduje naruszenie zasad dostępu. W jaki sposób można to debugować?  
  
## <a name="solution"></a>Rozwiązanie  
 Jeśli w wierszu kodu, który wyłuskań wielu wskaźników naruszenie zasad dostępu, może być trudne dowiedzieć się, wskaźnika, który spowodował naruszenie zasad dostępu. Począwszy od programu Visual Studio 2015 Update 1, okno dialogowe wyjątku teraz jawnie nazwy wskaźnika, który spowodował naruszenie zasad dostępu.  
  
 Na przykład biorąc pod uwagę następujący kod, należy uzyskać naruszenie zasad dostępu:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Jeśli uruchomisz ten kod w Visual Studio 2015 Update 1, powinny zostać wyświetlone następujące okno dialogowe wyjątku:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Jeśli nie można ustalić, dlaczego wskaźnik spowodował naruszenie zasad dostępu, prześledzi kod, aby upewnić się, że wskaźnik przyczyną problemu jest poprawnie przypisany.  Jeśli jest ona przenoszona jako parametr, upewnij się, że jest prawidłowo przenoszona i nie utworzysz przypadkowo [kopii płytki](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Następnie sprawdź, czy wartości nie są przypadkowo zmieniane w programie, tworząc punkt przerwania danych dla danego wskaźnika, aby upewnić się, że nie jest on modyfikowany w innym miejscu programu. Aby uzyskać więcej informacji na temat punktów przerwania danych, zobacz sekcję punkt przerwania danych w temacie [Używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
