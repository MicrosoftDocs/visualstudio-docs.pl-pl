---
title: 'Instrukcje: Identyfikowanie symboli w bibliotece | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191869"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Instrukcje: identyfikowanie symboli w bibliotece
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Narzędzia do przeglądania symboli wyświetlają hierarchiczne widoki symboli. Symbole reprezentują przestrzenie nazw, obiekty, klasy, składowe klas i inne elementy języka.  
  
 Każdy symbol w hierarchii może być identyfikowany przez informacje nawigacji przesłane przez bibliotekę symboli do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżera obiektów przez następujące interfejsy:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Położenie symbolu w hierarchii odróżnia symbol. Umożliwia ona przechodzenie przez narzędzia do przeglądania symboli do określonego symbolu. Unikatowa, w pełni kwalifikowana ścieżka do symbolu określa lokalizację. Każdy element w ścieżce jest węzłem. Ścieżka rozpoczyna się od węzła najwyższego poziomu i zostaje zakończona określonym symbolem. Na przykład jeśli metoda M1 jest składową klasy C1, a C1 znajduje się w N1 przestrzeni nazw, pełna ścieżka metody M1 to N1. C1. M1. Ta ścieżka zawiera trzy węzły: N1, C1 i M1.  
  
 Informacje o nawigacji umożliwiają [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menedżerowi obiektów lokalizowanie, wybieranie i utrzymywanie wybranych symboli w hierarchii. Umożliwia nawigowanie po jednym narzędziu do przeglądania. Podczas używania **Przeglądarka obiektów** do przeglądania symboli w [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekcie, można kliknąć prawym przyciskiem myszy metodę i uruchomić narzędzie **przeglądarka wywołań** , aby wyświetlić metodę w grafie wywołań.  
  
 Dwa formularze opisują lokalizację symboli. Formularz kanoniczny jest oparty na w pełni kwalifikowanej ścieżce symbolu. Reprezentuje unikatową pozycję symbolu w hierarchii. Jest on niezależny od narzędzia do przeglądania symboli. Aby uzyskać informacje o formularzu kanonicznym, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Menedżer obiektów wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodę. Formularz prezentacji opisuje lokalizację symbolu w określonym narzędziu do przeglądania symboli. Pozycja symbolu jest względem pozycji innych symboli w hierarchicy. Dany symbol może mieć kilka ścieżek prezentacji, ale tylko jedną ścieżkę kanoniczną. Na przykład jeśli Klasa C1 jest dziedziczona z klasy C2 i obie klasy znajdują się w N1 przestrzeni nazw, **Przeglądarka obiektów** wyświetla następujące drzewo hierarchiczne:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Ścieżka kanoniczna klasy C2, w tym przykładzie, to N1 + C2. Ścieżka prezentacji C2 zawiera węzły C1 i "podstawowe i interfejsy": N1 + C1 + "bazy i interfejsy" + C2.  
  
 Aby uzyskać informacje o formularzu prezentacji, Menedżer obiektów wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodę.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identyfikowanie symbolu w hierarchii  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Aby uzyskać informacje o formularzach kanonicznych i prezentacji  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodę.  
  
     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów znajdujących się w ścieżce kanonicznej symbolu.  
  
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
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodę.  
  
     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów znajdujących się w ścieżce prezentacji symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Instrukcje: rejestrowanie biblioteki przy użyciu Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Instrukcje: uwidacznianie listy symboli udostępnianych przez bibliotekę dla menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
