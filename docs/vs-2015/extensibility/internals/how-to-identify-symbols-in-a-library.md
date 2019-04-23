---
title: 'Instrukcje: Identyfikowanie symboli w bibliotece | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f154c63940189f1a6035246fb7f72ec27be677f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116254"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Instrukcje: Identyfikowanie symboli w bibliotece
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Narzędzia do przeglądania symboli wyświetlić widokach hierarchicznych symboli. Symbole reprezentują przestrzenie nazw, obiektów, klas, składowych klasy i inne elementy języka.  
  
 Każdy symbol w hierarchii można zidentyfikować przez nawigacji informacje przekazywane przez bibliotekę symboli do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów przy użyciu następujących interfejsów:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Lokalizacja symbolu w hierarchii różnic między usługą symbol. Umożliwia ona narzędzi do przeglądania symboli można przejść do określonego symbolu. Unikatowa, w pełni kwalifikowaną ścieżkę do symbolu Określa lokalizację. Każdy element w ścieżce jest węzłem. Ścieżka zaczyna się od węzła najwyższego poziomu i kończy się wraz z określonego symbolu. Na przykład jeśli metoda M1 jest składową klasy C1 C1 znajduje się w przestrzeni nazw N1, pełną ścieżkę metoda M1 jest N1. C1. M1. Ta ścieżka zawiera trzy węzły: N1, C1 i M1.  
  
 Informacje o nawigacji umożliwia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów, aby zlokalizować, zaznacz i zachować wybrane symbole w hierarchii. Umożliwia przechodzenie między jedno narzędzie do przeglądania do innego. Podczas korzystania z **przeglądarki obiektów** do przeglądania symboli w [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektu, kliknij prawym przyciskiem myszy metodę i rozpoczęcia mogą **przeglądarce wywołań** narzędzia, aby wyświetlić wykresu wywołań metody.  
  
 Dwie formy opisują lokalizację symbolu. Forma kanoniczna opiera się na w pełni kwalifikowaną ścieżkę symbolu. Reprezentuje unikatową pozycję symbolu w hierarchii. Jest ono niezależne od narzędzia do przeglądania symboli. Aby uzyskać informacje forma kanoniczna [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obiekt Menedżera wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metody. Prezentacja formularz opisuje Lokalizacja symbolu w określonym narzędziu przeglądania symboli. Pozycja znaku jest określana względem pozycji innych symboli w hierarchicy. Podanego symbolu może mieć wiele ścieżek prezentacji, ale tylko jedna ścieżka canonical. Na przykład, jeśli klasa C1 jest dziedziczona z klasy C2 i obie klasy w przestrzeni nazw N1 **przeglądarki obiektów** wyświetla następujące drzewa hierarchicznego:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Canonical ścieżka klasy C2, w tym przykładzie jest N1 + C2. Ścieżka prezentacji C2 zawiera węzły "Podstaw i interfejsy" i C1: N1 + C1 + "baz i interfejsy" + C2.  
  
 Uzyskiwania informacji formularza prezentacji, wywołań Menedżera obiektów <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metody.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identyfikowanie symboli w hierarchii  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Aby uzyskać canonical i prezentacji formularzy informacji  
  
1. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metody.  
  
     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów znajdujących się w ścieżce canonical symbolu.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metody.  
  
     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów znajdujących się w ścieżce prezentacji symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Instrukcje: Rejestrowanie biblioteki przy użyciu Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Instrukcje: Uwidacznianie listy symboli udostępnianych przez bibliotekę dla Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
