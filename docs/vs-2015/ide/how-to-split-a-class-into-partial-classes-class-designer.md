---
title: 'Instrukcje: Podział klasy na klasy częściowe (Projektant klas) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 15c57de4a8f51283692b21bcaa148c86bb4deb2d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775795"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Instrukcje: Podział klasy na klasy częściowe (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deklaracja klasy lub struktury między kilka deklaracji można podzielić przy użyciu `Partial` — słowo kluczowe w języku Visual Basic lub `partial` — słowo kluczowe w języku Visual C#. Można użyć tylu częściowe deklaracje, jak w tyle plików innego źródła lub w jednym pliku źródłowym. Jednak wszystkie deklaracje musi należeć do tego samego zestawu i tej samej przestrzeni nazw.  
  
 Klasy częściowe są przydatne w kilku sytuacjach. Na przykład pracujesz nad dużymi projektami, rozdzielając klasy na więcej niż jeden plik umożliwia więcej niż jeden programisty pracować nad nim, w tym samym czasie. Podczas pracy z kodem, który program Visual Studio generuje klasę można zmienić bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu, który generuje programie Visual Studio obejmuje kod otoki Windows Forms i usługi sieci Web). Ten sposób można utworzyć kod, który używa klasy generowane automatycznie, bez konieczności modyfikowania pliku przez program Visual Studio.  
  
 Istnieją dwa rodzaje metod częściowych. W języku Visual C# są one nazywane deklarowania i implementowanie; w języku Visual Basic są nazywane deklarację i implementację.  
  
 Projektant klasy obsługuje klasy częściowe i metody. Typ kształtu na diagramie klasy odwołuje się do lokalizacji jednej deklaracji klasy częściowej. Jeśli częściowa klasa jest zdefiniowana w wielu plikach, można określić lokalizacji deklaracji, do której będzie używać projektanta klas, ustawiając **Lokalizacja nowej składowej** właściwość **właściwości** okna. Oznacza to, gdy klikniesz dwukrotnie kształt klasy, Projektant klas jest przesyłany do pliku źródłowego, który zawiera deklarację klasy identyfikowane przez **Lokalizacja nowej składowej** właściwości. Po dwukrotnym kliknięciu metody częściowej w kształcie klasy projektanta klas jest przesyłany do deklaracji metody częściowej. Ponadto **właściwości** oknie **nazwy pliku** właściwość odwołuje się do lokalizacji, w deklaracji. Dla klas częściowych **nazwy pliku** zawiera listę wszystkich plików, które zawierają kod deklarację i implementację dla tej klasy. Jednak w przypadku metod częściowych **nazwy pliku** plik zawierający deklaracji metody częściowej.  
  
 Poniższe przykłady dzielenie definicji klasy `Employee` na dwie deklaracje, z których każdy definiuje różne procedury. Dwie definicje częściowe w przykładach można w jednym pliku źródłowym lub w dwóch innych plików źródłowych.  
  
> [!NOTE]
>  Visual Basic używa definicji częściowej klasy do oddzielania programu Visual Studio — wygenerowanego kodu z kodu utworzonych przez użytkownika. Kod jest dzielony na pliki źródłowe dyskretnych. Na przykład **projektanta formularzy Windows** definiuje częściowe klasy dla kontrolek, takich jak `Form`. Kod wygenerowany w tych kontrolek nie należy modyfikować.  
  
 Aby uzyskać więcej informacji na temat typów częściowych w języku Visual Basic, zobacz [częściowe](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).  
  
## <a name="example"></a>Przykład  
 Aby podzielić definicji klas w języku Visual Basic, należy użyć `Partial` — słowo kluczowe, jak pokazano w poniższym przykładzie.  
  
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
 Aby podzielić definicję klasy w języku Visual C#, należy użyć `partial` — słowo kluczowe, jak pokazano w poniższym przykładzie.  
  
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
 [Klasy częściowe i metody](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)   
 [partial (Type)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)   
 [Partial (metoda) (odwołanie w C#)](http://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137)   
 [Partial](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
