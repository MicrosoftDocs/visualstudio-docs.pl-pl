---
title: 'Instrukcje: Identyfikowanie symboli w bibliotece | Microsoft Docs'
description: Dowiedz się, jak identyfikować symbole w bibliotece, implementując metody, które przekazują informacje o nawigacji z biblioteki symboli do Menedżera obiektów programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6c897801b98857f4a310323d4e00583c98245d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078880"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Instrukcje: Identyfikowanie symboli w bibliotece
Narzędzia do przeglądania symboli wyświetlają hierarchiczne widoki symboli. Symbole reprezentują przestrzenie nazw, obiekty, klasy, składowe klas i inne elementy języka.

 Każdy symbol w hierarchii może być identyfikowany przez informacje nawigacji przesłane przez bibliotekę symboli do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów przez następujące interfejsy:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Położenie symbolu w hierarchii odróżnia symbol. Umożliwia ona przechodzenie przez narzędzia do przeglądania symboli do określonego symbolu. Unikatowa, w pełni kwalifikowana ścieżka do symbolu określa lokalizację. Każdy element w ścieżce jest węzłem. Ścieżka rozpoczyna się od węzła najwyższego poziomu i zostaje zakończona określonym symbolem. Na przykład jeśli metoda M1 jest składową klasy C1, a C1 znajduje się w N1 przestrzeni nazw, pełna ścieżka metody M1 to N1. C1. M1. Ta ścieżka zawiera trzy węzły: N1, C1 i M1.

 Informacje nawigacyjne umożliwiają [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menedżerowi obiektów Znajdowanie, wybieranie i utrzymywanie wybranych symboli w hierarchii. Umożliwia nawigowanie po jednym narzędziu do przeglądania. Podczas używania **Przeglądarka obiektów** do przeglądania symboli w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekcie, można kliknąć prawym przyciskiem myszy metodę i uruchomić narzędzie **przeglądarka wywołań** , aby wyświetlić metodę w grafie wywołań.

 Dwa formularze opisują lokalizację symboli. Formularz kanoniczny jest oparty na w pełni kwalifikowanej ścieżce symbolu. Reprezentuje unikatową pozycję symbolu w hierarchii. Jest on niezależny od narzędzia do przeglądania symboli. Aby uzyskać informacje o formularzu kanonicznym, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżer obiektów wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodę. Formularz prezentacji opisuje lokalizację symbolu w określonym narzędziu do przeglądania symboli. Pozycja symbolu jest względem pozycji innych symboli w hierarchii. Dany symbol może mieć kilka ścieżek prezentacji, ale tylko jedną ścieżkę kanoniczną. Na przykład jeśli Klasa C1 jest dziedziczona z klasy C2 i obie klasy znajdują się w N1 przestrzeni nazw, **Przeglądarka obiektów** wyświetla następujące drzewo hierarchiczne:

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

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Aby uzyskać informacje o formularzach kanonicznych i prezentacji

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
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Instrukcje: rejestrowanie biblioteki przy użyciu Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Instrukcje: Uwidacznianie list symboli dostarczonych przez bibliotekę do Menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
