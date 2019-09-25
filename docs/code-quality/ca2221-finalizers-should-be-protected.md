---
title: 'CA2221: Finalizatory powinny być chronione'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 827a8ee01575d6d263c8f8ee423de72cfe939e39
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231182"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizatory powinny być chronione

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ publiczny implementuje finalizator, który nie określa dostępu rodziny (chronione).

## <a name="rule-description"></a>Opis reguły
Finalizatory muszą korzystać z modyfikatora dostępu „family”. Ta reguła jest wymuszana przez C#kompilatory, Visual Basic i C++ wizualizacje.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić finalizator na dostęp do rodziny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Tej reguły nie można naruszać w żadnym języku .NET wysokiego poziomu; można je naruszyć w przypadku pisania języka pośredniego firmy Microsoft.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Zobacz także

- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)