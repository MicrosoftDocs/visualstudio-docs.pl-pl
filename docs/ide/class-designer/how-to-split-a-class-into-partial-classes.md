---
title: Podział klasy na klasy częściowe
description: Dowiedz się, jak używać słowa kluczowego częściowe do dzielenia deklaracji klasy lub struktury między kilka deklaracji w Projektant klas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9a29aed406d216e2fd72d9763cd9d0522f9cdd17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951826"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Instrukcje: dzielenie klasy na klasy częściowe w Projektant klas

Możesz użyć `partial` słowa kluczowego ( `Partial` w Visual Basic) do dzielenia deklaracji klasy lub struktury między kilka deklaracji. Możesz użyć dowolnej liczby deklaracji częściowych.

Deklaracje mogą znajdować się w jednym lub w wielu plikach źródłowych. Wszystkie deklaracje muszą znajdować się w tym samym zestawie i w tej samej przestrzeni nazw.

Klasy częściowe są przydatne w kilku sytuacjach. Na przykład w dużym projekcie, oddzielenie klasy na wiele plików umożliwia więcej niż jednemu programisty pracy nad projektem w tym samym czasie. Podczas pracy z kodem, który generuje program Visual Studio, można zmienić klasę bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu generowanego przez program Visual Studio obejmują Windows Forms i kod otoki usługi sieci Web). W ten sposób można utworzyć kod, który używa automatycznie generowanych klas, bez konieczności modyfikowania pliku tworzonego przez program Visual Studio.

Istnieją dwa rodzaje metod częściowych. W języku C# są one nazywane deklarowaniem i implementacją; w Visual Basic są one nazywane deklaracją i implementacją.

**Projektant klas** obsługuje klasy częściowe i metody. Kształt typu na diagramie klas odnosi się do pojedynczej lokalizacji deklaracji dla klasy częściowej. Jeśli Klasa częściowa jest zdefiniowana w wielu plikach, można określić, która lokalizacja deklaracji **Projektant klas** będzie używana przez ustawienie właściwości **Nowa lokalizacja elementu członkowskiego** w oknie **Właściwości** . Oznacza to, że po dwukrotnym kliknięciu kształtu klasy **Projektant klas** przechodzi do pliku źródłowego, który zawiera deklarację klasy identyfikowaną przez **nową właściwość lokalizacja elementu członkowskiego** . Po dwukrotnym kliknięciu metody częściowej w kształcie klasy **Projektant klas** przechodzi do deklaracji metody częściowej. Ponadto w oknie **Właściwości** Właściwość **Nazwa pliku** odwołuje się do lokalizacji deklaracji. W przypadku klas częściowych **Nazwa pliku** zawiera listę wszystkich plików, które zawierają deklarację i kod implementacji dla tej klasy. Jednak w przypadku metod częściowych **Nazwa pliku** zawiera tylko plik zawierający deklarację metody częściowej.

Poniższe przykłady dzielą definicję klasy `Employee` na dwie deklaracje, z których każda definiuje inną procedurę. Dwie definicje częściowe w przykładach mogą znajdować się w jednym pliku źródłowym lub w dwóch różnych plikach źródłowych.

> [!NOTE]
> Visual Basic używa definicji częściowej klasy do oddzielenia kodu generowanego przez program Visual Studio od kodu napisanego przez użytkownika. Kod jest podzielony na osobne pliki źródłowe. Na przykład **Projektant formularzy systemu Windows** definiuje klasy częściowe dla formantów, takich jak `Form` . Nie należy modyfikować wygenerowanego kodu w tych kontrolkach.

Aby uzyskać więcej informacji na temat typów częściowych w Visual Basic, zobacz [częściowy](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Przykład

Aby podzielić definicję klasy, użyj `partial` słowa kluczowego ( `Partial` w Visual Basic), jak pokazano w następującym przykładzie:

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

- [Klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [częściowe (Type) (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [częściowe (Metoda) (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
