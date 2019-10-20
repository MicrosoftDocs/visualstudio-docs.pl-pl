---
title: 'Instrukcje: dzielenie klasy na klasy częściowe (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e93ebc58e4e9b6092921e4155fe3d821bb552c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670714"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Porady: podział klas na klasy częściowe (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deklarację klasy lub struktury można podzielić między kilka deklaracji za pomocą słowa kluczowego `Partial` w Visual Basic lub słowa kluczowego `partial` w wizualizacji C#. Możesz użyć dowolną liczbę deklaracji częściowych, tak jak wiele różnych plików źródłowych, lub w jednym pliku źródłowym. Wszystkie deklaracje muszą jednak znajdować się w tym samym zestawie i w tej samej przestrzeni nazw.

 Klasy częściowe są przydatne w kilku sytuacjach. Na przykład podczas pracy nad dużymi projektami oddzielenie klasy do więcej niż jednego pliku umożliwia wielu programistom pracę nad nim jednocześnie. Podczas pracy z kodem, który generuje program Visual Studio, można zmienić klasę bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu generowanego przez program Visual Studio obejmują Windows Forms i kod otoki usługi sieci Web). W ten sposób można utworzyć kod, który używa automatycznie generowanych klas, bez konieczności modyfikowania pliku tworzonego przez program Visual Studio.

 Istnieją dwa rodzaje metod częściowych. W wizualizacji C#są one nazywane deklarowaniem i implementacją; w Visual Basic są one nazywane deklaracją i implementacją.

 Projektant klas obsługuje klasy częściowe i metody. Kształt typu na diagramie klas odnosi się do pojedynczej lokalizacji deklaracji dla klasy częściowej. Jeśli Klasa częściowa jest zdefiniowana w wielu plikach, można określić, która lokalizacja deklaracji Projektant klas będzie używana przez ustawienie właściwości **Nowa lokalizacja elementu członkowskiego** w oknie **Właściwości** . Oznacza to, że po dwukrotnym kliknięciu kształtu klasy Projektant klas przechodzi do pliku źródłowego, który zawiera deklarację klasy identyfikowaną przez **nową właściwość lokalizacja elementu członkowskiego** . Po dwukrotnym kliknięciu metody częściowej w kształcie klasy Projektant klas przechodzi do deklaracji metody częściowej. Ponadto w oknie **Właściwości** Właściwość **Nazwa pliku** odwołuje się do lokalizacji deklaracji. W przypadku klas częściowych **Nazwa pliku** zawiera listę wszystkich plików, które zawierają deklarację i kod implementacji dla tej klasy. Jednak w przypadku metod częściowych **Nazwa pliku** zawiera tylko plik zawierający deklarację metody częściowej.

 Poniższe przykłady dzielą definicję klasy `Employee` na dwie deklaracje, z których każda definiuje inną procedurę. Dwie definicje częściowe w przykładach mogą znajdować się w jednym pliku źródłowym lub w dwóch różnych plikach źródłowych.

> [!NOTE]
> Visual Basic używa definicji częściowej klasy do oddzielenia programu Visual Studio — wygenerowany kod z kodu napisanego przez użytkownika. Kod jest podzielony na osobne pliki źródłowe. Na przykład **Projektant formularzy systemu Windows** definiuje klasy częściowe dla kontrolek, takich jak `Form`. Nie należy modyfikować wygenerowanego kodu w tych kontrolkach.

 Aby uzyskać więcej informacji na temat typów częściowych w Visual Basic, zobacz [częściowy](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).

## <a name="example"></a>Przykład
 Aby podzielić definicję klasy w Visual Basic, użyj słowa kluczowego `Partial`, jak pokazano w poniższym przykładzie.

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

## <a name="example"></a>Przykład
 Aby podzielić definicję klasy w wizualizacji C#, użyj słowa kluczowego `partial`, jak pokazano w poniższym przykładzie.

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

## <a name="see-also"></a>Zobacz też
 Częściowe [klasy i metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [częściowe (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334) [częściowe (Metoda)C# (odwołanie)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137) [częściowe](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
