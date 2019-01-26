---
title: 'Instrukcje: Podział klasy na klasy częściowe (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5b169979da4a6eba777855d3b0af5c0a31059f73
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970087"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Instrukcje: Podział klasy na klasy częściowe w Projektancie klas

Możesz użyć `partial` — słowo kluczowe (`Partial` w języku Visual Basic) do dzielenia deklaracji klasy lub struktury między kilka deklaracji. Można użyć tylu częściowe deklaracje.

Deklaracje może być w jednym lub w wielu plikach źródłowych. Wszystkie deklaracje musi należeć do tego samego zestawu i tej samej przestrzeni nazw.

Klasy częściowe są przydatne w kilku sytuacjach. W dużym projekcie na przykład oddzielenie klasę do wielu plików umożliwia więcej niż jeden programisty do pracy nad projektem w tym samym czasie. Podczas pracy z kodem, który program Visual Studio generuje klasę można zmienić bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu, który generuje programie Visual Studio obejmuje kodu otoki usługi sieci web i Windows Forms). Ten sposób można utworzyć kod, który używa klasy generowane automatycznie, bez konieczności modyfikowania pliku przez program Visual Studio.

Istnieją dwa rodzaje metod częściowych. W języku C# są nazywane deklarowania i implementowanie; w języku Visual Basic są nazywane deklarację i implementację.

**Projektant klasy** obsługuje klasy częściowe i metody. Typ kształtu na diagramie klasy odwołuje się do lokalizacji jednej deklaracji klasy częściowej. Jeśli częściowa klasa jest zdefiniowana w wielu plikach, można określić lokalizacji, do której deklaracji **projektanta klas** użyje ustawiając **Lokalizacja nowej składowej** właściwość **właściwości**  okna. Oznacza to, że po dwukrotnym kliknięciu kształt klasy **projektanta klas** zbliża się do pliku źródłowego, który zawiera deklarację klasy identyfikowane przez **Lokalizacja nowej składowej** właściwości. Po dwukrotnym kliknięciu metody częściowej w kształcie klasy **projektanta klas** przechodzi do deklaracji metody częściowej. Ponadto **właściwości** oknie **nazwy pliku** właściwość odwołuje się do lokalizacji, w deklaracji. Dla klas częściowych **nazwy pliku** zawiera listę wszystkich plików, które zawierają kod deklarację i implementację dla tej klasy. Jednak w przypadku metod częściowych **nazwy pliku** plik zawierający deklaracji metody częściowej.

Poniższe przykłady dzielenie definicji klasy `Employee` na dwie deklaracje, z których każdy definiuje różne procedury. Dwie definicje częściowe w przykładach można w jednym pliku źródłowym lub w dwóch innych plików źródłowych.

> [!NOTE]
> Visual Basic używa definicji częściowej klasy do oddzielania programu Visual Studio — wygenerowanego kodu z kodu utworzonych przez użytkownika. Kod jest dzielony na pliki źródłowe dyskretnych. Na przykład **projektanta formularzy Windows** definiuje częściowe klasy dla kontrolek, takich jak `Form`. Kod wygenerowany w tych kontrolek nie należy modyfikować.

Aby uzyskać więcej informacji na temat typów częściowych w języku Visual Basic, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Przykład

Aby podzielić definicji klasy, należy użyć `partial` — słowo kluczowe (`Partial` w języku Visual Basic), jak pokazano w poniższym przykładzie:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Zobacz także

- [Klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [Partial (typ) (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [Partial (metoda) (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)