---
title: 'Jak: identyfikowanie symboli w bibliotece | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708006"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Jak: identyfikowanie symboli w bibliotece
Narzędzia do przeglądania symboli wyświetlają hierarchiczne widoki symboli. Symbole reprezentują przestrzenie nazw, obiekty, klasy, elementy członkowskie klasy i inne elementy języka.

 Każdy symbol w hierarchii może być identyfikowany przez informacje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nawigacyjne przekazywane przez bibliotekę symboli do menedżera obiektów za pośrednictwem następujących interfejsów:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Położenie symbolu w hierarchii wyróżnia symbol. Umożliwia narzędziom do przeglądania symboli przechodzenie do określonego symbolu. Unikatowa, w pełni kwalifikowana ścieżka do symbolu określa lokalizację. Każdy element w ścieżce jest węzłem. Ścieżka rozpoczyna się od węzła najwyższego poziomu i kończy się określonym symbolem. Na przykład jeśli metoda M1 jest członkiem klasy C1 i C1 jest w obszarze nazw N1, pełna ścieżka metody M1 jest N1. C1. M1. Ta ścieżka zawiera trzy węzły: N1, C1 i M1.

 Informacje nawigacyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwiają menedżerowi obiektów lokalizowanie, zaznaczanie i przechowywanie zaznaczonych symboli w hierarchii. Umożliwia nawigację z jednego narzędzia do przeglądania do drugiego. Podczas korzystania z **przeglądarki obiektów** do [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] przeglądania symboli w projekcie można kliknąć prawym przyciskiem myszy metodę i uruchomić narzędzie **Wywołaj przeglądarkę,** aby wyświetlić metodę na wykresie wywołań.

 Dwa formularze opisują położenie symbolu. Forma kanoniczna opiera się na w pełni kwalifikowanej ścieżce symbolu. Reprezentuje unikatową pozycję symbolu w hierarchii. Jest niezależna od narzędzia do przeglądania symboli. Aby uzyskać informacje o formularzu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kanonicznym, menedżer obiektów wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodę. Formularz prezentacji opisuje położenie symbolu w określonym narzędziu do przeglądania symboli. Położenie symbolu jest względem położenia innych symboli w hierarchii. Dany symbol może mieć kilka ścieżek prezentacji, ale tylko jedną ścieżkę kanoniczną. Na przykład jeśli klasa C1 jest dziedziczona z klasy C2, a obie klasy znajdują się w obszarze nazw N1, **przeglądarka obiektów** wyświetla następujące drzewo hierarchiczne:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Ścieżka kanoniczna klasy C2, w tym przykładzie, jest N1 + C2. Ścieżka prezentacji C2 zawiera C1 i "Podstawy i interfejsy" węzły: N1 + C1 + "Podstawy i interfejsy" + C2.

 Aby uzyskać informacje o formularzu <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> prezentacji, menedżer obiektów wywołuje metodę.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Aby uzyskać informacje o formularzach kanonicznych i prezentacji

1. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodę.

     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów zawartych w ścieżce kanonicznej symbolu.

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

     Menedżer obiektów wywołuje tę metodę, aby uzyskać listę węzłów zawartych w ścieżce prezentacji symbolu.

## <a name="see-also"></a>Zobacz też
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Jak: Zarejestruj bibliotekę w menedżerze obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Jak: Uwidacznianie list symboli dostarczonych przez bibliotekę do menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
