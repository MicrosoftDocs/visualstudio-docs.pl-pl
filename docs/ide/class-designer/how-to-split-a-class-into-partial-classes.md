---
title: 'Porady: podział klas na klasy częściowe (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 48672e2d316828019ede7097306517b270062327
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588684"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Jak: Dzielenie klasy na klasy częściowe w Projektancie klas

Za pomocą `partial` słowa`Partial` kluczowego (w języku Visual Basic) można podzielić deklarację klasy lub struktury między kilka deklaracji. Można użyć dowolną liczbę deklaracji częściowych.

Deklaracje mogą znajdować się w jednym lub w wielu plikach źródłowych. Wszystkie deklaracje muszą znajdować się w tym samym zestawie i tej samej przestrzeni nazw.

Klasy częściowe są przydatne w kilku sytuacjach. Na przykład w dużym projekcie oddzielenie klasy do wielu plików umożliwia więcej niż jeden programista do pracy nad projektem w tym samym czasie. Podczas pracy z kodem, który generuje program Visual Studio, można zmienić klasę bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu generowanego przez program Visual Studio obejmują formularze systemu Windows i kod otoki usługi sieci Web). W ten sposób można utworzyć kod, który używa automatycznie generowanych klas bez konieczności modyfikowania pliku, który tworzy program Visual Studio.

Istnieją dwa rodzaje metod częściowych. W języku C# są one nazywane deklarowaniem i wdrażaniem; w języku Visual Basic, są one nazywane deklaracji i implementacji.

**Projektant klas** obsługuje częściowe klasy i metody. Kształt typu na diagramie klasy odnosi się do pojedynczej lokalizacji deklaracji dla klasy częściowej. Jeśli klasa częściowa jest zdefiniowana w wielu plikach, można określić, która lokalizacja deklaracji **Projektant klasy** będzie używana przez ustawienie właściwości Nowa lokalizacja **elementu członkowskiego** w oknie **Właściwości.** Oznacza to, że po dwukrotnym kliknięciu kształtu klasy **Projektant klasy** przechodzi do pliku źródłowego, który zawiera deklarację klasy identyfikowaną przez właściwość Nowa lokalizacja **elementu członkowskiego.** Po dwukrotnym kliknięciu metody częściowej w kształcie klasy **Projektant klasy** przechodzi do deklaracji metody częściowej. Ponadto w oknie **Właściwości** **właściwość Nazwa pliku** odwołuje się do lokalizacji deklaracji. W przypadku klas częściowych **nazwa pliku** zawiera listę wszystkich plików, które zawierają deklarację i kod implementacji dla tej klasy. Jednak dla metod częściowych **nazwa pliku** wyświetla tylko plik, który zawiera deklarację metody częściowej.

Poniższe przykłady podzielić definicję klasy `Employee` na dwie deklaracje, z których każda definiuje inną procedurę. Dwie definicje częściowe w przykładach może być w jednym pliku źródłowym lub w dwóch różnych plikach źródłowych.

> [!NOTE]
> Visual Basic używa definicji częściowej klasy do oddzielenia kodu wygenerowanego przez program Visual Studio od kodu autorstwa użytkownika. Kod jest podzielony na oddzielne pliki źródłowe. Na przykład **Projektant formularzy systemu Windows** definiuje `Form`klasy częściowe dla formantów, takie jak . Nie należy modyfikować wygenerowany kod w tych formantów.

Aby uzyskać więcej informacji na temat typów częściowych w języku Visual Basic, zobacz [Częściowe](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Przykład

Aby podzielić definicję klasy, użyj `partial` słowa kluczowego (w`Partial` języku Visual Basic), jak pokazano w poniższym przykładzie:

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

## <a name="see-also"></a>Zobacz też

- [Klasy i metody częściowe](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (Typ) (odwołanie c#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial (Metoda) (odwołanie C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
